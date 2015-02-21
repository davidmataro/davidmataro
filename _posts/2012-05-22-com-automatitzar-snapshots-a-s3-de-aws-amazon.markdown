---
layout: post
status: publish
published: true
title: Com automatitzar snapshots a S3 de AWS Amazon
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 339
wordpress_url: http://www.davidmataro.com/?p=339
date: !binary |-
  MjAxMi0wNS0yMiAwOTo1MjowMSArMDAwMA==
date_gmt: !binary |-
  MjAxMi0wNS0yMiAwNzo1MjowMSArMDAwMA==
tags:
- sysadmin
- backup
- s3
- aws
comments: []
---
<p>En el <a href="http://www.davidmataro.com/2012/04/aspectes-a-considerar-per-dissenyar-una-estrategia-de-backup/" title="Aspectes a considerar per a una estratègia de backup">post</a> anterior he descrit els aspectes a considerar per dissenyar una estratègia de backup que s'adapti a les nostres necessitats</p>
<p>Una de les tasques a realitzar es automatitzar la realització de les copies de seguretat. En el cas que estiguem utilitzant un servidor de AWS Amazon, una de les opcions que podem utilitzar per fer backup es fer Snapshots de discos EBS a S3. Tot i que EC2 disposa de les eines per fer el snapshot, aquest no proporciona cap eina per automaitzar i programar aquests.</p>
<p>L'script següent llegeix tots els volums d'un servidor i en fa un snapshot.</p>
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
<p>Per automatitzar-ho, cal executar l'script des del cron tal i com es mostra a continuació.</p>
<p><code lang="bash" width="558"><br />
0 4 * * * /usr/local/backup/bin/EBS-snapshot.sh i-006d6969 servidor<br />
</code></p>
<p>Abans d'executar l'script, cal instal·lar la API de EC2 i descarregar les claus de la nostra compte i així poder interactuar amb AWS Amazon des de la API EC2.</p>
