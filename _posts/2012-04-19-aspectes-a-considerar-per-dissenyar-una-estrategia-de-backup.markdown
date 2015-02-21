---
layout: post
status: publish
published: true
title: Aspectes a considerar per dissenyar una estratègia de backup
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 314
wordpress_url: http://www.davidmataro.com/?p=314
date: !binary |-
  MjAxMi0wNC0xOSAyMDo0Mzo0MSArMDAwMA==
date_gmt: !binary |-
  MjAxMi0wNC0xOSAxODo0Mzo0MSArMDAwMA==
tags:
- sysadmin
- IT
- backup
- RPO
- RTO
comments:
- id: 3504
  author: Com automatitzar snapshots a S3 de AWS Amazon - David MatarÃ³ i Ciller
  author_email: ''
  author_url: http://www.davidmataro.com/2012/05/com-automatitzar-snapshots-a-s3-de-aws-amazon/
  date: !binary |-
    MjAxMi0wNS0yMiAwOTo1MjoxMiArMDAwMA==
  date_gmt: !binary |-
    MjAxMi0wNS0yMiAwNzo1MjoxMiArMDAwMA==
  content: ! '[...] el post anterior he descrit els aspectes a considerar per dissenyar
    una estratÃ¨gia de backup que [...]'
---
<p>T'has preguntat mai quin sistema de còpia de seguretat necessites per la teva empresa? aquesta es una pregunta que malauradament no s'acostuma a fer. Son molts els casos en que s'implanta un sistema de còpia de seguretat sense abans haver analitzar quina estratègia es la més adequada per a l'empresa.</p>
<p>A continuació, es descriuen un conjunt de consideracions que cal tenir en compte alhora de dissenyar una estratègia de backup. Aquestes s'organitzen en el procés de còpia, en el suports d'emmagatzematge y en el procés de recuperació.</p>
<p>Còpia de seguretat:</p>
<ul>
<li>Que s'ha de copiar? quins fitxers o/i bases de dades s'han de copiar?</li>
<li>S'han de fer copies totals o incrementals?</li>
<li>Amb quina freqüència s'ha de fer la còpia?</li>
<li>Quina es la quantitat de dades a copiar?</li>
<li>Quina es la taxa de creixement anual?</li>
<li>Quant de temps triga a fer-se la copia de seguretat?</li>
<li>Quina consistència tenen les dades copiades?</li>
<li>Quina es la finestra de còpia?</li>
</ul>
<p>Suport d'emmagatzematge:</p>
<ul>
<li>Quin cost té el dispositiu de backup?</li>
<li>Quina es la seva vida útil?</li>
<li>Es pot disposar d'un dispositiu de reserva?</li>
<li>Quin es el cost mig per GB copiat?</li>
<li>On s'emmagatzemen les copies?</li>
<li>onsite: quin es el pla de recuperació davant desastre?</li>
<li>offsite: quin cost té?</li>
<li>Durant quant temps es guarden les copies?</li>
<li>Hi ha limitacions físiques d'espai?</li>
<li>El suport es deteriora?</li>
<li>De quant de temps es disposa per recuperar les dades?</li>
</ul>
<p>Recuperació</p>
<ul>
<li>Quines copies necessites per recuperar?</li>
<li>De quant de temps es disposa per recuperar les dades si aquestes estan fora (offsite)?</li>
<li>Que passa si no es disposa de les dades?</li>
<li>Que passa si les dades estan corruptes?</li>
<li>Quin es el temps esperat de recuperació o RTO (Recovery Time Objective)?</li>
<li>En quin punt s'han de recuperar les dades o RPO (Recovery Point Objective)?</li>
</ul>
<p>D'altre banda, una estratègia de backup també ha de considerar el temps de vida de les dades copiades. Per derminar-lo, cal considerar:</p>
<ul>
<li>Quant de temps cal retenir la còpia de seguretat?</li>
<li>Que passa o cal fer quant les dades ha expirat?</li>
<li>Quin es el pla de rotació dels suports de backup?</li>
<li>Que passa amb els suports antics?</li>
<li>Pots necessitar els backups antics?</li>
</ul>
<p>Finalment, hi ha aspectes relacionats amb el negoci que també cal tenir en compte alhora de definir una estratègia de còpia de seguretat:</p>
<ul>
<li>Quin valor o quant val el negoci?</li>
<li>Quin valor tenen les dades?</li>
<li>Quin cost té una parada?</li>
<li>Qui es el cost mig per GB?</li>
<li>Quant costen els suports i quants en necessites?</li>
<li>Quin es el cost d'operació? és a dir, quin es el cost de gestió del sistema de còpia de seguretat?</li>
</ul>
<p>Respondre a aquestes preguntes es un exercici que permet conèixer les necessitats i capacitats del sistema de còpia de seguretat més adequat per a l'empresa. I un exercici necessari per establir una correcta estratègia de còpia i recuperació de dades.</p>
