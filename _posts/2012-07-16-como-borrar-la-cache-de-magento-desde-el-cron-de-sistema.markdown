---
layout: post
status: publish
published: true
title: Como borrar la cache de Magento desde el cron de sistema
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 402
wordpress_url: http://www.davidmataro.com/?p=402
date: !binary |-
  MjAxMi0wNy0xNiAxMDo1NTo1NyArMDAwMA==
date_gmt: !binary |-
  MjAxMi0wNy0xNiAwODo1NTo1NyArMDAwMA==
tags:
- sysadmin
- magento
comments:
- id: 3838
  author: Andrea De Pirro
  author_email: andreadepirro@gmail.com
  author_url: http://www.yameveo.com
  date: !binary |-
    MjAxMi0wOS0wNCAxNjozMTozNCArMDAwMA==
  date_gmt: !binary |-
    MjAxMi0wOS0wNCAxNDozMTozNCArMDAwMA==
  content: ! 'Hemos actualizado el script. Aqui podeis encontrar la nueva version:

    https://github.com/akira28/magento-utils/blob/master/shell/cleanCache.php

    Esta versiÃ³n permite eligir cual cache borrar, y utiliza el sistema de shell
    de Magento.

    Ejemplos:

    php cleanCache.php all // limpia todas las caches

    php cleanCache.php --clean image // limpia la cache de imagenes

    php cleanCache.php info // imprime el listado de caches que se pueden borrar'
---
<p>Desde la administración de Magento se puede borrar la cache, pero en ocasiones, se hace necesario borrar la cache de Magento de forma automática. El siguiente script permite automatizar borrar la cache de Magento desde el cron de sistema.</p>
<p><code lang="bash"><br />
<?php<br />
date_default_timezone_set("Europe/Madrid");<br />
echo "Start Cleaning all caches at ... " . date("Y-m-d H:i:s") . "\n\n";<br />
ini_set("display_errors", 1);</p>
<p>require '../app/Mage.php';<br />
Mage::app('admin')->setUseSessionInUrl(false);<br />
Mage::getConfig()->init();</p>
<p>$types = Mage::app()->getCacheInstance()->getTypes();</p>
<p>try {<br />
    echo "Cleaning data cache... \n";<br />
    flush();<br />
    foreach ($types as $type => $data) {<br />
        echo "Removing $type ... ";<br />
        echo Mage::app()->getCacheInstance()->clean($data["tags"]) ? "[OK]" : "[ERROR]";<br />
        echo "\n";<br />
    }<br />
} catch (exception $e) {<br />
    die("[ERROR:" . $e->getMessage() . "]");<br />
}</p>
<p>echo "\n";</p>
<p>try {<br />
    echo "Cleaning stored cache... ";<br />
    flush();<br />
    echo Mage::app()->getCacheInstance()->clean() ? "[OK]" : "[ERROR]";<br />
    echo "\n\n";<br />
} catch (exception $e) {<br />
    die("[ERROR:" . $e->getMessage() . "]");<br />
}</p>
<p>try {<br />
    echo "Cleaning merged JS/CSS...";<br />
    flush();<br />
    Mage::getModel('core/design_package')->cleanMergedJsCss();<br />
    Mage::dispatchEvent('clean_media_cache_after');<br />
    echo "[OK]\n\n";<br />
} catch (Exception $e) {<br />
    die("[ERROR:" . $e->getMessage() . "]");<br />
}</p>
<p>try {<br />
    echo "Cleaning image cache... ";<br />
    flush();<br />
    echo Mage::getModel('catalog/product_image')->clearCache();<br />
    echo "[OK]\n";<br />
} catch (exception $e) {<br />
    die("[ERROR:" . $e->getMessage() . "]");<br />
}<br />
</code></p>
<p><a href="http://www.yameveo.com/development/php/flush-every-magento-cache-from-the-command-line" title="Flush every magento cache from the command line" target="_blank">Script original</a></p>
<p>Configurar el script en el cron de sistema con crontab -e</p>
<p><code lang="bash"><br />
01 08 * * * <full path to cron file>/cron_refresh_cache.php > /dev/null 2>&1<br />
</code></p>
