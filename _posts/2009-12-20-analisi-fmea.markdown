---
layout: post
status: publish
published: true
title: Anàlisi FMEA
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 26
wordpress_url: http://www.davidmataro.com/?p=26
date: !binary |-
  MjAwOS0xMi0yMCAyMDo0OTowMCArMDAwMA==
date_gmt: !binary |-
  MjAwOS0xMi0yMCAxODo0OTowMCArMDAwMA==
tags:
- itil
- risk
comments: []
---
<p><span style="color: #000000; font-size: 100%;">FMEA (Failure Modes and Effects Analysis) o altrament dit l'anàlisi de modes i efectes de fallo és una metodologia per a l'anàlisi dels potencials modes de fallo d'un sistema o element i classificar-los en base a la severitat, la probabilitat d'ocurrència i la capacitat de detecció. </span></p>
<p style="color: #000000;"><span style="font-size: 100%;">A continuació es descrieuen els conceptes basics de la metodologia i com aplicar-la per fer una anàlisi de riscos d'un sistema.</span></p>
<p style="color: #000000;"><span style="font-size: 100%;">Conceptes bàsics:</span></p>
<ul style="color: #000000;">
<li><span style="font-weight: bold; font-size: 100%;">Mode de fallada</span><span style="font-size: 100%;"> (Failure mode): és la manera en que es produeix un error o fallo. És a dir si analitzen un sistema d'alimentació elèctrica per exemple, un possible mode de fallo és la caiguda del subministrament de companyia.</span></li>
<li><span style="font-weight: bold; font-size: 100%;">Efectes</span><span style="font-size: 100%;"> (Failure effects): és l'efecte que produeix l'error o fallo sobre el sistema. Seguint amb l'exemple anterior, en cas de disposar un sistema de subministrament elèctric compost per el subministrament de companyia i un sistema dedundant composat per un generador autònom, l'efecte davant la caiguda de la corrent de companyia és la pèrdua de redundancia en el subministrament elèctric.</span></li>
<li><span style="font-weight: bold; font-size: 100%;">Causa</span><span style="font-size: 100%;"> (Failure cause): és l'element, el defecte o proces que ha iniciat el proces de fallo. En l'exemple pot ser un error en la central elèctrica.</span></li>
<li><span style="font-weight: bold; font-size: 100%;">Severitat</span><span style="font-size: 100%;"> (Severity): és la conseqüència que produeix el fallo, entesa com el grau de dany que aquest provoca.</span></li>
<li><span style="font-weight: bold; font-size: 100%;">Ocurrencia</span><span style="font-size: 100%;"> (Ocurrence): és la probabilitat que pasi el fallo en concret.</span></li>
<li><span style="font-weight: bold; font-size: 100%;">Detecció</span><span style="font-size: 100%;"> (Detection): és la capacitat de detecció del fallo o error. Entenent com a capacitat de detecció, quines son les accions proventives, de test, monitoratge per detectar l'error abans que aquest es manifesti i afecti al servei.</span></li>
<li><span style="font-weight: bold; font-size: 100%;">RPN</span><span style="font-size: 100%;"> (Risk Priotity Number): és el valor que s'obté de la multiplicació dels valors o graus determinats en la severitat, la ocurrència i la detecció: RPN = S x O x D. El RPN serveix per prioritzar les accions a realitzar sobre els sistemes o elements, de manera que els modes de fallo amb un RPN més alt, són les que podem considerar més prioritaries alhora d'emprendre accions corretives o preventives.</span></li>
</ul>
<p style="color: #000000;"><span style="font-size: 100%;">El procés o metodologia per fer una anàlisis FMEA consisteix en:</span></p>
<p style="margin-left: 14px; color: #000000;"><span style="font-size: 100%;">1. Detectar el model de fallo o error</span></p>
<p style="margin-left: 14px; color: #000000;"><span style="font-size: 100%;">2. Analitzar i qualificar la severitat</span></p>
<p style="margin-left: 14px; color: #000000;"><span style="font-size: 100%;">3. Analitzar i qualificar la probabilitat d'ocurrècnia</span></p>
<p style="margin-left: 14px; color: #000000;"><span style="font-size: 100%;">4. Analitzar i qualificar el grau de detecció</span></p>
<p style="margin-left: 14px; color: #000000;"><span style="font-size: 100%;">5. Determinar el valor de RPN</span></p>
<p style="margin-left: 14px; color: #000000;"><span style="font-size: 100%;">6. Emprendre les accions correctives i preventives</span></p>
<p style="color: #000000;"><span style="font-size: 100%;">Aquest procés format pel anterior sis punts, es pot executar cada vegada que es posa un nou sistema o procés en funcionament, o cada cop que aquest sistema o procés s'actualitza o és modifica, o cada cop que es detecta un problema en el mateix. És important, realitzar el procés cada cop que es modifica d'una manera o altre el sistema o procés, a fi de detectar possibles febleses del mateix i poder prendre les accions preventives i correctives abans que aquestes afectin el servei.</span></p>
<p style="color: #000000;"><span style="font-size: 100%;">També és important realizar aquest anàlisi en la fase de disseny d'un nou sistema, ja que permet incorporar al sistema les mesures necessàries per minimitzar el risc d'error del sistema i poder prendre les mesures correctives en cas que es produeixi l'error. </span></p>
<p style="color: #000000;"><span style="font-size: 100%;">Una manera de realitzar un analisis FMEA és utilitzant un full de càlcul tal i com es motre a l'exemple següent. On s'avalua l'error en el sistema d'arrancada remota del generador en un sistema de subministrament elèctric amb redundància.</span></p>
<p>&nbsp;</p>
