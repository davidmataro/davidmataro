---
layout: post
status: publish
published: true
title: Probando ElasticHosts
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 263
wordpress_url: http://davidmataro.loc/?p=263
date: !binary |-
  MjAxMC0wOC0wOSAxNjo0MDoyMiArMDAwMA==
date_gmt: !binary |-
  MjAxMC0wOC0wOSAxNjo0MDoyMiArMDAwMA==
tags:
- cloud
- elastichost
comments: []
---
<p>Hoy he leído que <a href="http://www.serverbeach.co.uk/"> ServerBeach </a> ha lanzado un servicio de cloud utilizando la plataforma de <a href="http://www.elastichosts . com / "> ElasticHosts </a> y me he decidido a probarla. En el proceso de registro me he llevado la primera sorpresa. Se obligado poner un teléfono y que sea correcto ya que envían la mitad de la clave por mail y la otra mitad a través de un sms.</p>
<p>Una vez creada la cuenta se accede al panel de control vía https://lon-p.elastichosts.com/accounts/ con el mail como nombre de usuario y password que nos han enviado por mail y sms. Por defecto la demo tiene creada una máquina virtual con las siguientes características:</p>
<p>CPU: 2000 core MHz<br />
RAM: 1024 MB<br />
Drives: RedHat Fedora Linux 13 Live CD</p>
<p>El sistema asigna una ip dinámica en la máquina virtual y permite el acceso por vnc y a las estadísticas de tráfico desde el propio panel de control.</p>
<p>Para crear un nuevo servidor, desde la parte derecha del panel de control está la opción "Add server oro drive", aquí seleccionamos server, introduciendo un nombre - en mi caso test1 - y seleccionamos el tipo de instalación :</p>
<p>· Imagen pre-instalada: dispone de imágenes de debian, ubuntu y windows.</p>
<p>· Instalación desde un CD: dispone de cd de sación, debian, freebsd, knoppix, OpenSolaris, RedHat Fedora, Ubunto y Windows. esta opción permite por toda la instalación del sistema operativo de forma personalizada.</p>
<p>· Arrancar desde un live cd: también ofrece opciones en linux y windows.</p>
<p>· Arrancar desde una imagen de disco existente: hay que seleccionar la imagen previamente creada.</p>
<p>Para la prueba, he seleccionado crear el servidor desde una imagen pre-instalada y he seleccionado la imagen de un Debian Linux 4.0: System Base without X. Finalmente seleccionamos la capacidad del disco (1 GB).</p>
<p>Al pulsar Add, en el panel de control se muestra el nuevo servidor con nombre test1 y el nuevo disco también llamado test1. Podemos visualizar que en la vista del servidor indica que el disco del servidor es test1. El servidor permite las opciones de arrancar, editar y borrar.</p>
<p>Al seleccionar la opción de editar, se puede modificar el nombre del servidor, la cpu, la memoria, los discos la configuración de red y el password de acceso vnc. También hay unas opciones avanzadas donde se puede modificar el número de cores, el modelo de la tarjeta de red, configurar una lan privada y encriptar la sesión vnc.</p>
<p>Una vez arranque la máquina virtual test1 ya podemos entrar por vnc con el password que se indica en el panel de control. Una vez dentro, con el login root entramos directamente en la consola del sistema sin password. De modo que hay que poner una password. Una vez puesta la password la próxima vez que hacemos login ya nos pide la contraseña para entrar.</p>
<p>Por defecto, el único acceso al servidor virtual es vía vnc, de manera que si queremos acceso ssh, es necesario arrancar el servicio.</p>
<p>Ahora ya podemos empezar a trabajar con el nuevo servidor virtual.</p>
<p>A que destacar la posibilidad de crear vlan privadas para conectar las máquinas virtuales. Así permite desplegar arquitecturas de más de una capa con recursos de red dedicados.</p>
<p><a href="http://www.elastichosts.com/"> ElasticHosts </a> proporciona una API REST para la gestión remota de las máquinas virtuales vía llamadas HTTP. Para probarla podemos descargar el shell script elastichost.sh. Los datos de acceso desde la API están a My Account&gt; Profile, son el UUID y Secreto API Key. En la web está toda la documentación para utilizar la API.</p>
<p><a href="http://www.elastichosts.com/"> ElasticHosts </a> presenta dos modalidad de facturación, una por carga de crédito y otra por pago de una cuota mensual.</p>
<p>My account&gt; Billing: desde aquí podemos gestionar el consumo de recursos utilizados en la modalidad de prepago. Estos recursos se consumen por tramos horarios.</p>
<p>My account&gt; Subscription: permite gestionar las suscripciones, donde se paga una cuota mensual por unos recursos. Es decir, permite pagar un tanto mensual por una cantidad de recursos de MHz de CPU, de RAM, Disco y de Tráfico.</p>
<p>Para finalizar, <a href="http://www.elastichosts.com/"> ElasticHosts </a> presenta una interface de gestión simple y útil para la administración de servidores en cloud, la que se merece los premios que le están dando ultimamente. Sin duda esta es una muy buena opción para desplegar un servicio de alquiler de servidor en la modalidad de pago por uso.</p>
