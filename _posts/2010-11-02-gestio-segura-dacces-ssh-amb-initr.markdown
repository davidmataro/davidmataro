---
layout: post
status: publish
published: true
title: Gestió segura d’accés SSH amb Initr
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 102
wordpress_url: http://www.davidmataro.com/?p=102
date: !binary |-
  MjAxMC0xMS0wMiAxNDo1MzoyNyArMDAwMA==
date_gmt: !binary |-
  MjAxMC0xMS0wMiAxMjo1MzoyNyArMDAwMA==
tags:
- ingent
- initr
- sysadmin
comments:
- id: 2733
  author: Tweets that mention David MatarÃ³Â» Blog Archive Â» GestiÃ³ segura dâ€™accÃ©s
    SSH amb Initr -- Topsy.com
  author_email: ''
  author_url: http://topsy.com/trackback?url=http%3A%2F%2Fwww.davidmataro.com%2F%3Fp%3D102&amp;utm_source=pingback&amp;utm_campaign=L2
  date: !binary |-
    MjAxMC0xMS0wNSAxMToyOToxOSArMDAwMA==
  date_gmt: !binary |-
    MjAxMC0xMS0wNSAwOToyOToxOSArMDAwMA==
  content: ! '[...] This post was mentioned on Twitter by Oriol Bausa, David MatarÃ³.
    David MatarÃ³ said: GestiÃ³ segura d&#039;accÃ©s ssh amb initr http://ow.ly/34ORZ
    [...] '
---
<p lang="ca-ES">Un  dels problemes amb que s'enfronta tot administrador de sistemes és la gestió permisos d'accés remot als servidors. És a dir, qui pot i qui no pot entrar en un servidor amb permisos d'administrador (root). Un altre problema de disposar d'accés remot als servidors és la gestió de la seguretat: ports d'accés oberts a tothom, farragoses gestions de firewall's, canvis de password's o revocacions de certificats, ... en definitiva una problemàtica que acostuma a costar forces hores d'administració de sistemes.</p>
<p lang="ca-ES">
<p lang="ca-ES">Aquestes problemàtiques i els costos d'administració associats es solucionen amb ssh_station. ssh_station és un mòdul que <a title="Ingent Grup" href="http://www.ingent.net" target="_blank">Ingent Grup</a> ha desenvolupat dintre del projecte <a title="Initr" href="http://www.initr.org" target="_blank">Initr</a> que permet automatitzat la gestionar els permisos d'accés ssh als servidors. Les característiques principals de ssh_stations són:</p>
<ul>
<li> Accés per certificat digital:</li>
</ul>
<p>L'accés als servidors o nodes es fa mitjançant certificat digital i es suprimeix l'accés per login i password, evitant així atacs de força bruta que poden vulnerar un servidor.</p>
<p lang="ca-ES">
<ul>
<li>Administració centralitzada:</li>
</ul>
<p lang="ca-ES">
<p lang="ca-ES">La gestió de permisos d'accés ssh als servidors es fa via web des de <a title="Initr" href="http://www.initr.org" target="_blank">Initr</a>. Tot usuari donat d'alta a Initr publica la seva clau pública dintre del seu perfil d'usuari. Aquest clau és utilitzada per ssh_station per proporcionar accés als servidors.</p>
<p lang="ca-ES">
<p lang="ca-ES">La gestió de permisos d'accés es fa per projectes. Un usuari està assignat a un o més projectes i disposa d'accés ssh via certificat digital a tots els nodes assignats al projecte. És a dir, els projectes actuen com a grups.</p>
<p lang="ca-ES">
<ul>
<li>Accés centralitzat:</li>
</ul>
<p lang="ca-ES">
<p lang="ca-ES">ssh_station permet accedir als servidors des d'un únic punt (ssh_server_station). De manera que no cal que l'operador o administrador de sistemes recordi la ip del servidor on es vol connectar, sinó que es connecta per ssh al ssh_server_station i aquest li proporciona la llista de servidors on té permís d'accés. Llavors es tant senzill com escollir el servidor on es vol accedir i establir la connexió ssh.</p>
<p lang="ca-ES">
<p>[caption id="attachment_104" align="aligncenter" width="300" caption="ssh_station connection"]<a href="http://www.davidmataro.com/wp-content/uploads/2010/11/Screen-shot-2010-11-02-at-10.43.26-AM.png"><img class="size-medium wp-image-104 " title="ssh_station" src="http://www.davidmataro.com/wp-content/uploads/2010/11/Screen-shot-2010-11-02-at-10.43.26-AM-300x216.png" alt="" width="300" height="216" /></a>[/caption]</p>
<p lang="ca-ES">
<p lang="ca-ES">
<p lang="ca-ES">La connexió ssh establerta no es fa com a root, sinó que es fa amb un usuari sense permisos, obligant a fer sudo per adquirir permisos de root. Això aporta un nivell més de seguretat.</p>
<p lang="ca-ES">
<ul>
<li>Accés SSH transparent:</li>
</ul>
<p lang="ca-ES">
<p lang="ca-ES">Una altre característica important de ssh_station és l'accés ssh transparent. És a dir, permet accedir via ssh als nodes que estan darrera d'un firewall sense tenir que configurar cap regle en el firewall. Aquesta funcionalitat permet que els servidors no tinguin el port 22 obert a Internet, evitant així atacs de seguretat al port 22.</p>
<p lang="ca-ES">
<p lang="ca-ES">
<p lang="ca-ES">
<p lang="ca-ES">Les avantatges de ssh_station es fan més evidents quant s'està administrant servidors distribuïts en diferents Centres de Dades o clouds públics, on s'acostuma a tenir entorns heterogenis: diferents firewall's, interlocutors, eines de gestió,etc.. En aquest entorn portar la gestió d'accés amb Initr estalvia moltes hores d'administració de sistemes i redueix els riscos davant atacs als servidors.</p>
<p lang="ca-ES">
<p lang="ca-ES">Un altre característica important de ssh_station és la possibilitat d'establir túnels segurs a d'altres ports (aplicacions web) del servidor o de servidors de la xarxa on està connectat el servidor. I accedir a aquestes aplicacions en remot i de forma segura. L'explicació d'aquesta funcionalitat la deixaré per un altre post.</p>
