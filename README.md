# Casperjs 

Debian Jessie<br>
phantomjs 1.9.8<br>
casperjs 1.1.0-beta3<br>

## Usage ##
<pre>
docker run ricardobelo/docker-casperjs casperjs --version
docker run -v `pwd`/casperjs-files:/home/casperjs-files ricardobelo/docker-casperjs casperjs /home/casperjs-files/sample.js
</pre>

## Take a screenshot ##
<pre>
docker run -v `pwd`/casperjs-files:/home/casperjs-files ricardobelo/docker-casperjs casperjs test /home/casperjs-files/capture.js
</pre>

Please feel free to contribute or report any bugs.


---
install.sh
---

#!/bin/bash

# update/upgrade - install dependencies
apt-get update && apt-get upgrade -y
apt-get install build-essential chrpath wget libssl-dev libxft-dev unzip python git -y
apt-get install libfreetype6 libfreetype6-dev -y
apt-get install libfontconfig1 libfontconfig1-dev -y

# Install phantomjs
PHANTOMJS_VERSION=1.9.8
#echo https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-$PHANTOMJS_VERSION-linux-x86_64.tar.bz2 -P /home
wget "https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-$PHANTOMJS_VERSION-linux-x86_64.tar.bz2" -P /home
tar xvjf /home/phantomjs-$PHANTOMJS_VERSION-linux-x86_64.tar.bz2
mv phantomjs-$PHANTOMJS_VERSION-linux-x86_64 /usr/local/share/
ln -sf /usr/local/share/phantomjs-$PHANTOMJS_VERSION-linux-x86_64/bin/phantomjs /usr/local/share/phantomjs
ln -sf /usr/local/share/phantomjs-$PHANTOMJS_VERSION-linux-x86_64/bin/phantomjs /usr/local/bin/phantomjs
ln -sf /usr/local/share/phantomjs-$PHANTOMJS_VERSION-linux-x86_64/bin/phantomjs /usr/bin/phantomjs
chmod 777 /usr/local/share/phantomjs

# Install casperjs
cd /home/
git clone https://github.com/n1k0/casperjs.git
mv /home/casperjs /usr/local/share/casperjs-latest
ln -sf /usr/local/share/casperjs-latest/bin/casperjs /usr/local/share/casperjs
ln -sf /usr/local/share/casperjs-latest/bin/casperjs /usr/local/bin/casperjs
ln -sf /usr/local/share/casperjs-latest/bin/casperjs /usr/bin/casperjs
chmod 777 /usr/local/share/casperjs

---
