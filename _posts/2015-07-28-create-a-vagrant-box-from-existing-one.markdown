---
layout: post
status: published
published: true
title: Create a Vagrant box from existing one
description: "How to optimize the vagrant vm bootstrap by customizing your own boxes"
keywords: "vagrant, boxes, bootstrap"
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
tags: ['devops','vagrant']
comments: []
---


Vagrant boxes are the package format for Vagrant environments. There are a lot of boxes in https://atlas.hashicorp.com/boxes/search, but in some cases you need customize your box. You can automatize your bootstrap with a script or chef, but the virtual machine start up consume time. To reduce the bootstrap time, you can create your own custom box.

Once you have started and installed your virtual machine, you can create your own box following the next steps:

1. Create a new vm from a base box

  ```bash
  vagrant init basebox
  ```

  ```bash
  vagrant up
  ```

2. Customize you virtual machine

3. Clean the box

  ```bash
  sudo apt-get clean
  ```

  ```bash
  sudo dd if=/dev/zero of=/EMPTY bs=1M
  sudo rm -f /EMPTY
  ```

  ```bash
  cat /dev/null > ~/.bash_history && history -c && exit
  ```

4. Package de virtual machine to a new vagrant box

  ```bash
  vagrant package --output boxname.box
  ```

5. Add the new box to your vagrant install

  ```bash
  vagrant box add boxname boxname.box
  ```

5. Destroy de virtual machine

  ```bash
  vagrant destroy
  rm Vagrantfile
  ```

7. Configure the nex box in your Vagrantfile

  ```bash
  vagrant init boxname
  ```

  Edit the Vagrantfile and configure it.

8. Start up the virtual machine

  ```bash
  vagrant up
  ```
