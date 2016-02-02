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
