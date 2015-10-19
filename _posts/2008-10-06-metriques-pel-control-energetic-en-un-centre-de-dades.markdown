---
layout: post
status: publish
published: true
title: Mètriques pel control energètic en un Centre de Dades
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 11
wordpress_url: http://www.davidmataro.com/?p=11
date: !binary |-
  MjAwOC0xMC0wNiAyMzoyNjowMCArMDAwMA==
date_gmt: !binary |-
  MjAwOC0xMC0wNiAyMToyNjowMCArMDAwMA==
tags:
- datacenter
- green
comments: []
---
<div><span class="Apple-style-span"   style=" ;font-family:Verdana;font-size:13px;">
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;">Ja fa temps que m'interessa el control de l'eficiència energètica dels Centres de Dades. Sens dubte, col·laborar amb un datacenter com </span><a href="http://www.digitalparks.com/"><span class="Apple-style-span" style="font-family: georgia;">Digital Parks</span></a><span class="Apple-style-span" style="font-family: georgia;"> m'ajuda a satisfer aquest interès i a més portar-lo a la pràctica. </span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;"><br /></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;">Un dels aspectes més importants alhora de controlar i millorar la eficiència energètica d'un datacenter és establir mètriques de control que permetin determinar la seva eficiència. Des de </span><a href="http://www.thegreengrid.org/"><span class="Apple-style-span" style="font-family: georgia;">The Green Grid</span></a><span class="Apple-style-span" style="font-family: georgia;"> proposen dues mètriques, el PUE (Power Usage Effectiveness) i el seu recíproc DCiE (Data Center Infraestructure Efficiency). </span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;"><br /></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;"><br /></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;">El PUE es defineix com:</span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;"><br /></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;"><br /></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-weight: bold;"><span class="Apple-style-span" style="font-family: georgia;">                    Total Facility Power</span></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-weight: bold;"><span class="Apple-style-span" style="font-family: georgia;">El PUE = ----------------------------- <br /></span></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-weight: bold;"><span class="Apple-style-span" style="font-family: georgia;">                  IT Equipement Power</span></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;"><br /></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;"><br /></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;">i el DCiE es defineix com:</span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;"><br /></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;"><br /></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-weight: bold;"><span class="Apple-style-span" style="font-family: georgia;">                1         IT Equipement Power</span></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-weight: bold;"><span class="Apple-style-span" style="font-family: georgia;">DCiE = ----- = -----------------------------  (x 100%)</span></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-weight: bold;"><span class="Apple-style-span" style="font-family: georgia;">             PUE        Total Facility Power</span></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;"><br /></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;"><br /></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;">on:</span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;"><br /></span></div>
<div style="margin-top: 0px; margin-bottom: 0px; ">
<ul>
<li style="text-align: justify;"><span class="Apple-style-span" style="font-weight: bold; "><span class="Apple-style-span" style="font-family: georgia;">IT equipement Powe</span></span><span class="Apple-style-span" style="font-weight: bold; "><span class="Apple-style-span" style="font-family: georgia;">r</span></span><span class="Apple-style-span" style="font-family: georgia;"> és el total d'energia consumit pels servidors, sistemes de storage, electrònica de xarxa, sistemes de gestió, i equipament suplementari com kvm, pantalles, o qualsevol altre element utilitzat pel control i la gestió del datacenter.<br /></span></li>
</ul>
</div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;"><br /></span></div>
<div style="margin-top: 0px; margin-bottom: 0px; ">
<ul>
<li style="text-align: justify;"><span class="Apple-style-span" style="font-weight: bold; "><span class="Apple-style-span" style="font-family: georgia;">Total Facility Power</span></span><span class="Apple-style-span" style="font-family: georgia;"> inclou per una banda l'energia consumida en el procés de distribució de la mateixa, com ups, pdu's, bateries i les pèrdues d'energia de la pròpia xarxa de distribució. D'altra banda, també inclou l'energia consumida pel sistema de climatització i pel sistema d'enllumenat. <br /></span></li>
</ul>
</div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;"><br /></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;"><br /></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;">Per entendre millor les mètriques PUE i DCiE, que millor que un exemple: un PUE de 3 indica que el consum total d'energia del datacenter és tres vegades més que l'energia consumida pel l'equipament IT. D'altra banda un DCiE del 33%, que equival a un PUE de 3, indica que l'equipament IT consumeix un 33% de l'energia del datacenter.</span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;"><br /></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;"><br /></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;">Sens dubte, el primer pas per millorar la eficiència energètica d'un datacenter es determinar les mètriques de control que ens permeten fer el seguiment dels processos de millora. I per això, cal fer la presa de dades del consum de cadascun dels elements del datacenter i fer-la de manera periòdica. Així dons<br />
, si fins ara els sistemes de monitoratge sols tenien en compte la lectura de variables de servidors i elements de xarxa amb objectiu de generar alertes i guardar un històric per poder fer un anàlisi de capacitats, ara el sistema de monitoratge s'estén al control del consum d'energia.</span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;"><br /></span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "><span class="Apple-style-span" style="font-family: georgia;">Per finalitzar, remarcar que aquestes mètriques són útils per fer el seguiment dels processos de millora de la eficiència energètica del datacenter, i també per fer comparacions entre diferents Centres de Dades. Un altre aspecte importat de disposar d'aquestes mètriques és que amb elles s'obté la capacitat de calcular el cost real total d'un o un grup de sistemes allotjats en el datacenter.</span></div>
<div style="text-align: justify;margin-top: 0px; margin-bottom: 0px; "></div>
<p></span></div>
