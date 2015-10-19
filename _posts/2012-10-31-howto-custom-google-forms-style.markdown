---
layout: post
status: publish
published: true
title: Howto custom Google Forms style?
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 499
wordpress_url: http://www.davidmataro.com/?p=499
date: !binary |-
  MjAxMi0xMC0zMSAyMzozMjozNCArMDAwMA==
date_gmt: !binary |-
  MjAxMi0xMC0zMSAyMTozMjozNCArMDAwMA==
tags:
- google
comments: []
---
<p>One of the more common things that there are in a website are the formularies. Usually the formularies content are send by email. An alternative is use the Google Forms integrated in your website. In Google Forms, when a user filled a formularie, all the fields are introduced into a spreadsheet docs.</p>
<p>By default Google Forms has it own style and it is very simple, but you can change it. Next, I explain how to customize the Google Form style.</p>
<p>1. Crear a new form.</p>
<p>Loggin into your Google Drive and select Create > Form.</p>
<p>2. Add your form fields</p>
<p>3. Customize the style</p>
<p>3.1. Select the form view from the bottom page link. It open a new page with the form. </p>
<p>3.2. Copy the page source. Copy everything between the tags<br />
<form> and </form>
<p>3.3. Paste the code in your html page and customize the style.</p>
<p>3.4. Add your own confirmation page.</p>
<p><code></p>
<form action="YOUR-GOOGLE-SPREADSHEET-LINK" method="POST">
</code><br />
With this:</p>
<p><code><br />
<script type="text/javascript">var submitted=false;</script><br />
<iframe name="hidden_iframe" id="hidden_iframe"<br />
style="display:none;" onload="if(submitted)<br />
{window.location='http://CONFIRMATION-PAGE.html';}"></iframe></p>
<form action="YOUR-GOOGLE-SPREADSHEET-LINK" method="post"<br />
target="hidden_iframe" onsubmit="submitted=true;"><br />
</code></p>
