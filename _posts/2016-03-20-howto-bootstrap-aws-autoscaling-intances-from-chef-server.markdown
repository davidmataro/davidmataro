---
layout: post
status: published
published: true
title: How to bootstrap AWS Autoscaling instances from chef-server
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
tags: ['devops','chef']
comments: []
dark: true
---


1.- Bootstrap an ec2 instance with knife.

```bash
knife bootstrap ec2-54-229-215-8.eu-west-1.compute.amazonaws.com --ssh-user ubuntu --sudo --identity-file ~/.ec2/my.pem --environment production --node-name myserver --secret-file .chef/encrypted_data_bag_secret --run-list 'role[base],role[webserver]'
```

2.- Clean the ec2 instance

* Delete /etc/chef/client.pem.
* Delete node_name from /etc/chef/client.rb


3.- Generate AMI.

4.- Generate cloud init configuration

* Get instance name
* Add instance name to /etc/chef/client.rb configuration file

5.- Run chef-client

```bash
_node_name="NodeName-`ec2metadata --instance-id`"
sudo rm -rf /etc/chef/client.pem
echo "node_name '$_node_name'" >> /etc/chef/client.rb
sudo chef-client -N "$_node_name"  -o role["webserver"]
```


References:

* [SDS Practical Example](https://securosis.com/assets/library/reports/SDS-Practical-Example.pdf)
* [Register chef-client in AWS Autoscaling](http://www.tothenew.com/blog/register-chef-client-in-aws-autoscaling/)
