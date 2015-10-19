---
layout: post
status: publish
published: true
title: Install vagrant-chef-zero on vagrant 1.6.3.1
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 566
wordpress_url: http://www.davidmataro.com/?p=566
date: !binary |-
  MjAxNC0wOS0yNiAxODoyNzo1MSArMDAwMA==
date_gmt: !binary |-
  MjAxNC0wOS0yNiAxNjoyNzo1MSArMDAwMA==
tags: []
comments: []
---
<p>I have tried to install "vagrant-chef-zero" on vagrant-1.6.3.1 and I get a problem with nokinori.</br></p>
<p><code><br />
Bundler, the underlying system Vagrant uses to install plugins,<br />
reported an error. The error is shown below. These errors are usually<br />
caused by misconfigured plugin installations or transient network<br />
issues. The error from Bundler is:</p>
<p>An error occurred while installing nokogiri (1.6.3.1), and Bundler cannot continue.<br />
Make sure that `gem install nokogiri -v '1.6.3.1'` succeeds before bundling.<br />
</code><br />
</br><br />
After search in google and read some post, finally I have found this post <a href="http://zdk.blinkenshell.org/vagrant-1.6.3-nokogiri-depended-plugin-installation-quickfix/" target="_blank">http://zdk.blinkenshell.org/vagrant-1.6.3-nokogiri-depended-plugin-installation-quickfix/</a> with the solution.<br />
</br><br />
Edit /Applications/Vagrant/embedded/gems/specifications/vagrant-1.6.3.gemspec and add s.add_dependency(%q<nokogiri>, ["= 1.6.2.1"]) after Gem::Specification.new do |s|<br />
</br><br />
<code><br />
# -*- encoding: utf-8 -*-</p>
<p>Gem::Specification.new do |s|<br />
  s.name = "vagrant"<br />
  s.version = "1.6.3"<br />
  s.add_dependency(%q<nokogiri>, ["= 1.6.2.1"])<br />
</code></p>
