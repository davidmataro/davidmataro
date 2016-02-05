---
layout: post
status: published
published: true
title: Chef development approach with kitchen berkshelf and vagrant
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
tags: ['devops','chef']
comments: []
dark: true
---

Until now, I have been using the approach defined in my post [My first approach working with chef in local mode](my-first-approach-working-with-chef-local-mode) for develop and in some case for production also. Now I use a new approach based on kitchen, [berkshelf](http://berkshelf.com) and vagrant. This approach give me a clear vision of the developed cookbooks.

In this approach, I use [berkshelf](http://berkshelf.com) to manage the cookbooks dependencies. And because in most projects that I develop there is more that one cookbook, I need to add all the cookbooks from the only one Berskfile file. For do it, I use the next scenario:

* A project repository with the cookbooks and other stuff.
* The project contains:
  * cookbooks
  * roles
  * environments
  * data_bags
* A Berksfile inside the project repository.
* A .kitchen.yml definition inside the project repository.


### Example

Create a new project repository named mystack.

```bash
chef generate app mystack
```

Creates the following files:

```bash
mystack/
  |__ .git
  |__ .gitignore
  |__ .kitchen.yml
  |__ README.md
  |__ cookbooks/
  |    |__ mystack/
  |__ test
```

Create a Berksfile inside mystack/ directory and add your cookbooks.  

```Berskfile
source "https://supermarket.chef.io"

cookbook "mystack", path: "cookbooks/mystack"
```

You can add into Berskfile file as many cookbooks as you wish. Each cookbook have their own metadata.rb with their dependencies.



Configure .kitchen.yml

```bash
---
driver:
  name: vagrant

provisioner:
  name: chef_zero
  cookbook_path: cookbooks
  roles_path: roles
  environments_path: environments
  data_bags_path: data_bags
  client_rb:
    environment: development

platforms:
  - name: ubuntu/trusty64

suites:
  - name: default
    driver:
      vm_hostname: mystack.loc
      network:
      - ["private_network", {ip: "10.0.0.31"}]
      customize:
        memory: 1024
        cpus: 1
    run_list:
      - recipe[mystack::default]
    attributes:
```

Because I use a development environment in my .kitchen.ym file configuration, I need create a environment/development.json file.

```bash
{
  "name": "development",
  "description": "Development environment",
  "cookbook_versions": {
  },
  "json_class": "Chef::Environment",
  "chef_type": "environment",
  "default_attributes": {
    "authorization": {
      "sudo": {
        "users": [
          "vagrant"
        ]
      }
    }
  },
  "override_attributes": {
  }
}
```

To download all cookbooks dependencies run the next command:

```bash
berks install
```

By default all the cookbook dependencies are located at '~/.berkshelf/cookbooks'. And each cookbook is named using the convention {name}-{version}.

Finally, run 'kitchen converge' to start a vagrant virtual machine and install and configure all the software components.

```bash
kitchen converge default
```

To upload all cookbooks to Chef server, you must create a knife.rb configuration inside the .chef/ directory, add the validation and user keys and run:

```bash
berks upload
```
