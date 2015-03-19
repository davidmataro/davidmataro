---
layout: post
status: draft
published: true
title: My first approach working with chef in local mode
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
tags: []
comments: []
---
For some projects, I prefer don't work with a chef-server as a chef code repository. I prefer work directly with git and don't use a chef-server. To do it, we can use chef-solo or use chef in local mode. In the next lines I show you my first approach to deploy a system with chef in local mode.


List of components used:

- Git as a code repository.
- Chef in local mode to deploy
- Vagrant to run the development node.
- Ec2 instance to run the production node.




### Create the development environment
1.- Create the chef repo and add your chef code.

2.- Create the vagrant node

Configure vagrant to install Chef client. You need to have the vagrant omnibus plugin installed. This is my Vagranfile.

```
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  #config.vm.box = "precise32"
  config.vm.synced_folder ".", "/vagrant", :nfs => true
  config.vm.network "private_network", ip: "10.0.0.31"
  config.omnibus.chef_version = :latest
end
```

3.- Configure chef client to run in local mode. To do this, I have create the next clitnt.rb file


```ruby
cookbook_path   "/vagrant/chef-repo/cookbooks"
role_path '/vagrant/chef-repo/roles'
data_bag_path  '/vagrant/chef-repo/data_bags'
environment_path '/vagrant/chef-repo/environments'
environment 'development'
local_mode 'true'
node_name 'node_dev'
node_path '/vagrant/chef-repo/nodes'
validator_key '/vagrant/chef-repo/.chef/validator.pem'
encrypted_data_bag_secret '/vagrant/chef-repo'
log_level :info
```

4.- Create a node definition.

To run chef in local mode we need to create the node definition in the local repository and add a run list. I use the nodes/node_dev.json.

```json
"name": "node_dev",
  "chef_environment": "development",
  "override": {

  },
  "normal": {
    "tags": [

    ]
  },
  "run_list": [
    "role[base]",
    "role[dbserver]",
    "role[webserver]",
    "role[phpserver]"
  ]
}
```


### Deploy to development environment

```shell
vagrant ssh
cd /vagrant/chef-repo
sudo chef-client -c client.rb
```


### Create the production environment

1.- Create the ec2 instance and install chef client.

2.- Configure chef client to run in local mode. I have created the next /etc/chef/client.rb file in the production node.

```ruby
cookbook_path   "/root/chef-repo/cookbooks"
role_path '/root/chef-repo/roles'
data_bag_path  '/root/chef-repo/data_bags'
environment_path '/root/chef-repo/environments'
encrypted_data_bag_secret '/etc/chef'
environment 'production'
local_mode 'true'
node_name 'node'
node_path '/root/chef-repo/nodes'
log_level :info
```

3.- Add in your repo the production node definition.  nodes/node.json.

```json
"name": "node",
  "chef_environment": "production",
  "override": {

  },
  "normal": {
    "tags": [

    ]
  },
  "run_list": [
    "role[base]",
    "role[dbserver]",
    "role[webserver]",
    "role[phpserver]"
  ]
}
```



### Deploy to production environment


1.- Upload chef code to ec2 instance.

To upload the chef code to ec2 node I use the git server, but you can use ssh or you favorite method.

2.- Run chef-client

```bash
git pull origin master
chef-client
```


### Future improvements

Using a git hook we can automatize the production deployment task. We can develop a hook that after push you production branch to git server, It connect to the production node and run a git pull and a chef-client.
