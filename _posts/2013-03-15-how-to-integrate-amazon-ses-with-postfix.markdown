---
layout: post
status: publish
published: true
title: How to integrate Amazon SES with postfix
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 521
wordpress_url: http://www.davidmataro.com/?p=521
date: !binary |-
  MjAxMy0wMy0xNSAxNzowMTowNSArMDAwMA==
date_gmt: !binary |-
  MjAxMy0wMy0xNSAxNTowMTowNSArMDAwMA==
tags: []
comments: []
---
<p>Before today I has integrated Amazon SES with postfix using stunnel. But today I have integrated Amazon SES with Postfix without stunnel.</p>
<p>To integrate Amazon SES with Potsfix I have followed the <a title="Integrating Amazon SES with Postfix" href="http://docs.aws.amazon.com/ses/latest/DeveloperGuide/postfix.html">Amazon documentations</a>. Next I describe the basic steps to integrate Amazon SES with Postfix in Ubuntu 12.04TLS.</p>
<p>1. Configure /etc/postfix/main.cf</p>
<p><code lang="bash"><br />
# See /usr/share/postfix/main.cf.dist for a commented, more complete version<br />
# Debian specific: Specifying a file name will cause the first<br />
# line of that file to be used as the name. The Debian default<br />
# is /etc/mailname.<br />
#myorigin = /etc/mailname</p>
<p>smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)<br />
biff = no</p>
<p># appending .domain is the MUA's job.<br />
append_dot_mydomain = no</p>
<p># Uncomment the next line to generate "delayed mail" warnings<br />
#delay_warning_time = 4h</p>
<p>readme_directory = no</p>
<p>&nbsp;</p>
<p>relayhost = email-smtp.us-east-1.amazonaws.com:25<br />
smtp_sasl_auth_enable = yes<br />
smtp_sasl_security_options = noanonymous<br />
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd<br />
smtp_use_tls = yes<br />
smtp_tls_security_level = encrypt<br />
smtp_tls_note_starttls_offer = yes</p>
<p>smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt<br />
</code><br />
&nbsp;</p>
<p>2. Edit /etc/postfix/sasl_password and add the folowwing lines repleacing USERNAME:PASSWORD for your credentials.</p>
<p><code lang="bash"><br />
email-smtp.us-east-1.amazonaws.com:25 USERNAME:PASSWORD<br />
ses-smtp-prod-335357831.us-east-1.elb.amazonaws.com:25 USERNAME:PASSWORD<br />
</code></p>
<p>&nbsp;<br />
3. Create a encryptation file<br />
<code lang="bash"><br />
postmap hash:/etc/postfix/sasl_passwd<br />
</code><br />
&nbsp;<br />
4. Tell Postfix where to find CA certificate</p>
<p><code lang="bash"><br />
postconf -e 'smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt'<br />
</code></p>
<p>&nbsp;</p>
