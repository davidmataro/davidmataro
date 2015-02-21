---
layout: post
status: publish
published: true
title: Como mover el catálogo de productos, clientes y pedidos de Magento
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 383
wordpress_url: http://www.davidmataro.com/?p=383
date: !binary |-
  MjAxMi0wNy0wOSAyMjo0MzozNSArMDAwMA==
date_gmt: !binary |-
  MjAxMi0wNy0wOSAyMDo0MzozNSArMDAwMA==
tags:
- sysadmin
- magento
comments: []
---
<p>Tarde o temprano, nos encontramos con la necesidad de mover el catálogo de productos, los clientes y los pedidos, incluyendo las facturas y órdenes de envío de un Magento a otro. Hay una manera de hacerlo bastante simple y efectiva.</p>
<p>Para ejecutar este procedimiento utilizaremos el script mysqldump_bypattern.sh, el cual permite exportar las tablas de una base de datos mysql según un patrón. Ver <a title="Cómo hacer un mysqldump de tablas según un patrón" href="http://www.davidmataro.com/es/2012/04/como-hacer-un-mysqldump-de-tablas-segun-un-patron/">Cómo hacer un mysqldump de tablas según un patrón</a>.</p>
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
<p>Es importante exportar e importar la tabla eav_entity_store, ya que contiene los contadores de pedidos, facturas y envíos.</p>
