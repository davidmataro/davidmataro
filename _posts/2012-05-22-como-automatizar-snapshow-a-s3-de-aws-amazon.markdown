---
layout: post
status: publish
published: true
title: Como automatizar snapshow a S3 de AWS Amazon
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 348
wordpress_url: http://www.davidmataro.com/?p=348
date: !binary |-
  MjAxMi0wNS0yMiAwOTo1MjoxMiArMDAwMA==
date_gmt: !binary |-
  MjAxMi0wNS0yMiAwNzo1MjoxMiArMDAwMA==
tags:
- backup
- s3
- aws
- snapshot
comments: []
---
<p>En el post anterior se han descrito los aspectos a considerar para diseñar una estrategia de backup que se adapte a nuestras necesidades</p>
<p>Una de las tareas a realizar es automatizar la realización de las copias de seguridad. En el caso que estemos utilizando un servidor de AWS Amazon, una de las opciones que podemos utilizar para hacer backup es hacer Snapshots de discos EBS a S3. Aunque EC2 dispone de las herramientas para hacer el snapshot, éste no proporciona ninguna herramienta para automaitzar y programar estos.</p>
<p>El script siguiente lee todos los volúmenes de un servidor y hace un snapshot.</p>
<p><code lang="bash" width="558"><br />
#!/bin/bash</p>
<p>if [ ! $# == 2 ]; then<br />
/bin/echo "USAGE: EBS-snapshot.sh "<br />
exit<br />
fi</p>
<p># Quantity of snapshot on S3<br />
QUANTITY=1</p>
<p>export JAVA_HOME=/usr/java/jre1.6.0_27<br />
export EC2_HOME='/usr/local/ec2' # Make sure you use the API tools, not the AMI tools<br />
export EC2_BIN=$EC2_HOME/bin<br />
export PATH=$PATH:$EC2_BIN<br />
export PATH=$PATH:$EC2_BIN<br />
export EC2_URL=https://ec2.eu-west-1.amazonaws.com</p>
<p># I know all of the above is good to have solution, but not re-usable<br />
# I have captured all of the above in a particular file and lemme execute it<br />
source /etc/environment</p>
<p>EC2_BIN=$EC2_HOME/bin</p>
<p># store the certificates and private key to your amazon account<br />
MY_KEY='/usr/local/ec2/pk-4BDXGQGWBNNTKC7LSTDN7J77YYK257GZ.pem'<br />
MY_CERT='/usr/local/ec2/cert-4BDXGQGWBNNTKC7LSTDN7J77YYK257GZ.pem'<br />
# fetching the instance-id from the metadata repository<br />
MY_INSTANCE_ID=$1<br />
INSTANCE_NAME=$2</p>
<p># temporary file<br />
TMP_FILE='/tmp/rock-ebs-info.txt'<br />
# get list of locally attached volumes via EC2 API:<br />
$EC2_BIN/ec2-describe-volumes -C $MY_CERT -K $MY_KEY &gt; $TMP_FILE<br />
VOLUME_LIST=$(/bin/cat $TMP_FILE | /bin/grep ${MY_INSTANCE_ID} | /bin/awk '{ print $2 }')</p>
<p>sync</p>
<p>#create the snapshots<br />
/bin/logger -t EBS-SNAP-$MY_INSTANCE_ID "Create EBS Volume Snapshot $MY_INSTANCE_ID $INSTANCE_NAME - Process started."<br />
/bin/logger -t EBS-SNAP-$MY_INSTANCE_ID $VOLUME_LIST</p>
<p>for volume in $(echo $VOLUME_LIST); do<br />
DESC="Backup $INSTANCE_NAME ($MY_INSTANCE_ID) $volume"<br />
/bin/logger -t EBS-SNAP-$MY_INSTANCE_ID "Creating Snapshot for the volume: $volume with description: $DESC"<br />
/bin/logger -t EBS-SNAP-$MY_INSTANCE_ID "Snapshot info below:"<br />
$EC2_BIN/ec2-create-snapshot -C $MY_CERT -K $MY_KEY -d "$DESC" $volume<br />
done</p>
<p>/bin/logger -t EBS-SNAP-$MY_INSTANCE_ID "Process ended at $(date +%m-%d-%Y-%T)"</p>
<p>rm -f $TMP_FILE<br />
</code></p>
<p>Para automatizarlo, hay que ejecutar el script desde el cron tal y como se muestra a continuación.</p>
<p><code lang="bash" width="558"><br />
0 4 * * * /usr/local/backup/bin/EBS-snapshot.sh i-006d6969 servidor<br />
</code></p>
<p>Antes de ejecutar el script, hay que instalar la API de EC2 y descargar las claves de nuestra cuenta y así poder interactuar con AWS Amazon desde la API EC2.</p>
