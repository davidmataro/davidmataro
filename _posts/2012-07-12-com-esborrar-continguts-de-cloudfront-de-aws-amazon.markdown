---
layout: post
status: publish
published: true
title: Com esborrar continguts de CloudFront de AWS Amazon
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 389
wordpress_url: http://www.davidmataro.com/?p=389
date: !binary |-
  MjAxMi0wNy0xMiAxNjoxNToyMCArMDAwMA==
date_gmt: !binary |-
  MjAxMi0wNy0xMiAxNDoxNToyMCArMDAwMA==
tags:
- sysadmin
- aws
- cloudfront
comments: []
---
<p>Si necessites esborrar un contingut del CDN de AWS Amazon, CloudFront abans de que aquest expiri i CloudFront el torni a anar a buscar a l'origen, pots fer-ho invalidant el contingut des de la Consola de AWS Amazon.</p>
<p>1. Connectar a la consola de AWS Amazon</p>
<p>2. Seleccionar CloudFront</p>
<p>3. Seleccionar la distribució on hi ha el contingut i premer el botó "Distribution Setting".</p>
<p>4. Seleccionar la opció "Invalidations"</p>
<p>6. Entrar el path del objecte que volem invalidar. Per exemple:</p>
<p>/image/image1.jpg</p>
<p>7. Premer "Invalidate"</p>
<p>El procés d'invalidació triga uns minuts. Un cop l'objecte ha estat invalidat, quant es faci la primera petició a l'objecte,  CloudFront l'anirà a buscar a l'origen.</p>
<p>Cal tenir en compte que AWS Amazon cobra $0,005 per invalidar continguts, tot i que els primers 1000 objectes invalidats per més no tenen cost.</p>
