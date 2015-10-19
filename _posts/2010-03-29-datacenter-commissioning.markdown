---
layout: post
status: publish
published: true
title: Datacenter commissioning
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 30
wordpress_url: http://www.davidmataro.com/?p=30
date: !binary |-
  MjAxMC0wMy0yOSAyMDoxNTowMCArMDAwMA==
date_gmt: !binary |-
  MjAxMC0wMy0yOSAxODoxNTowMCArMDAwMA==
tags:
- datacenter
comments: []
---
<p>Quant s'afronta un projecte de contrucció d'un Datacenter, en la fase de disseny s'especifíquen tot un conjunt de subsistemes (sistema elèctric, sistema de refrigeració, sistema de detecció i extenció d'incèndis, sistemes de seguretat física i sistemes de monitoratge i gestió), la relació entre cadascun dels elements i s'estima el comportament del conjunt amb càrrega. Després en la fase de desplegament, cada sistema es desplegat pel proveïdor corresponents - normalment un proveïdor per subsistema -  i probat de manera individual. Cada proveïdor realitza la posta en marxa i les proves funcionals del subsistema que ha instal·lat per tal de disposar de la acceptació del client i facturar. En aquest procés, en cap moment es fa una comprovació de tot el conjunt. I és aquí on el "Commissioning" pren importància.</p>
<p>L'objectiu del "Commissioning" és provar el comportament de tots els subsistemes treballant conjuntament, amb la finalitat de comprovar si el desplegament de cada subsistema assoleix els objectius marcats en la fase de disseny i compleix amb els requisits inicials. És a dir, és un procés de validació de la instal·lació. També permet identificar les mancances de la instal·lació i els límits de la mateixa, informació que serà de molta utilitat en la fase d'explotació. És per això que la pràctica del "Commissioning" es cada cop més utilitzada en la fase de desplegament d'un Datacenter.</p>
<p>Com tot procés aquest està format per una entrada, un conjunt d'activitats i una sortida.</p>
<p>Entrades:</p>
<ul>
<li>LLista de requisits de disseny i contrucció del datacenter.</li>
<li>El disseny del Datacenter.</li>
<li>Resultat de les proves realitzades en la posta en marxa de cadascun dels components del Datacenter.</li>
</ul>
<p>Sortides:</p>
<ul>
<li>Script: conté la llista de components provats i el tipus de test realitzat i el resultat obtingut.</li>
<li>Registre d'error: és una anàlisi <a href="http://davidmataro.blogspot.com/2009/12/analisi-fmea.html">FMEA</a> (Failure Mode Effects Analysis) d'un components específica que ha fallat durant el test. Aquest identifica l'impacte de l'error i recomana les possibles solucions.</li>
<li>Resum executiu: descriu les accions les proves realitzades i un pla d'acció.</li>
</ul>
<p>Activitats:</p>
<p>Les principals activitats del procés de provisioning són realitzar l'script (scripting), executar les proves i documentar.</p>
<ul>
<li>Scripting: defineix la seqüència, el temps i l'ordre per fer les proves de tots els elements del Datacenter. També permet defineix els registres a obtenir en cada prova. </li>
<li>Executa les proves: consisteix en executar una sèrie d'errors en els elements del sistema segons una seqüència establerta i tornar a restablir-los. Amb aquestes proves cal provar tant el sistema d'alimentació elèctrica, de fred, de detecció d'incèndis, ...</li>
<li>Documentació: cal registrar totes les proves realitzades i documentar-ho per tal deixar registrar l'estat i comportament de tot el sistema. La documentació serveix tant per veure el grau de compliment del sistema respecte els requisits inicials i el disseny, com per a la posterior explotació del mateix.</li>
</ul>
<p>Per executar les proves del sistema amb càrrega, s'utilitza el que es coneix com a "load banks". Són un conjunt d'elements per generar calor a la sala i així provar tant el sistema elèctric com el sistema de refrigeració.</p>
<p>El procés de commissioning no tant sols és utils per comprovar el grau de compliment  d'una instal·lació nova i identificar les mancances i limits del mateix. Sinó que també permet auditar un Datacenter construïts ja fa anys o en producció.</p>
<p>Bibliografia d'interés:</p>
<ul>
<li>ASHARE Guideline 0 - the Commissioning Process: Guia on descriuen totes les fases del procés de Commissioning.</li>
<li>APC White Paper #148 Data Center Projects: Commissioning.</li>
<li>APC White Paper #149 Ten Errors to Avoid When Commissioning a Data Center.</li>
</ul>
