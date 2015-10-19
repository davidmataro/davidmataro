---
layout: post
status: publish
published: true
title: Com moure el catàleg de productes, clients i comandes de Magento
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 377
wordpress_url: http://www.davidmataro.com/?p=377
date: !binary |-
  MjAxMi0wNy0wOSAyMjozNzoyNyArMDAwMA==
date_gmt: !binary |-
  MjAxMi0wNy0wOSAyMDozNzoyNyArMDAwMA==
tags:
- sysadmin
- magento
comments: []
---
<p>Tard o d'hora, ens trobem amb la necessitat de moure el catàleg de productes, els clients i les comandes, incloent les factures o ordres d'enviament d'un Magento a un altre. Hi ha una manera de fer-ho força simple i efectiva.</p>
<p>Per executar aquest procediment utilitzarem l'script mysqldump_bypattern.sh, el qual permet exportar les taules d'una base de dades mysql segon un patró. Veure <a title="com fer un mysqldump de taules segons un patró" href="http://www.davidmataro.com/2012/04/com-fer-un-mysqldump-de-taules-segons-un-patro/">Com fer un mysqldump de taules segons un patró</a>.</p>
<p>Exportar:<br />
<code lang="bash"><br />
$ mysqldump_bypattern.sh sales% sales.dump<br />
$ mysqldump_bypattern.sh customer% customer.dump<br />
$ mysqldump_bypattern.sh catalog% catalog.dump<br />
$ mysqldump_bypattern.sh eav_entity_store eav_entity_store.dump<br />
</code></p>
<p>Importar:<br />
<code lang="bash"><br />
$ mysql -u -p &lt; sales.dump<br />
$ mysql -u -p &lt; customer.dump<br />
$ mysql -u -p &lt; catalog.dump<br />
$ mysql -u -p &lt; eav_entity_store.dump<br />
</code></p>
<p>És important exportar i importar la taula eav_entity_store, ja que conté els comptadors de comandes, factures i enviaments.</p>
