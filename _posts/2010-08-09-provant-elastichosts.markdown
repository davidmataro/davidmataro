---
layout: post
status: publish
published: true
title: Provant ElasticHosts
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 40
wordpress_url: http://www.davidmataro.com/?p=40
date: !binary |-
  MjAxMC0wOC0wOSAxMzo1MDowMCArMDAwMA==
date_gmt: !binary |-
  MjAxMC0wOC0wOSAxMTo1MDowMCArMDAwMA==
tags:
- cloud
comments: []
---
<p>Avui he llegit que <a href="http://www.serverbeach.co.uk/">ServerBeach</a> ha llençat un servei de cloud utilitzant la plataforma de <a href="http://www.elastichosts.com/">ElasticHosts</a> i m'he decidit a provar-la. En el procés de registre m'he endut la primera sorpresa. Es obligat posar un telèfon i que sigui correcte ja que envien la meitat de la password per mail i l'altre meitat via un sms.</p>
<p>Un cop creada la compte, s'accedeix al panell de control  via https://lon-p.elastichosts.com/accounts/ amb el mail com a nom d'usuari i la password que ens han anviat per mail i sms. Per defecte la demo té creada una màquina virtual amb les característiques següents:</p>
<p>CPU: 2000 core MHz<br />RAM: 1024 MB<br />Drives: RedHat  Fedora Linux 13 Live CD</p>
<p>El sistema asigna una ip dinàmica a la màquina virtual i permet l'accés per vnc i a les estadístiques de tràfic des del pròpi panell de control.</p>
<p>Per crear un nou servidor, des de la part dreta del panell de control, hi ha la opció "Add server or drive", aquí seleccionem server, introduïnt un nom - en el meu cas test1 - i seleccionem el tipus d'instal·lació:</p>
<p>· Imatge pre-instal·lada: disposa de imatges de debian, ubuntu i windows.</p>
<p>· Instal·lació des d'un cd: disposa de cd de centos, debian, freebsd, knoppix, opensolaris, RedHat Fedora, Ubunto i Windows. aquesta opció permet per tota la instal·lació del sistema operatiu de manera personalitzada.</p>
<p>· Arrancar des d'un live cd: també ofereix opcions en linux i windows.</p>
<p>· Arrancar des de una imatge de disc existent: cal seleccionar la imatge previament creada.</p>
<p>Per la prova, he seleccionat crear el servidor des d'una imatge pre-instal·lada i he seleccionat la imatge d'un Debian Linux 4.0: System Base without X. Finalment seleccionem la capacitat del disc (1 GB).</p>
<p>Al premer Add, en el panel de control es mostra el nou servidor amb nom test1 i el nou disc també anomenat test1. Podem visualitzar que en la vista del servidor s'indica que el disc del servidor és test1. El servidor permet les opcions de arrancar, editar i d'esborrar.</p>
<p>Al seleccionar la opció de editar, es pot modificar el nom del servidor, la cpu, la memoria, els discos la configuració de xarxa i el password d'accés vnc. També hi ha unes opcions avançades on es pot modificar el número de cores, el model de la targeta de xarxa, configurar una lan privada i encriptar la sessió vnc.</p>
<p>Un cop arrancada la màquina virtual test1 ja podem entrar per vnc amb el password que s'indica en el panel de control. Un cop a dins, amb el login root entrem directament a la consola del sistema sense password. De manera que cal posar una password. Un cop posada la password la pròxima vegada que fem login ja ens demana la password per entrar.</p>
<p>Per defecte, l'únic accés al servidor virtual és via vnc, de manera que si volem accés ssh, cal que arranquem el servei.</p>
<p>Ara ja podem començar a treballar amb el nou servidor virtual.</p>
<p>A descatar la posibilitat de crear vlan privades per conectar les màqunes virtuals. Així permet desplegar arquitectures de més d'una capa amb recursos de xarxa dedicats.  </p>
<p><a href="http://www.elastichosts.com/">ElasticHosts</a> proporciona una API REST per a la gestió remota de les màquines virtuals via crides HTTP. Per  provar-la podem descarregar el shell script elastichost.sh. Les dades d'accés des de la API estan a My Account > Profile, son el UUID i la Secret API Key. Al web hi ha tota la documentació per utilitzar la API.</p>
<p><a href="http://www.elastichosts.com/">ElasticHosts</a> presenta dos modelitat de facturació, una per càrrega de credit i una altre per pagament d'una quota mensual. </p>
<p>My account > Billing: des d'aquí podem gestionar el consum de recursos utilitzants en la modelitat de pregamament. Aquest recursos es consumeixen per trams horaris.</p>
<p>My account > Subscriptions: permet gestionar les subscripcions, on es paga una quota mensual per uns recursos. És a dir, permet pagar un tant mensual per una quantitat de recursos de MHz de CPU, de RAM, de Disc i de Tràfic.</p>
<p>Per finalitzar, <a href="http://www.elastichosts.com/">ElasticHosts</a> presenta una interface de gestió simple i util per a la administració de servidors en cloud, la qual és mereix els premis que li estan donant ultimament. Sens dubte aquesta és una molt bona opció per desplegar un servei de lloguer de servidor en la modelitat de pagament per us.</p>
