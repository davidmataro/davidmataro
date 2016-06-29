---
layout: post
status: draft
published: true
title: Automating aws autoscaling with chef server
excerpt: Approach to manage Chef nodes in a AWS Autoscaling infrastructure using AWS SQS queues.
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
tags: ['devops','aws','autoscaling','chef']
comments: []
dark: false
---

One of the most powerfull services from AWS is Autoscaling. [AWS Autoscaling](https://aws.amazon.com/autoscaling/) allow scale EC2 instances up and down automatically. Another powerfull tool is [Chef](https://www.chef.io/) or other tool to automating infrastructures. The combination off both is a great solution to manage your applications in the cloud.

To integrate [AWS Autoscaling](https://aws.amazon.com/autoscaling/) with Chef, is necessary communicate to [Chef Server](https://www.chef.io/chef-server/]) when an instance is up or down. When new instance boot, chef-client register new instances to [Chef Server](https://www.chef.io/chef-server/]), but when a instance shutdown anyone communicate with the [Chef Server](https://www.chef.io/chef-server/]). To do it, I use AWS SQS, where AWS Autoscaling](https://aws.amazon.com/autoscaling/) publish a message when instance down. And in the [Chef Server](https://www.chef.io/chef-server/]), I use an script to get the messages and delete node in Chef Server.

![AWS Autoscaling and chef server integration]({{site.baseurl}}/public/images/aws-autoscaling-sns-sqs-chef-server.jpg)


Next, there are the details to configure [AWS Autoscaling](https://aws.amazon.com/autoscaling/) to work with [Chef Server](https://www.chef.io/chef-server/])




## Generate custom AMI

The proposes of generate a custom AMI are:

* Install chef-client and pre-configure it.
* Reduce the boot time when AusoScaling up an new instance.

I use cloud-init to customize new instances in boot time. The next script is the basic bootstrap.txt that add node name to chef-client configuration and run the chef-client.

```bash
#!/bin/bash
set -x -e

_node_name="node-`ec2metadata --instance-id`"
echo "node_name '$_node_name'" >> /etc/chef/client.rb
echo '{"run_list":["role[base]","role[webserver]"]}"' > /etc/chef/first-boot.json
chef-client -N "$_node_name" -E "production" -L "/var/log/chef-client-first-boot-log" -j /etc/chef/first-boot.json
```

## Configure AWS queue to notify that an instances terminate.

Create IAM user with SQS access and copy user ARN (arn:aws:iam::<aws account number>:user/devops)

Create a SNS topic AutoScalingDown


__ARN: arn:aws:sns:eu-west-1:<aws account number>:AutoScalingDown__


Create SQS queue DeregisterChefServer and allow user ARN to receive message action.

* ARN: 	__arn:aws:sqs:eu-west-1:<aws account number>:DeregisterChefServer__

* URL: https://sqs.eu-west-1.amazonaws.com/<aws account number>/DeregisterChefServer


Add permitions to SQS queue DeregisterChefServer

  IAM User:

  * Effect: Allow

  * Principal: arn:aws:iam::<aws account number>:user/devops

  * Action: receiveMessage


  SNS ARN:

  * Effect: allow

  * Principal: everybody

  * Action: All

  * Conditions:

    * Condition: ArnEquals

    * Key: aws:SourceArn

    * Value: arn:aws:sns:eu-west-1:<aws account number>:AutoScalingDown


Create a SNS subcription:

  * Topic ARN: __arn:aws:sns:eu-west-1:<aws account number>:Superpop2AutoScalingDown__

  * Protocol: Amazon SQS

  * Endpoint: arn:aws:sqs:eu-west-1:<aws account number>:DeregisterChefServer



Create a notification in AutoScaling Group:


  Send a notification to: AutoScalingDown (__arn:aws:sqs:eu-west-1:<aws account number>:DeregisterChefServer__)
  Whenever instance: terminate


## Script to subcribe to AWS queue and remove nodes from [Chef Server](https://www.chef.io/chef-server/])

To get message from AWS SQS and delete nodes in [Chef Server](https://www.chef.io/chef-server/]), I have developed a small php script to run from cron. It use __aws-sdk-php__ api to connect to AWS SQS and get messages from [AWS Autoscaling](https://aws.amazon.com/autoscaling/) and run __knife__ to delete node and client from [Chef Server](https://www.chef.io/chef-server/]).


Install the next script in /usr/local/awssgs2chefserver directory:


```php
<?php

require '/usr/local/awssgs2chefserver/vendor/autoload.php';

use Aws\Sqs\SqsClient;

$queueUrl = 'https://sqs.eu-west-1.amazonaws.com/<aws account number>/DeregisterChefServer';

$client = SqsClient::factory(array(
    'profile' => 'my_aws_profile',
    'region'  => 'eu-west-1'
));

try {

  $result = $client->receiveMessage(array(
    'QueueUrl' => $queueUrl
  ));

  if ($result['Messages'] == null) {
    exit;
  }

  $result_message = array_pop($result['Messages']);
  $queueHandle = $result_message['ReceiptHandle'];
  $messageBody = $result_message['Body'];

  $body = json_decode($messageBody, true);
  $message = json_decode($body['Message'], true);
  $delete_node = "/usr/bin/knife node delete node-" . $message['EC2InstanceId'] . " -y";
  $delete_client = "/usr/bin/knife client delete node-" . $message['EC2InstanceId'] . " -y";

  $result = system($delete_node);
  if (!$result) {
    echo "failed to delete node node-" . $message['EC2InstanceId'] . "\n";
  }

  $result = system($delete_client);
  if (!$result) {
    echo "failed to delete client node-" . $message['EC2InstanceId'] . "\n";
  }

  $client->deleteMessage(array(
    'QueueUrl' => $queueUrl,
    'ReceiptHandle' => $queueHandle
  ));

} catch (Exception $e) {
    die('Error receiving message to queue ' . $e->getMessage());
}
?>
```

Create a composer.json file /usr/local/awssgs2chefserver/composer.json to install aws-sdk-php:


```json
{
    "require": {
        "aws/aws-sdk-php": "2.*"
    }
}
```


Install and run composer:


```bash
curl -sS https://getcomposer.org/installer | php
php composer.phar install
```


Create /usr/local/awssgs2chefserver/.chef directory and add:


* admin.pem

* trusted_certs/<chef server trusted cert>.crt

* knife.rb


```ruby
# See https://docs.getchef.com/config_rb_knife.html for more information on knife configuration options

current_dir = File.dirname(__FILE__)
log_level                :info
log_location             STDOUT
node_name                "admin"
client_key               "#{current_dir}/admin.pem"
validation_client_name   "<organization>-validator"
validation_key           "#{current_dir}/<organization>-validator.pem"
chef_server_url          "<chef server url>"
cookbook_path            ["#{current_dir}/../cookbooks"]
```

Create a AWS credentials for IAM user in /root/.aws/credentials


```bash
[my_aws_profile]
aws_access_key_id = <IAM access key>
aws_secret_access_key = <IAM secret key>
```


Install chefdk.


Run script from cron creating the /etc/cron.d/awssgs2chefserver file:


```bash
* * * * *	root	cd /usr/local/awssgs2chefserver; /usr/bin/php /usr/local/awssgs2chefserver/awssgs2chefserver
```
