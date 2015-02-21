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
wordpress_id: 279
wordpress_url: http://davidmataro.loc/?p=279
date: !binary |-
  MjAxMC0wMy0yOSAxNjo1MToxOCArMDAwMA==
date_gmt: !binary |-
  MjAxMC0wMy0yOSAxNjo1MToxOCArMDAwMA==
tags:
- datacenter
comments: []
---
<p><span class="Apple-style-span" style="font-family: Arial, sans-serif; font-size: 13px; line-height: 22px; "><span title="Quant s'afronta un projecte de contrucció d'un Datacenter, en la fase de disseny s'especifíquen tot un conjunt de subsistemes (sistema elèctric, sistema de refrigeració, sistema de detecció i extenció d'incèndis, sistemes de seguretat física i sistemes de" style="background-color: rgb(255, 255, 255); ">En cuanto se afronta un proyecto de construcción de un Datacenter, en la fase de diseño se especifican un conjunto de subsistemas (sistema eléctrico, sistema de refrigeración, sistema de detección y extinción de incendios, sistemas de seguridad física y sistemas de </span><span title="monitoratge i gestió), la relació entre cadascun dels elements i s'estima el comportament del conjunt amb càrrega." style="background-color: rgb(255, 255, 255); ">monitorización y gestión), la relación entre cada uno de los elementos y se estima el comportamiento del conjunto con carga. </span><span title="Després en la fase de desplegament, cada sistema es desplegat pel proveïdor corresponents - normalment un proveïdor per subsistema - i probat de manera individual." style="background-color: rgb(255, 255, 255); ">Después en la fase de despliegue, cada sistema es desplegado por el proveedor correspondientes - normalmente un proveedor para subsistema - y probado de manera individual. </span><span title="Cada proveïdor realitza la posta en marxa i les proves funcionals del subsistema que ha instal·lat per tal de disposar de la acceptació del client i facturar." style="background-color: rgb(255, 255, 255); ">Cada proveedor realiza la puesta en marcha y las pruebas funcionales del subsistema que ha instalado para disponer de la aceptación del cliente y facturar. </span><span title="En aquest procés, en cap moment es fa una comprovació de tot el conjunt." style="background-color: rgb(255, 255, 255); ">En este proceso, en ningún momento se hace una comprobación de todo el conjunto.</span><span title="I és aquí on el &quot;Commissioning&quot; pren importància." style="background-color: rgb(255, 255, 255); ">Y es aquí donde el "Commissioning" toma importancia.</p>
<p></span><span title="L'objectiu del &quot;Commissioning&quot; és provar el comportament de tots els subsistemes treballant conjuntament, amb la finalitat de comprovar si el desplegament de cada subsistema assoleix els objectius marcats en la fase de disseny i compleix amb els requisits inicials." style="background-color: rgb(255, 255, 255); ">El objetivo del "Commissioning" es probar el comportamiento de todos los subsistemas trabajando conjuntamente, con el fin de comprobar si el desarrollo de cada subsistema alcanza los objetivos marcados en la fase de diseño y cumple con los requisitos iniciales. </span><span title="És a dir, és un procés de validació de la instal·lació.">Es decir, es un proceso de validación de la instalación. </span><span title="També permet identificar les mancances de la instal·lació i els límits de la mateixa, informació que serà de molta utilitat en la fase d'explotació.">También permite identificar las carencias de la instalación y los límites de la misma, información que será de mucha utilidad en la fase de explotación. </span><span title="És per això que la pràctica del &quot;Commissioning&quot; es cada cop més utilitzada en la fase de desplegament d'un Datacenter.">Es por ello que la práctica del "Commissioning" es cada vez más utilizada en la fase de despliegue de un Datacenter.</p>
<p></span><span title="Com tot procés aquest està format per una entrada, un conjunt d'activitats i una sortida.">Como todo proceso este está formado por una entrada, un conjunto de actividades y una salida.</p>
<p></span><span title="Entrades:">Entradas:</p>
<ul>
<li>Lista de requisitos de diseño y construcción del datacenter. </li>
<li>El diseño del Datacenter. </li>
<li>Resultado de las pruebas realizadas en la puesta en marcha de cada uno de los componentes del Datacenter. </li>
</ul>
<p></span><span title="Sortides: .">Salidas:</p>
<ul>
<li>Script: contiene la lista de componentes probados y el tipo de test realizado y el resultado obtenido. </li>
<li><span title="Registre d'error: és una anàlisi FMEA (Failure Mode Effects Analysis) d'un components específica que ha fallat durant el test.">Registro de error: es un análisis <a href="http://davidmataro-es.blogspot.com/2009/12/analisis-fmea.html">FMEA</a> (Failure Mode Effects Analysis) de un componentes específica que ha fallado durante el test. </span><span title="Aquest identifica l'impacte de l'error i recomana les possibles solucions.">Este identifica el impacto del error y recomienda las posibles soluciones. </span></li>
<li><span title="Aquest identifica l'impacte de l'error i recomana les possibles solucions.">Resumen ejecutivo: describe las acciones las pruebas realizadas y un plan de acción. </span></li>
</ul>
<p></span><span title="Activitats:">Actividades:</p>
<p></span><span title="Les principals activitats del procés de provisioning són realitzar l'script (scripting), executar les proves i documentar.">Las principales actividades del proceso de commissioning son realizar el script (scripting), ejecutar las pruebas y documentar.</p>
<ul>
<li><span title="Scripting: defineix la seqüència, el temps i l'ordre per fer les proves de tots els elements del Datacenter." style="background-color: rgb(255, 255, 255); ">Scripting: define la secuencia, el tiempo y el orden para hacer las pruebas de todos los elementos del Datacenter. </span><span title="També permet defineix els registres a obtenir en cada prova.">También permite define los registros a obtener en cada prueba. </span></li>
<li><span title="També permet defineix els registres a obtenir en cada prova."><span title="Executa les proves: consisteix en executar una sèrie d'errors en els elements del sistema segons una seqüència establerta i tornar a restablir-los." style="background-color: rgb(255, 255, 255); ">Ejecuta las pruebas: consiste en ejecutar una serie de errores en los elementos del sistema según una secuencia establecida y volver a restablecer los mismos. </span><span title="Amb aquestes proves cal provar tant el sistema d'alimentació elèctrica, de fred, de detecció d'incèndis, ..." style="background-color: rgb(255, 255, 255); ">Con estas pruebas hay que probar tanto el sistema de alimentación eléctrica, de frío, de detección de incendios, ... </span></span></li>
<li><span title="També permet defineix els registres a obtenir en cada prova."><span title="Amb aquestes proves cal provar tant el sistema d'alimentació elèctrica, de fred, de detecció d'incèndis, ..." style="background-color: rgb(255, 255, 255); "><span title="Documentació: cal registrar totes les proves realitzades i documentar-ho per tal deixar registrar l'estat i comportament de tot el sistema.">Documentación: hay que registrar todas las pruebas realizadas y documentar esto para dejar registrar el estado y comportamiento de todo el sistema. </span><span title="La documentació serveix tant per veure el grau de compliment del sistema respecte els requisits inicials i el disseny, com per a la posterior explotació del mateix.">La documentación sirve tanto para ver el grado de cumplimiento del sistema respecto a los requisitos iniciales y el diseño, como para la posterior explotación del mismo. </span></span></span></li>
</ul>
<p></span><span title="Per executar les proves del sistema amb càrrega, s'utilitza el que es coneix com a &quot;load banks&quot;.">Para ejecutar las pruebas del sistema con carga, se utiliza lo que se conoce como "load banks". </span><span title="Són un conjunt d'elements per generar calor a la sala i així provar tant el sistema elèctric com el sistema de refrigeració.">Son un conjunto de elementos para generar calor en la sala y así probar tanto el sistema eléctrico como el sistema de refrigeración.</p>
<p></span><span title="El procés de commissioning no tant sols és utils per comprovar el grau de compliment d'una instal·lació nova i identificar les mancances i limits del mateix.">El proceso de commissioning no sólo es útil para comprobar el grado de cumplimiento de una instalación nueva e identificar las carencias y límites del mismo. </span><span title="Sinó que també permet auditar un Datacenter construïts ja fa anys o en producció.">Sino que también permite auditar un Datacenter construidos ya hace años o en producción.</p>
<p></span><span title="Bibliografia d'interés:">Bibliografía de interés:</p>
<ul>
<li>Asha Guideline 0 - the Commissioning Process: Guía donde describen todas las fases del proceso de Commissioning. </li>
<li>APC White Paper # 148 Data Center Projects: Commissioning. </li>
<li>APC White Paper # 149 Ten Errores to Avoid When Commissioning en Data Center.</li>
</ul>
<p></span></span></p>
