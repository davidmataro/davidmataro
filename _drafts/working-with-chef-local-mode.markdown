---
layout: post
status: draft
published: true
title: Working with chef local mode
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
tags: []
comments: []
---
For some projects, I prefer don't work with a chef-server as a chef code repository. I prefer work directly with git and don't use a chef-server. To do it, we can use chef-solo or use chef in local mode. In the next lines I show you my first approch to deploy a system with chef in local mode.

- Git as a code repository.

- Vagrant as a developement platform.

Configure vagrant to install Chef client.


```
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  #config.vm.box = "precise32"
  config.vm.synced_folder ".", "/vagrant", :nfs => true
  config.bindfs.bind_folder "/vagrant", "/var/www/", :create_as_user => true
  config.vm.network "private_network", ip: "10.0.0.31"
  config.omnibus.chef_version = :latest
end
```






