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


Vagrant boxes are the package format for Vagrant environments. There are a lot of [boxes](https://atlas.hashicorp.com/boxes/search), but in some cases you need customize your box. You can automatize your bootstrap with a script or chef, but the virtual machine start up consume time. To reduce the bootstrap time, you can create your own custom box.

Once you have started and installed your virtual machine, you can create your own box following the next steps:

1. Create a new vm from a base box

  {% highlight bash %}
  vagrant init basebox
  {% endhighlight %}

  {% highlight bash %}
  vagrant up
  {% endhighlight %}

2. Customize you virtual machine

3. Clean the box

  {% highlight bash %}
  sudo apt-get clean
  {% endhighlight %}

  {% highlight bash %}
  sudo dd if=/dev/zero of=/EMPTY bs=1M
  sudo rm -f /EMPTY
  {% endhighlight %}

  {% highlight bash %}
  cat /dev/null > ~/.bash_history && history -c && exit
  {% endhighlight %}

4. Package de virtual machine to a new vagrant box

  {% highlight bash %}
  vagrant package --output boxname.box
  {% endhighlight %}

5. Add the new box to your vagrant install

  {% highlight bash %}
  vagrant box add boxname boxname.box
  {% endhighlight %}

5. Destroy de virtual machine

  {% highlight bash %}
  vagrant destroy
  rm Vagrantfile
  {% endhighlight %}

7. Configure the nex box in your Vagrantfile

  {% highlight bash %}
  vagrant init boxname
  {% endhighlight %}

  Edit the Vagrantfile and configure it.

8. Start up the virtual machine

  {% highlight bash %}
  vagrant up
  {% endhighlight %}


Updates:

-- 2015-11-04 --
With vagrant 1.7.4, I have had problems to authenticate to the box with private/public keys. To resolve this issues, I have configured the authentication with username/password.

  {% highlight bash %}
  config.ssh.username = 'vagrant'
  config.ssh.password = 'vagrant'
  {% endhighlight %}
