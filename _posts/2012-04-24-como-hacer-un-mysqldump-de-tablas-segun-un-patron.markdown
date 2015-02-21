---
layout: post
status: publish
published: true
title: Como hacer un mysqldump de tablas según un patron
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 337
wordpress_url: http://www.davidmataro.com/?p=337
date: !binary |-
  MjAxMi0wNC0yNCAxMjo0Mjo1MCArMDAwMA==
date_gmt: !binary |-
  MjAxMi0wNC0yNCAxMDo0Mjo1MCArMDAwMA==
tags:
- sysadmin
- mysql
comments: []
---
<p>Si nunca te has encontrado con la necesidad de hacer un mysqldump de un conjunto de tablas y no de toda la base de datos, el script siguiente facilita el trabajo:</p>
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
<p>El script permite hacer un mysqldump de las tablas que responden a un patron en concreto. Por ejemplo, para hacer un mysqldump de todas la tablas de la base de dades 'basedatos' que empiezan por 'sales' hay que ejecutar:</p>
<p><code lang="bash" width="558"><br />
./mysqldump_bypattern.sh basedatos usuario password sales% fichero_de_salida.dump<br />
</code><br />
&nbsp;</p>
<p>El script se puede descargar <a title="mysqldump_bypattern.sh" href="https://gist.github.com/1016920#file_mysqldump_bypattern.sh" target="_blank">aquí</a>.</p>
