---
layout: post
status: publish
published: true
title: Gestión segura de acceso SSH con Initr
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 256
wordpress_url: http://davidmataro.loc/?p=256
date: !binary |-
  MjAxMC0xMS0wNSAxNjoyOToxNCArMDAwMA==
date_gmt: !binary |-
  MjAxMC0xMS0wNSAxNjoyOToxNCArMDAwMA==
tags:
- initr
- ssh
comments: []
---
<p>Uno de los problemas con que se enfrenta todo administrador de sistemas es la gestión permisos de acceso remoto a los servidores. Es decir, quién puede y quién no puede entrar en un servidor con permisos de administrador (root). Otro problema de disponer de acceso remoto a los servidores es la gestión de la seguridad: puertos de acceso abiertos a todo el mundo, complicadas gestiones de firewall's, cambios de password's o revocaciones de certificados, ... en definitiva una problemática que suele costar muchas horas de administración de sistemas.</p>
<p>Estas problemáticas y los costes de administración asociados se solucionan con ssh_station. ssh_station es un módulo que <a title="Ingent Grup" href="http://www.ingent.net" target="_blank">Ingent Grup</a> ha desarrollado dentro del proyecto <a title="Initr" href="http://www.initr.org" target="_blank">Initr</a> que permite automatizar la gestión de los permisos de acceso ssh a los servidores. Las características principales de ssh_stations son:</p>
<ul>
<li>Acceso por certificado digital:</li>
</ul>
<p>El acceso a los servidores o nodos se realiza mediante certificado digital y se suprime el acceso por login y password, evitando así ataques de fuerza bruta que pueden vulnerar un servidor.</p>
<ul>
<li>Administración centralizada:</li>
</ul>
<p>La gestión de permisos de acceso ssh a los servidores se realiza vía web desde <a title="Initr" href="http://www.initr.org" target="_blank">Initr</a>. Todo usuario dado de alta en <a title="Initr" href="http://www.initr.org" target="_blank">Initr</a> publica su clave pública dentro de su perfil de usuario. Este clave es utilizada por ssh_station para proporcionar acceso a los servidores.</p>
<p>La gestión de permisos de acceso se hace por proyectos. Un usuario está asignado a uno o más proyectos y dispone de acceso ssh vía certificado digital a todos los nodos asignados al proyecto. Es decir, los proyectos actúan como grupos.</p>
<ul>
<li>Acceso centralizado:</li>
</ul>
<p>ssh_station permite acceder a los servidores desde un único punto (ssh_server_station). De modo que no es necesario que el operador o administrador de sistemas recuerde la ip del servidor donde se quiere conectar, sino que se conecta por ssh al ssh_server_station y éste le proporciona la lista de servidores donde tiene permiso de acceso. Entonces es tan sencillo como elegir el servidor donde se quiere acceder y establecer la conexión ssh.</p>
<p>[caption id="attachment_104" align="alignnone" width="300" caption="ssh_station connection"]<a href="http://davidmataro.loc/wp-content/uploads/2010/11/Screen-shot-2010-11-02-at-10.43.26-AM.png"><img src="http://davidmataro.loc/wp-content/uploads/2010/11/Screen-shot-2010-11-02-at-10.43.26-AM-300x216.png" alt="" title="ssh_station" width="300" height="216" class="size-medium wp-image-104" /></a>[/caption]</p>
<p>La conexión ssh establecida no se hace como root, sino que se hace con un usuario sin permisos, obligando a hacer sudo para adquirir permisos de root.Esto aporta un nivel más de seguridad.</p>
<ul>
<li>Acceso SSH transparente:</li>
</ul>
<p>Otra característica importante de ssh_station es el acceso ssh transparente. Es decir, permite acceder vía ssh a los nodos que están detrás de un firewall sin tener que configurar ningún regla en el firewall. Esta funcionalidad permite que los servidores no tengan el puerto 22 abierto a Internet, evitando así ataques de seguridad en el puerto 22.</p>
<p>Las ventajas de ssh_station se hacen más evidentes en cuanto se está administrando servidores distribuidos en diferentes Centros de Datos o clouds públicos, donde se acostumbra a tener entornos heterogéneos: diferentes firewall's, interlocutores, herramientas de gestión, etc .. En este entorno llevar la gestión de acceso con <a title="Initr" href="http://www.initr.org" target="_blank">Initr</a> ahorra muchas horas de administración de sistemas y reduce los riesgos ante ataques a los servidores.</p>
<p>Otra característica importante de ssh_station es la posibilidad de establecer túneles seguros a otros puertos (aplicaciones web) del servidor o de servidores de la red donde está conectado el servidor. Y acceder a estas aplicaciones en remoto y de forma segura. La explicación de esta funcionalidad la dejaré para otro post.</p>
