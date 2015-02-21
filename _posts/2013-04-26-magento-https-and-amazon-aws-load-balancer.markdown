---
layout: post
status: publish
published: true
title: Magento HTTPS and Amazon AWS Load Balancer
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 547
wordpress_url: http://www.davidmataro.com/?p=547
date: !binary |-
  MjAxMy0wNC0yNiAyMDowMjowNyArMDAwMA==
date_gmt: !binary |-
  MjAxMy0wNC0yNiAxODowMjowNyArMDAwMA==
tags:
- aws
- magento
- nginx
- https
- load balancer
- elb
comments: []
---
<p>Magento can manage secure HTTPS connections in frontend and in backend. But, manage HTTPS connections is a additional load for the servers. If you use a load balancer in front of the servers, you can avoid this additional load and delegate the encryption process to the load balancer.</p>
<p>Architecture:</p>
<p>Browser <---- HTTPS(443) ----> Load Balancer <---- HTTP(80) ----> Nginx</p>
<p>Scenario:</p>
<ul>
<li>Magento 1.7.0.0</li>
<li>2 instance as a web servers with Ubuntu 12.04 TLS.</li>
<li>nginx as webserver</li>
<li>AWS Load Balancer</li>
</ul>
<p>To test the system I have created a self signed certificate. To create a self signed certificate in ubuntu, I have run the next commands.</p>
<p><code lang="bash"><br />
openssl req -new -newkey rsa:2048 -nodes -out csr.pem -keyout private-key.pem -subj "/C=ES/ST=Barcelona/L=Barcelona/O=Enterwine/OU=Enterwine/CN=www.enterwine.com"</p>
<p>openssl x509 -req -days 365 -in csr.pem -signkey private-key.pem -out server.crt</p>
<p>openssl rsa -in private-key.pem -out decrypted-private-key.pem</p>
<p></code></p>
<p>Once I have the self signed certificate, I have loaded it to AWS Load Balancer.</p>
<p>Add certificate to AWS Load Balancer from AWS Console:</p>
<p>1. Go to AWS Console.<br />
2. Go to Service &gt; EC2<br />
3. Go to Network &amp; Security &gt; Load Balancers<br />
4. Select your Load Balancer and go to Listeners<br />
5. Add new Listener:<br />
Load Balacner Protocol: HTTPS<br />
Load Balancer Port: 443<br />
Instance Protocol: HTTP<br />
Instance Port: 80<br />
6. In the SSL Certificate option chose Select<br />
7. Go to Upload a new SSL Certificate and put your key (decrypted-private-key.pem) and vert (server.crt) content into the Private Key and Public Key Certificate.<br />
8. Save</p>
<p>Magento expect a header to identify the connection as a secure connection and the AWS Load Balancer send a header identifying the secure connection. For this, is necessary to configure the web server to send a header to magento when receive the secure header from AWS Load Balancer.</p>
<p>In my case, I use nginx web server. I have configured the nginx to detect the AWS Load Balacner header and set header to Magento.</p>
<p><code lang="bash"><br />
set $ssl "off";<br />
if ($http_x_forwarded_proto = "https") {<br />
set $ssl "on";<br />
}</p>
<p>location …. {<br />
…<br />
fastcgi_param HTTPS $ssl;<br />
}</p>
<p></code><br />
&nbsp;</p>
<p>You can read more here:<br />
<a href="http://www.aschroder.com/2012/07/magento-ssl-offloading-with-amazon-elb/" target="_blank">http://www.aschroder.com/2012/07/magento-ssl-offloading-with-amazon-elb/</a><br />
<a href="http://www.sonassi.com/knowledge-base/magento-kb/magento-https-redirect-loop/" target="_blank">http://www.sonassi.com/knowledge-base/magento-kb/magento-https-redirect-loop/</a></p>
