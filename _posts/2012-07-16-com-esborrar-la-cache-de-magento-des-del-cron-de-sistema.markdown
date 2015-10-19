---
layout: post
status: publish
published: true
title: Com esborrar la cache de magento des del cron de sistema
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 397
wordpress_url: http://www.davidmataro.com/?p=397
date: !binary |-
  MjAxMi0wNy0xNiAxMDo1MDoxOCArMDAwMA==
date_gmt: !binary |-
  MjAxMi0wNy0xNiAwODo1MDoxOCArMDAwMA==
tags:
- sysadmin
- magento
comments: []
---
<p>Des de la administració de Magento es pot esborra la cache, però en alguns casos, es fa necessari esborrar la cache de manera automàtica. El següent script permet automatitzar esborrar la cache de Magento des del cron de sistema.</p>
<p><code lang="bash" width="558"><br />
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
<p>Configurar l'script en el cron mitjançant crontab -e</p>
<p><code lang="bash" width="558"><br />
01 08 * * * <full path to cron file>/cron_refresh_cache.php > /dev/null 2>&1<br />
</code></p>
