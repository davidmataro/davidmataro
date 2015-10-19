---
layout: post
status: publish
published: true
title: Probando Googlecl
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 271
wordpress_url: http://davidmataro.loc/?p=271
date: !binary |-
  MjAxMC0wNy0xOSAxNjo0Njo1OCArMDAwMA==
date_gmt: !binary |-
  MjAxMC0wNy0xOSAxNjo0Njo1OCArMDAwMA==
tags:
- google
comments: []
---
<p>Google ha publicado Googlecl, un shell que utiliza las APIs de Google i que permite gestionar los servicios de Google desde línea de comandos. Permite gestionar los servicios siguientes: </p>
<p>· Blogger<br />· Calendar<br />· Contacts<br />· Docs<br />· Picasa<br />· Youtube</p>
<p>Primero hay que instalar googlecl. En mi caso lo instalo sobre Mac OS X:</p>
<blockquote><p>1. Instalar Xcode</p>
<p>Lo instalo directamente desde el DVD de Snow Leopard. También se puede descargar de <a href="http://developer.apple.com/technologies/tools/xcode.html">Developer Tools</a>.</p>
<p>2. En caso de no tener instaladas las X, también hay que instalar las X. </p>
<p>3. Instalar <a href="http://www.macports.org">macports</a></p>
<p>Descargar MacPorts-1.9.1.pkg  de la web de <a href="http://www.macports.org">macports</a> para Snow Leopard e instalarlo.</p>
<p>Abrir un terminal y executar 'sudo port -v selfupdate' para asegurar que se tiene instalado la última release.</p>
<p>4. Instalar googlecl</p>
<p>sudo port install googlecl</p>
</blockquote>
<p>Para utilizar googlecl hay que ejecutar google seguido del servicio y de la tarea a ejecutar. Por ejemplo, para listar la lista de contactos hay que escribir:</p>
<p>$ google contacts list</p>
<p>La primera vez que se accede a un servicio pide que se autorize el acceso. Para ello, cuando ejecutar el comando por primera vez, te pide el usuario, y una vez entrado el usuario muestra una url con un token. Al poner esta url en un explorador se puede permitir o denegar el acceso. Siempre se puede volver a denegar el acceso conectando a google y seleccionando My Account -> Change authorized websites.</p>
<p>Obtener ayuda:</p>
<p>$ google --help</p>
<p>$ google help <service></p>
<p>A partir de aqui solo hay qeu dejar correr la imaginación para sacarle partido a googlecl. Un pequeño ejemplo. Si queremos hacer un backup de los contactos de google contacts podemos ejecutar el siguiente comando: </p>
<p>$ google contacts list > contacs.csv</p>
