---
layout: post
status: publish
published: true
title: Com fer un mysqldump de taules segons un patró
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 323
wordpress_url: http://www.davidmataro.com/?p=323
date: !binary |-
  MjAxMi0wNC0yNCAxMjozNzozNSArMDAwMA==
date_gmt: !binary |-
  MjAxMi0wNC0yNCAxMDozNzozNSArMDAwMA==
tags:
- sysadmin
- mysql
comments:
- id: 3736
  author: Como moure el catÃ leg de productes, clients i comandes de Magento
  author_email: ''
  author_url: http://www.davidmataro.com/2012/07/como-moure-el-cataleg-de-productes-clients-i-comandes-de-magento/
  date: !binary |-
    MjAxMi0wNy0wOSAyMjozODo1NCArMDAwMA==
  date_gmt: !binary |-
    MjAxMi0wNy0wOSAyMDozODo1NCArMDAwMA==
  content: ! '[...] Per executar aquest procediment utilitzarem l&#8217;script mysqldump_bypattern.sh,
    el qual permet exportar les taules d&#8217;una base de dades mysql segon un patrÃ³.
    Veure Com fer un mysqldump de taules segons un patrÃ³. [...]'
---
<p>Si mai us heu trobat amb la necessitat de fer un mysqldump d'un conjunt de taules i no de tota la base de dades, l'script següent facilitat la feina.</p>
<p><code lang="bash" width="558"><br />
#!/bin/bash</p>
<p>if [ $# -lt 5 ]; then<br />
echo "Exports data from mysql database in tables matching a like pattern e.g. 'table_%'"<br />
echo "Usage: $0 dbname dbuser dbpass pattern outputfile"<br />
exit 1<br />
fi</p>
<p>DBNAME=$1<br />
DBUSER=$2<br />
DBPASS=$3<br />
PATTERN=$4<br />
OUTPUTFILE=$5</p>
<p>TABLES=( `mysql -u$DBUSER -p$DBPASS $DBNAME --silent -e "show tables like '$PATTERN'"` )</p>
<p>for TABLE in "${TABLES[@]}"; do<br />
mysqldump -u$DBUSER -p$DBPASS $DBNAME $TABLE &gt;&gt; $OUTPUTFILE<br />
done</p>
<p></code><br />
&nbsp;</p>
<p>L'script permet fer un mysqldump de les taules que responen a un patró en concret. Així dons, per fer un dump de totes les taules de la base de dades 'basededades' que comencen per 'sales' cal executar:</p>
<p><code lang="bash" width="558"><br />
./mysqldump_bypattern.sh basedades usuari password sales% fitxer_de_sortida.dump<br />
</code><br />
&nbsp;</p>
<p>L'script es pot descarregar <a title="mysqldump_bypattern.sh" href="https://gist.github.com/1016920#file_mysqldump_bypattern.sh" target="_blank">aquí</a>.</p>
