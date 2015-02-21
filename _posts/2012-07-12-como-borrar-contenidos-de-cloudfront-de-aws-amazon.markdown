---
layout: post
status: publish
published: true
title: Como borrar contenidos de CloudFront de AWS amazon
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 392
wordpress_url: http://www.davidmataro.com/?p=392
date: !binary |-
  MjAxMi0wNy0xMiAxNjoxODozMSArMDAwMA==
date_gmt: !binary |-
  MjAxMi0wNy0xMiAxNDoxODozMSArMDAwMA==
tags:
- sysadmin
- aws
- cloudfront
comments: []
---
<p>Si necesitas borrar un contenido del CDN de AWS Amazon CloudFront antes de que este expire y CloudFront lo vuelva a ir a buscar en su origen, puedes hacerlo invalidando el contenido desde la Consola de AWS Amazon.</p>
<p>1. Conectar a la consola de AWS Amazon</p>
<p>2. Seleccionar CloudFront</p>
<p>3. Seleccionar la distribución donde se encuentra el contenido y pulsar el botón "Distribution Setting".</p>
<p>4. Seleccionar la opción "Invalidations"</p>
<p>6. Entrar el path del objeto que queremos invalidar. Por ejemplo:</p>
<p>/ image/image1.jpg</p>
<p>7. Pulsar "Invalidate"</p>
<p>El proceso de invalidación tarda unos minutos. Una vez el objeto ha sido invalidado, cuando se haga la primera petición al objeto, CloudFront la irá a buscar en su origen.</p>
<p>Hay que tener en cuenta que AWS Amazon cobra $ 0.005 para invalidar contenidos, aunque los primeros 1000 objetos invalidados por mes no tienen coste.</p>
