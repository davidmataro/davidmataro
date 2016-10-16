---
layout: post
status: draft
published: true
title: generating kibana reports with phantomjs
excerpt: How to generate Kibana reports using phantomjs and send its by email.
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
tags: []
comments: []
dark: false
---

This week a customer said me that he want to receive kibana reports by email. After look in Internet, I found a payment services like Skedler and some approach that use browser tools like selenium or phantomjs. Finally I chose use a broswer approach and because I want to run reports without X11, I chose phantomjs.

First I have created a dashboard in Kibana by each report I need send. After create a Kibana dashboard I have created a simple phantomjs script to get the report and render it as png file. I use png file because I don't want to send dashboard header, and the pdf render not run well when gets only a dashboard grid.


Phantomjs script:

```javascript
var page = require('webpage').create(),
  system = require('system'),
  url, output, type;
page.customHeaders={'Authorization': 'Basic '+btoa('admin:PASSWORD')};
page.viewportSize = { width: 1800, height: 2000 };
var waitTime = 120 * 1000;

if (system.args.length < 3 || system.args.length > 5) {
    console.log('Usage: phantomjs_reports.js  url environment type');
    phantom.exit(1);
} else {

  url = system.args[1];
  output = system.args[2];
  type = system.args[3];

  page.open(url, function(status) {
    console.log("Status: " + status);
    if(status !== "success") {
      console.log('Unable to load the address!');
      phantom.exit();
    }else{
      window.setTimeout(function () {
        var clipRect = page.evaluate(function(){
          return document.querySelector('.ready').getBoundingClientRect();
        });

        page.clipRect = {
          top:    clipRect.top,
          left:   clipRect.left,
          width:  clipRect.width,
          height: clipRect.height
        };
        page.render('/tmp/' + output + '.' + type);
        phantom.exit();
      }, waitTime);
    }
  });
}
```

The script takes three arguments:

* The Url of kibana dashboard. The url contains all parameters to get the dashboard.
* The Output file name without extension.
* The type of the file returned by phantomjs script.

Example of script call from bash:

```bash
/usr/local/bin/phantomjs /usr/local/reports/phantomjs_reports.js 'http://kibana.davidmataro.com/app/kibana#/dashboard/Custom-Dashboard?_g=(refreshInterval:(display:Off,pause:!f,value:0),time:(from:now-7d,mode:quick,to:now))' custom-Dashboard png
```

To automate sending reports by email, I have created a small php script that runs pantomjs_reports.js for each report and send it by email. Finally I run this php script from cron.
