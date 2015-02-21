---
layout: post
status: publish
published: true
title: Instalación automática de sistemas con Cobbler
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 267
wordpress_url: http://davidmataro.loc/?p=267
date: !binary |-
  MjAxMC0wNi0yNSAxNjo0Mzo0OCArMDAwMA==
date_gmt: !binary |-
  MjAxMC0wNi0yNSAxNjo0Mzo0OCArMDAwMA==
tags:
- datacenter
- opensource
- sysadmin
comments: []
---
<p>En todo Datacenter, la automatitizació de sistemas es una tarea imprescindible para minimizar los costes operativos de desarrollar un nuevo sistema, mantener la homogeneidad de los sistemas y evitar los errores humanos. Con la virtualización y la posibilidad de clonar máquinas virtuales rápidamente, automatizar la instalación de nuevos sistemas se ha simplificado. Sin embargo, no todos los sistemas son virtuales, de modo que hay también en la instalación de los sistemas físicos además de los virtuales.</p>
<p>Una herramienta para automaitzar la instalación de sistemas físicos y virtuales es <a href="https://fedorahosted.org/cobbler/"> Cobbler </a>. <a href="https://fedorahosted.org/cobbler/"> Cobbler </a> permite a los administradores de sistemas centralizar y automatizar la instalación de sistemas, ya sean físicos o virtuales. <a href="https://fedorahosted.org/cobbler/"> Cobbler </a> es un proyecto OpenSource de RedHat que se incluye dentro de <a href="https: / / fedorahosted.org / web /"> FedoraHoted </a>. <a href="https://fedorahosted.org/cobbler/"> Cobbler </a> se estructura en los elementos siguiente:</p>
<p>- Distribuciones: una distribución contiene toda la información realcionadas con el kernel, scripts, ... de una instalación. Es decir, es una distribución de Linux a partir de la cual se realiza una instalación.</p>
<p>- Perfil: un perfil es una particularización de la instalación de una distribución. Esta particularituzació se hace mediante la definición de un archivo de instalación kickstart. Un perfil por ejemplo puede representar la instalación de un servidor web, de un servidor de bbdd o de una estación de trabajo.</p>
<p>- Sistema: un sistema no es más que la instalación de un perfil sobre un servidor físico o virtual concreto.</p>
<p>- Repositorio: un repositorio es un mirror de las actualizaciones de una distribución concreta. De esta manera, los sistemas instalados desde <a href="https://fedorahosted.org/cobbler/"> Cobbler </a> actualizan los paquetes desde el mismo servidor de Cobbler y no desde Internet. Así, se acelera la actualización de paquetes y se reduce el tráfico de red Internet.</p>
<p>- Imágenes: son instalaciones que se hacen sobre un archivo ISO. De manera que esta imagen ISO se puede instalar tanto en un servidor físico como virtual.</p>
<p><a href="https://fedorahosted.org/cobbler/"> Cobbler </a> dispone de dos interface de trabajo, una vía línea de comandos y una segunda vía web. Desde ambas interface se pueden gestionar las distribuciones, perfiles, sistemas y repositorios.</p>
<p>Desde el punto de vista de un Datacenter, <a href="https://fedorahosted.org/cobbler/"> Cobbler </a> permite automatizar la instalación de nuevos servidor de hosting dedicado o virtual, la re-instalación de forma rápida un servidor que ha fallado e incluso, disponer de plantillas de servidores (perfiles) que se instalen automáticamente en función de la necesidad de carga. Por ejemplo, en caso de un portal web con un frontal formado por N servidores Apache, si aumenta la demanda se pueden instalar nuevos servidores Apache de manera rápida e incluso de manera automática. Y este servidores Apache se instalan basados en una plantilla (perfil) determinada.</p>
<p>Más información en <a href="https://fedorahosted.org/cobbler/"> Cobbler </a>.</p>
