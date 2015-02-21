---
layout: post
status: publish
published: true
title: Instal·lació automàtica de sistemes amb Cobbler
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 38
wordpress_url: http://www.davidmataro.com/?p=38
date: !binary |-
  MjAxMC0wNy0wNSAxNToyODowMCArMDAwMA==
date_gmt: !binary |-
  MjAxMC0wNy0wNSAxMzoyODowMCArMDAwMA==
tags:
- datacenter
- opensource
- sysadmin
comments: []
---
<p>En tot Datacenter la automatitizació de sistemes és una tasca imprescindible per tal de minimitzar els costos operatius de desplegar un nou sistema, mantenir la homogenietat dels sistemes i evitar els erros humans. La virtualització i la possibilitat de clonar màquines virtuals ràpidament, automatitzar la instal·lació de nous de sistemes s'ha simplificat. Tot i això, no tots els sistemes són virtuals, de manera que cal també automatitzar la instal·lació dels sistemes físics a banda dels virtuals.</p>
<p>Una eina per automatitzar la instal·lació de sistemes físics i virtuals és Cobbler. <a href="https://fedorahosted.org/cobbler/">Cobbler</a>  permet als administradors de sistemes centralitzar i automatitzar la instal·lació de sistemes, ja siguin físics o virtuals. <a href="https://fedorahosted.org/cobbler/">Cobbler</a> és un projecte OpenSource de RedHat que s'inclou dintre de <a href="https://fedorahosted.org/web/">FedoraHoted</a>. <a href="https://fedorahosted.org/cobbler/">Cobbler</a> s'estructura en els elements següent:</p>
<p>- Distribucions: una distribució conté tota la informació realcionada amb el kernel, scripts, ... d'una instal·lació. És a dir, és una <br />distribució de Linux a partir de la qual es realitza una instal·lació.</p>
<p>- Perfil: un perfil és una particularització de la instal·lació d'una distribució. Aquesta particularituzació es fa mitjançant la definició d'un fitxer d'instal·lació kickstart.  Un perfil per exemple pot representar la instal·lació d'un servidor web, d'un servidor de bbdd o d'una estació de treball.</p>
<p>- Sistema: un sistema no és més que la instal·lació d'un perfil sobre un servidor físic o virtual concret. </p>
<p>- Repositori: un repositori és un mirror de les actualitzacions d'uan distribució concreta. D'aquesta manera, els sistemes instal·lats des de <a href="https://fedorahosted.org/cobbler/">Cobbler</a> actualitzen els paquets des del mateix servidor de Cobbler i no des d'Internet. Així, s'accelera la actualització de paquets i és redueix el tràfic de xarxa Internet.</p>
<p>- Imatges: són instal·lacions que és fan sobre un fitxer ISO. De manera que aquesta imatge ISO es pot instal·lar tant sobre un servidor físic com virtual.</p>
<p><a href="https://fedorahosted.org/cobbler/">Cobbler</a> disposa de dos interface de treball, una via linia de comandes i una segona via web. Des de ambdues interface es poden gestionar les distribucions, perfils, sistemes i repositoris.</p>
<p>Des del punt de vista d'un Datacenter, <a href="https://fedorahosted.org/cobbler/">Cobbler</a> permet automatitzar la instal·lació de nous servidor de hosting dedicat o virtual, re-instal·lar de manera ràpida un servidor que ha fallat i fins hi tot, disposar de plantilles de servidors (perfils) que s'instal·lin automàticament en funció de la necessitat de càrrega. Per exemple, en cas d'un portal web amb un frontal format per N servidors Apache, si augmenta la demanda es poden instal·lar nous servidors Apache de manera ràpida i fins hi tot de manera automàtica. I aquest servidors Apache s'instal·len basats en una plantilla (perfil) determinada.</p>
<p>Més informació a <a href="https://fedorahosted.org/cobbler/">Cobbler</a>.</p>
