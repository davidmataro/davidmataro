---
layout: post
status: publish
published: true
title: "Testing web app with infrataster and kitchenci"
description: "How to use infrataster with kitchen and Chef to check a web app"
keywords: "infrataster, serverpec, kitchenci, chef"
author:
  display_name: davidmataro
  login: davidmataro
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
tags: []
comments: []
---

In some cases it's not sufficient to test if a nginx process is running or port 80 is open. There are some cases that before promote a change to production environment we need run some acceptance test.

I have been searching in google how to run some acceptance tests with [Chef](https://www.chef.io/) + [Kitchen](http://kitchen.ci/), and I found [infrastaster](https://github.com/ryotarai/infrataster/issues/37), a Infraestucture Behavior Testing Framework. And on a project issue I has found a solution to run [infrastaster](https://github.com/ryotarai/infrataster/issues/37) with [serverspec](http://serverspec.org/).

Next I show how I have implemented my own tests with [infrastaster](https://github.com/ryotarai/infrataster/issues/37)

The [serverspec](http://serverspec.org/) tests there are inside *integration/default/serverspec/* directory in the chef-repo.

Create a file *integration/default/serverspec/Gemfile*

```ruby
source 'https://rubygems.org'

gem 'infrataster'
```


Create a file *integration/default/serverspec/spec_helper*

```ruby
require 'serverspec'
require 'infrataster/rspec'

set :backend, :exec

Infrataster::Server.define(:app, '127.0.0.1')
```

Create tests

```ruby
equire 'spec_helper'

describe port(80) do
  it { should be_listening.on('0.0.0.0').with('tcp') }
end

describe server(:app) do
  describe http('http://testing.shopswey.com') do
    it "responds content including 'Shopswey'" do
      expect(response.body).to include('Shopswey')
    end
  end
end
```

This test  check if port 80 is open, and connect to http://testing.shopswey.com url to check if the response contains the string *Shopswey*

After create the test, you can run a *kitchen verify* to run the test. When you run the *kitchen verify*, [Kitchen](http://kitchen.ci/) install [infrastaster](https://github.com/ryotarai/infrataster/issues/37) on the node.
