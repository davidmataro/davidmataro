---
layout: post
status: published
published: true
title: How to run test Kitchen on amazon aws?
description: "How to install and configure kitchen-ec2 driver to run tests on AWS."
keywords: "test, kitchen, aws, chef"
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
tags: ['devops','aws','testing']
comments: []
dark: false
---

One of the most important things of continuous delivery process is to run tests. To run test with [Chef](https://www.chef.io/) we have [Test Kitchen](http://kitchen.ci/). [Test Kitchen](http://kitchen.ci/) is a tool to execute test on one o more platforms. [Test Kitchen](http://kitchen.ci/) have drivers to execute test on differents platforms like [Vagrant](https://www.vagrantup.com/), [AWS](http://aws.amazon.com/), [Rackspace](http://www.rackspace.com/), [Azure](https://azure.microsoft.com) and more.


By default, [Test Kitchen](http://kitchen.ci/) use kitchen-vagrant driver. This post contains the steps to configure Test Kitchen to execute tests on AWS using [kitchen-ec2](https://github.com/test-kitchen/kitchen-ec2) driver.



- Create a IAM user in your AWS account, and download the access credentials. I use the "arn:aws:iam::aws:policy/AmazonEC2FullAccess” policy.


- Add a credentials profile in .aws/credentials file:

  $HOME/.aws/credentials

  {% highlight bash %}
  [shopswey]
  aws_access_key_id = KKKKKKKKKKK
  aws_secret_access_key = SSSSSSSSSSSSSSSSSSSSSSSSSS
  {% endhighlight %}


- Create a ec2 key pair and save in $HOME/.ec2/ directory.

  {% highlight bash %}
  $HOME/.ec2/shopswey.pem
  {% endhighlight %}


- Create a ec2 security group.


- Install and init kitchen-ec2 driver:

  {% highlight bash %}
  kitchen init --driver=kitchen-ec2 --create-gemfile
  bundle install
  {% endhighlight %}


- Edit kitchen.yml file:

  {% highlight bash %}
  ---
  driver:
    name: ec2
    aws_ssh_key_id: shopswey
    security_group_ids: ["sg-c4eb47a0"]
    region: eu-west-1
    availability_zone: b
    require_chef_omnibus: true
    instance_type: t1.micro
    associate_public_ip: true
    shared_credentials_profile: shopswey

  provisioner:
    name: chef_zero
    cookbook_path: cookbooks
    roles_path: roles
    environments_path: environments
    data_bags_path: data_bags
    client_rb:
      environment: development

  platforms:
    - name: aws-ubuntu-14.04
      driver:
        image_id: ami-5da23a2a
      transport:
        ssh_key: /Users/dmataro/.ec2/shopswey.pem
        username: ubuntu

  suites:
    - name: aws
      driver:
        vm_hostname: s1.shopswey.loc
      run_list:
      - role[base]
      - role[dbserver]
      - role[phpserver]
      - role[webserver]
      attributes:
  {% endhighlight %}


To view what means each option, visit [kitchen-ec2](https://github.com/test-kitchen/kitchen-ec2)


- Run kitchen


Links:

[https://github.com/test-kitchen/kitchen-ec2](https://github.com/test-kitchen/kitchen-ec2)
[http://misheska.com/blog/2014/09/21/survey-of-test-kitchen-providers/#amazon-ec2-cloud-provider-kitchen-ec2](http://misheska.com/blog/2014/09/21/survey-of-test-kitchen-providers/#amazon-ec2-cloud-provider-kitchen-ec2)


2016-06-27 UPDATE


After update kitchen to 1.7.3 version, when run a kitchen test there are next error:

```bash
-----> Starting Kitchen (v1.7.3)
-----> Creating <aws-testing-ubuntu-trusty64>...
       If you are not using an account that qualifies under the AWS
free-tier, you may be charged to run these suites. The charge
should be minimal, but neither Test Kitchen nor its maintainers
are responsible for your incurred costs.

>>>>>> ------Exception-------
>>>>>> Class: Kitchen::ActionFailed
>>>>>> Message: Failed to complete #create action: [parameter validator found 3 errors:
  - unexpected value at params[:block_device_mappings][0][:ebs_device_name]
  - unexpected value at params[:block_device_mappings][0][:ebs_volume_size]
  - unexpected value at params[:block_device_mappings][0][:ebs_delete_on_termination]]
>>>>>> ----------------------
>>>>>> Please see .kitchen/logs/kitchen.log for more details
>>>>>> Also try running `kitchen diagnose --all` for configuration
```


In new kitchen versions the EBS configuration have changed. The new configuration is:

```yml
block_device_mappings:
  - device_name: /dev/sda1
    ebs:
      volume_size: 50
      delete_on_termination: true
```
