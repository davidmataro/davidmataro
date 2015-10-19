---
layout: post
status: publish
published: true
title: How to mount Amazon S3 bucket with s3fs
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 540
wordpress_url: http://www.davidmataro.com/?p=540
date: !binary |-
  MjAxMy0wNC0xMCAwMDoyMToxMCArMDAwMA==
date_gmt: !binary |-
  MjAxMy0wNC0wOSAyMjoyMToxMCArMDAwMA==
tags:
- s3
- aws
- s3fs
comments: []
---
<p><a title="S3fs" href="https://code.google.com/p/s3fs/" target="_blank">S3fs</a> is a fuse based file system backed by <a title="Amazon S3" href="http://aws.amazon.com/s3/" target="_blank">Amazon S3</a>. This permit mount a S3 bucked as a file system ans store files and folders transparently.</p>
<p>I have installed s3fs in a t1.micro ec2 instance with ubuntu 12.04.1 TLS x64. To install <a title="S3fs" href="https://code.google.com/p/s3fs/" target="_blank">s3fs</a> I have followed the next steps.</p>
<p>1. Create a bucket named mybucked.</p>
<p>2. Create IAM user and add permissions.</p>
<p>3. Install <a title="S3fs" href="https://code.google.com/p/s3fs/" target="_blank">s3fs</a></p>
<p>&nbsp;</p>
<p>cd /tmp/<br />
apt-get install build-essential libfuse-dev fuse-utils libcurl4-openssl-dev libxml2-dev mime-support</p>
<p>wget https://s3fs.googlecode.com/files/s3fs-1.66.tar.gz<br />
tar xvzf s3fs-1.65.tar.gz<br />
cd s3fs-1.65/<br />
./configure<br />
make<br />
make install</p>
<p>4. Configure credentials</p>
<p>Create a file /etc/passwd-s3fs add the credentials like the next line:</p>
<p>&lt;Access key id&gt;:&lt;secret access key&gt;</p>
<p>Change perms of /etc/passwd-s3fs</p>
<p><code><br />
chmod 600 /etc/passwd-s3fs<br />
</code></p>
<p>5. Create a mount point</p>
<p><code><br />
mkdir /mnt/s3<br />
chmod 777 /mnt/s3<br />
</code></p>
<p>without 777 permissions only root can write to bucket.</p>
<p>6. Mount manually</p>
<p><code lang="bash"><br />
s3fs mybucket /mnt/s3 -o noatime -o allow_other -o uid=1000 -o gid=1000 -o use_cache=/tmp -o default_acl=public-read-write<br />
</code></p>
<p>7. Configure to mount in boot time.</p>
<p>The documentation says that to mount s3 bucket in boot time, you need add to /etc/fstab the next line:</p>
<p><code lang="bash"><br />
s3fs#enterwinetest /mnt/s3 fuse defaults,noatime,allow_other,uid=1000,gid=1000,use_cache=/tmp,default_acl=public-read-write 0 0<br />
</code></p>
<p>but, in my case. When I reboot the instance, it not start.</p>
<p>To automount I have added the next line to /etc/rc.local</p>
<p><code lang="bash"><br />
/usr/local/bin/s3fs enterwine /mnt/s3 -o noatime -o allow_other -o uid=1000 -o gid=1000 -o use_cache=/tmp -o default_acl=public-read-write<br />
</code></p>
