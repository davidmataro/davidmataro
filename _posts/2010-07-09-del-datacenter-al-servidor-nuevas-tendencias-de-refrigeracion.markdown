---
layout: post
status: publish
published: true
title: Del Datacenter al servidor, nuevas tendencias de refrigeración.
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 265
wordpress_url: http://davidmataro.loc/?p=265
date: !binary |-
  MjAxMC0wNy0wOSAxNjo0MjoyOCArMDAwMA==
date_gmt: !binary |-
  MjAxMC0wNy0wOSAxNjo0MjoyOCArMDAwMA==
tags:
- datacenter
- green
comments: []
---
<p>Hace días leí un post sobre servidores de <a href="http://www.ibm.com"> IBM </a> refrigerados por agua. Hoy he leído en <a href="http://www.datacenterknowledge.com/archives/2010/07/06/google-patents-liquid-cooled-server-sandwich/"> Data Center Knowledge </a> que <a href = "http://www.google.com"> Google </a> ha patentado el Liquid-Cooled 'Server Sandwith'. Esta no es la única patente de <a href="http://www.google.com"> Google </a> en cuanto a sistemas de refrigeración en entornos de alta densidad. Hace unos días ya publiqué un <a href="http://davidmataro.blogspot.com/2010/06/dissenys-de-datacenter-de-google-basats.html"> post </a> donde hacía referencia al diseño de datacenters basados en contenedores de Google.</p>
<p>Que dos gigantes como <a href="http://www.ibm.com"> IBM </a> y <a href="http://www.google.com"> Google </a> estén trabajando para refrigerar directamente los servidores en lugar del Datacenter lleva a ciertas reflexión sobre las nuevas tendencias en los sistemas de refrigeración del Datacenter o mejor dicho de los servidores.</p>
<p>Si recordamos cuál es el objetivo de un sistema de refrigeración en un Datacenter, este es disipar el calor que generan los servidores al coste más bajo posible. Por eso hemos ido evolucionando, pasamos de sistemas de climatización basados en aire-aire en sistemas de climatización basados en agua-aire, sistema más eficientes energéticamente. También hemos ido evolucionados en cuanto a la gestión del aire. Es decir, hace unos años se refrigera las salas donde se alojaban los servidores sin más. Después implementemos pasillos frío y calientes y a día de hoy estamos conteniendo el aire frío o conteniendo el aire caliente o desplegando datacenters en contenedores. Cada vez estamos llevando el aire frío más cerca del servidores reduciendo los m3 a climatizar. Y esto lo hacemos porque los servidores que debemos refrigerar están diseñados para ser refrigerados con aire.</p>
<p>Ahora, el cambio de tendencia que están marcando <a href="http://www.ibm.com"> IBM </a> y <a href="http://www.google.com"> Google </a> entre otros, cambiando la refrigeración de los servidores de aire a agua, provoca un cambio de la infraestructura de refrigeración del Datacenter. Si ahora llevan el agua de las refrigeradoras a los equipos de sala, ahora deberá llevarse hasta el rack de la misma manera que lo hacen los sistemas inRow tipo <a href="http://www.apc.com"> APC </a>. Pero además, el agua deberá llegar a los servidores y por eso tendrán que adaptarse los racks, como ya han hecho algunos fabricante adaptando puertas traseras refrigeradas por agua para entorno de alta densidad.</p>
<p>Otro elemento que cambia es la gestión, esto puede suponer la definitiva integración de los sistemas de control de las infraestructuras con los de los servidores y elementos de red. Controlando desde un único punto la temperatura de los procesadores, del agua de los circuitos internos de los servidores, de la velocidad de impulsión, consumo eléctrico, ... conjuntamente con la ocupación de memoria, de disco, tráfico de red, ...</p>
<p>Sin duda este cambio en la arquitectura de refrigració del servidores forzará a cambiar muchos elementos del Datacenter.</p>
