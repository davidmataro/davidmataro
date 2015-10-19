---
layout: post
status: publish
published: true
title: RedHat Enterprise Virtualization Conference 2010
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 97
wordpress_url: http://www.davidmataro.com/?p=97
date: !binary |-
  MjAxMC0xMC0yNyAwOTo0Nzo0NSArMDAwMA==
date_gmt: !binary |-
  MjAxMC0xMC0yNyAwNzo0Nzo0NSArMDAwMA==
tags:
- datacenter
- redhat
- sysadmin
comments:
- id: 2704
  author: Jacqueline Evancho
  author_email: Barnell327@rocketmail.com
  author_url: http://jackie-evancho.us/
  date: !binary |-
    MjAxMC0xMC0yOCAxNTowNzo1MiArMDAwMA==
  date_gmt: !binary |-
    MjAxMC0xMC0yOCAxMzowNzo1MiArMDAwMA==
  content: It really makes sense, hope that you will add some more soon!
- id: 2705
  author: David MatarÃ³
  author_email: dmataro@gmail.com
  author_url: http://www.davidmataro.com
  date: !binary |-
    MjAxMC0xMS0wMiAwOTozMzozMSArMDAwMA==
  date_gmt: !binary |-
    MjAxMC0xMS0wMiAwNzozMzozMSArMDAwMA==
  content: about redhat coud, you can obtain more information from http://www.redhat.com/cloud
- id: 2706
  author: JM Gris
  author_email: jm.gris@gmail.com
  author_url: http://jmgris.blogspot.com
  date: !binary |-
    MjAxMC0xMS0xNCAxMTo0NzozOSArMDAwMA==
  date_gmt: !binary |-
    MjAxMC0xMS0xNCAwOTo0NzozOSArMDAwMA==
  content: ! 'Vinc del VMworld de Conpehagen.

    La tendencia es exactament aquesta i per altra banda, la "persona" que aixi li
    diuen el saxons al usuari+ vol portar adminicles mes lleugers i sense inteligencia.

    El 40% dels assistents portavem iPad i el 80% alguna cosa electronica per pendre
    notes, sigui Notebook, iPad, netbook.

    Aixo cambia ja!'
---
<p>Ahír vaig  estar la  conferència que va fer <a title="RedHat" href="http://www.redhat.com" target="_blank">RedHat </a>al World Trade Center de Barcelona anomenada "RedHat Enterprise Virtualization". <a href="http://www.rompalasbarreras.es/" target="_blank">Aquí</a> hi ha la agenda i més informació sobre l'acte.</p>
<div>De la conferència m'agradaria destacar algunes dades que ha donat el consultor de IDC durant la seva exposició. M'he quedat amb:</div>
<ul>
<li>La despesa en hardware es mante estable tot i la baixada del cost dels servidors x86. El fet, es que tot i que ha baixat el cost dels servidors, ha augmentat la demanda, de manera que la despesa s'ha mantingut estable.</li>
<li>Augmenta el cost energètic del datacenter i el cost de gestió i administració.</li>
<li>Degut a que cada dia hi ha més dependència de la tecnologia en els processos empresarials, el cost de parada (downtime) és més alt. Fet que augmenta la despesa de les empreses en sistemes d'alta disponibilitat i de recuperació davant de desastres.</li>
</ul>
<div>
<div>Segons aquest consultor la solució a aquest augment de costos és la Virtualització. Tot i que la virtualització és na solució per reduïr els costos he trobat a faltar aspectes com la gestió del clima i de la administració dels sistemes que comento a continuació.</div>
</div>
<div>Tot i que la virtualització porti una reducció del consum global, concentra el consum en menys espai i  augmenta la densitat de potència de rack. Aquest fet fa que tot i tenir potència frigorífica suficient, si aquesta no es gestiona de manera correcta pot provocar punts calents dins del Data Center. Un altre aspecte important a futur és el creixement de la infraestructura virtual. A mesura que la infraestructura virtual creix aumenta el número de servidrs físics, de  storage, etc.. En aquest escenari de creixement hi ha el  risc de sobrepasar la capacitat electrica i de refrigeració del Centre de Dades. De manera que és molt important fer anàlisis de capacitat de la infraestructura elèctrica i de refrigeració, a fi de controlar els limits del Centre de Dades i no sobrepassar-los.</div>
<div>Per altre banda hi ha els costos d'administració. Al virtualitzar augmenta el número de sistemes a administrar i aquest augment pot ser desmesurat, ja que el cost de crear un servidor virtual es molt inferior al de posar un servidor físic. Per tant, es imprescindible aplicar metodologies de gestió que no faci que apareguin màquines virtuals com a volets. I d'altre banda, per tal de reduïr els cotos de administració cal automatitzar al màxim possible la administració.</div>
<p>Per finalitzar m'agradaria destacar també la presetació de cas de Viajes Barceló i la de del cas pràctic d'automatització de sistemes. En aquest últim cas, s'ha mostrar com amb <a title="Cobbler" href="https://fedorahosted.org/cobbler/" target="_blank">cobbler</a> - eina que vaig desplegar a <a title="Digital Parks" href="http://www.digitalparks.com" target="_blank">Digital Parks</a> per a la instal·lació automàtica de servidors físics i vituals - gestiona la instal·lació de servidors físics i virtuals i com amb satellite la gestiona la distribució de paquets de software. Sens dubte, a <a title="RedHat" href="http://www.redhat.com" target="_blank">RedHat</a> a banda de distribuïr el <a title="RHEV" href="http://www.redhat.com/virtualization/rhev/" target="_blank">REHV</a> i donar suport, pensen en la reducció del cost operatius de la infraestructura virtual en base a la automatització dels processos d'administració, fet que els posiciona com a una bona alternativa a d'altres sistemes de virtualització del mercat.</p>
