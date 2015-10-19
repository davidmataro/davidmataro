---
layout: post
status: publish
published: true
title: Provant Googlecl
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 36
wordpress_url: http://www.davidmataro.com/?p=36
date: !binary |-
  MjAxMC0wNi0xOSAxNjozNTowMCArMDAwMA==
date_gmt: !binary |-
  MjAxMC0wNi0xOSAxNDozNTowMCArMDAwMA==
tags:
- google
- mac
comments: []
---
<p>Google a publicat Googlecl, un shell que utilitza les APIs de Google i que permet gestionar els serveis de Google des de la linia de comandes. Ara mateix permet gestionar els serveis següents:</p>
<p>· Blogger<br />· Calendar<br />· Contacts<br />· Docs<br />· Picasa<br />· Youtube</p>
<p>Primer de tot hem d'instal·lar-lo. En el meu cas l'instal·lo sobre Mac OS X:<br />
<blockquote>1. Instal·lar Xcode</p>
<p>En el meu cas l'instal·lo directament del DVD de Snow Leopard. També es por descarregar de <a href="http://developer.apple.com/technologies/tools/xcode.html">Developer Tools</a>.</p>
<p>2. En cas de no tenir instal·lades les X, cal instal·lar-les. En el meu cas ja les tinc instal·lades.</p>
<p>3. Instal·lar <a href="http://www.macports.org">macports</a></p>
<p>Descarregar el MacPorts-1.9.1.pkg  de la web de <a href="http://www.macports.org">macports</a> per a Snow Leopard i instal·lar-lo.</p>
<p>Obrir un terminal i executar 'sudo port -v selfupdate' per tal d'assegurar que disposem de la últime relaease.</p>
<p>4. Instal·lar googlecl</p>
<p>sudo port install googlecl</p>
</blockquote>
<p>Per utilitzar googlecl cal escriure google, seguit del servei i de la tasca a executar. Per exemple, si volem llistar tota la llista de contactes cal escriure:</p>
<p>$ google contacts list</p>
<p>La primera vegada que s'accediex a un servei demana que autoritzin l'accés. Per això, quant executes per primera vegada una comanda, primera demana l'usuari i després mostra una url amb un token. Posant aquesta url en un navegador podem autoritzar o denar l'accés. Sempre podem tornar a denegar l'accés connectant a Google i seleccionat My Account -> Change authorized websites.</p>
<p>Per obtenir ajuda cal:</p>
<p>$ google --help</p>
<p>$ google help <service></p>
<p>A partir d'aquí, sols cal utilitzar la imaginació per treure suc a googlecl. Un petit exemple, si volem fer una còpia de seguretat dels contactes que tenim a google contacts podem executar cada dia la comanda següent:</p>
<p>$ google contacts list > contacs.csv</p>
