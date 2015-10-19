---
layout: post
status: publish
published: true
title: Aspectos a considerar para diseñar una estrategia de backup
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 318
wordpress_url: http://www.davidmataro.com/?p=318
date: !binary |-
  MjAxMi0wNC0xOSAyMDo0Mzo0OCArMDAwMA==
date_gmt: !binary |-
  MjAxMi0wNC0xOSAxODo0Mzo0OCArMDAwMA==
tags:
- sysadmin
- IT
- backup
- RPO
- RTO
comments: []
---
<p>Te has preguntado alguna vez qué sistema de copia de seguridad necesitas para tu empresa? esta  es una pregunta que desgraciadamente no se suele hacer. Son muchos los casos en que se implanta un sistema de copia de seguridad sin antes haber analizado qué estrategia es la más adecuada para la empresa.</p>
<p>A continuación, se describen un conjunto de consideraciones a tener en cuenta a la hora de diseñar una estrategia de backup. Estas se organizan en el proceso de copia, en los soportes de almacenamiento y en el proceso de recuperación.</p>
<p>Copia de seguridad:</p>
<ul>
<li>Que se debe copiar? qué ficheros o / y bases de datos deben copiarse?</li>
<li>Se deben hacer copias totales o incrementales?</li>
<li>¿Con qué frecuencia se debe hacer la copia?</li>
<li>¿Cuál es la cantidad de datos a copiar?</li>
<li>¿Cuál es la tasa de crecimiento anual?</li>
<li>¿Cuánto tiempo tarda en hacerse la copia de seguridad?</li>
<li>¿Qué consistencia tienen los datos copiados?</li>
<li>¿Cuál es la ventana de copia?</li>
</ul>
<p>Soporte de almacenamiento:</p>
<ul>
<li>¿Qué coste tiene el dispositivo de backup?</li>
<li>¿Cuál es su vida útil?</li>
<li>Se puede disponer de un dispositivo de reserva?</li>
<li>¿Cuál es el coste medio por GB copiado?</li>
<li>Donde se almacenan las copias?</li>
<li>onsite: cual es el plan de recuperación ante desastre?</li>
<li>offsite: qué coste tiene?</li>
<li>¿Durante cuánto tiempo se guardan las copias?</li>
<li>Hay limitaciones físicas de espacio?</li>
<li>El apoyo se deteriora?</li>
<li>¿De cuánto tiempo se dispone para recuperar los datos?</li>
</ul>
<p>Recuperación</p>
<ul>
<li>¿Qué copias necesitas para recuperar?</li>
<li>¿De cuánto tiempo se dispone para recuperar los datos si éstas están fuera (offsite)?</li>
<li>Que pasa si no se dispone de los datos?</li>
<li>Que pasa si los datos están corruptos?</li>
<li>¿Cuál es el tiempo esperado de recuperación o RTO (Recovery Time Objective)?</li>
<li>En qué punto se han de recuperar los datos o RPO (Recovery Point Objective)?</li>
</ul>
<p>Por otro lado, una estrategia de backup también debe considerar el tiempo de vida de los datos copiados. Para derminar, hay que considerar:</p>
<ul>
<li>¿Cuánto tiempo hay que retener la copia de seguridad?</li>
<li>Que pasa o hay que hacer en cuanto los datos ha expirado?</li>
<li>¿Cuál es el plan de rotación de los soportes de backup?</li>
<li>Que pasa con los soportes antiguos?</li>
<li>Puedes necesitar los backups antiguos?</li>
</ul>
<p>Finalmente, hay aspectos relacionados con el negocio que también hay que tener en cuenta al definir una estrategia de copia de seguridad:</p>
<ul>
<li>¿Qué valor o cuánto vale el negocio?</li>
<li>¿Qué valor tienen los datos?</li>
<li>¿Qué coste tiene una parada?</li>
<li>¿Quién es el coste medio por GB?</li>
<li>¿Cuánto cuestan los soportes y cuántos necesitas?</li>
<li>¿Cuál es el costo de operación? es decir, cuál es el coste de gestión del sistema de copia de seguridad?</li>
</ul>
<p>Responder a estas preguntas es un ejercicio que permite conocer las necesidades y capacidades del sistema de copia de seguridad más adecuado para la empresa. Y un ejercicio necesario para establecer una correcta estrategia de copia y recuperación de datos.</p>
