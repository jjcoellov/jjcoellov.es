---
layout: post
status: publish
published: true
title: 'Tip de Supervivencia: Autenticación Automática en SSH'
author:
  display_name: Juanjo
  login: juanjo
  email: juanjo@jjcoellov.es
  url: http://www.jjcoellov.es
author_login: juanjo
author_email: juanjo@jjcoellov.es
author_url: http://www.jjcoellov.es
wordpress_id: 29
wordpress_url: http://jjcoellov.es/?p=29
date: '2008-04-27 00:06:49 +0100'
date_gmt: '2008-04-26 23:06:49 +0100'
categories:
- Tips Supervivencia
tags:
- Tips
- SSH
- Autenticacion
- How-to
---
<p>En una continua búsqueda de hacer las rutinas diarias delante del pc lo más cortas posible, he seguido estos pasos para autentificarme automáticamente en servidores remotos. En mi caso, necesito conectarme diariamente a mi cuenta en la Facultad mediante el protocolo seguro <a title="Secure Shell" href="http://es.wikipedia.org/wiki/SSH">SSH</a>. Básicamente, la cosa sería algo así como:<br id="qfnv" /></p>
<pre lang="text">
ssh usuario@hostremoto
RSA key fingerprint is d6:i0:ah:e1:8a:65:c3:3c:d2:35:ed:66:58:75:8e:8g.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'hostremoto,IP' (RSA) to the list of known hosts.
usuario@hostremoto's password:
prompt-usuario>
</pre>
<p>Primero pedimos el acceso a un servidor remoto vía ssh. Éste nos devuelve un secuencia de bytes que sirve como comprobación de la clave pública del RSA (conocida como <a title="Public key fingerprint" href="http://en.wikipedia.org/wiki/Public_key_fingerprint">key fingerprint</a>), nos advierte que el host remoto será añadido como servidor conocido (se concatenará una línea en el archivo <em>.ssh/known_hosts</em> con el servidor, el protocolo de encriptación y la clave privada de acceso al mismo), y nos pide la clave de acceso. Puede que realizar esta acción no sea demasiado difícil ni larga...si se hace una única vez. Pero muchas veces es necesario autenticarse varias veces (inluso en la misma facultad se cuenta con varios servidores con servicios asociados distintos, y es necesario saltar de uno a otro, vía ssh, realizando el proceso de nuevo), y la tarea, de tan repetitiva, termina siendo tediosa. Peor aún, si se mantiene un repositorio tipo SVN en un servidor remoto, y es necesario el acceso vía SSH al mismo, cada commit/update de los cambios necesita realizar el proceso de autenticación de nuevo. Así que es necesario encontrar una solución que lo automatice. Y es aquí donde entra en juego algunos comandos muchas veces desconocidos para el común de los mortales, que nos simplifican la tarea. La cosa sería más o menos así:<br id="f61j" /> <br id="cx9v" /> SSH incluye la posilibidad de autenticar usuarios mediante el uso de claves públicas (es necesario conocer un poco de la encriptación por clave pública para entender ésto). En lugar de autenticar al usuario con la clave, el servidor SSH en la máquina remota verifica un mensaje firmado con la clave privada del usuario con la copia de la clave pública. El primer paso sería conseguir, por tanto, una clave pública. Para ello se puede utilizar el comando ssh-gen:<br id="qfnv" /></p>
<pre lang="text">$ ssh-keygen -t rsa -N '</pre>
<p>La opción -t selecciona el tipo de clave que se desea generar (en este caso, rsa). Los otros tipos son rsa1, y <a title="dsa" href="http://es.wikipedia.org/wiki/DSA">dsa</a>. La opción -N indica la opción de una <a title="passphrase" href="http://en.wikipedia.org/wiki/Passphrase">passphrase</a> (frase clave). En principio, nosotros indicaremos mediante el doble comillado simple '' que no deseamos utilizar una passphrase. Por defecto, la identificación será guardada en un fichero en <em>/home/usuario/.ssh/id_rsa</em>. La clave pública se almacenará en <em>/home/usuario/.ssh/id_rsa.pub</em>.<br />
<br/>Una vez que se ha generado el par de claves, es necesario copiar la clave pública en la máquina remota. Para esto, es necesario concatenarla al archivo<em> .ssh/authorized_keys</em> en el host remoto:<br id="qfnv" /></p>
<pre lang="text">$ ssh-copy-id -i ~/.ssh/id_rsa.pub usuario@hostremoto</pre>
<p>También puede hacerse como alternativa:<br id="qfnv" /></p>
<pre lang="text">
$ ssh remote.machine "umask 077; cat >> .ssh/authorized_keys" < /home/user/.ssh/id_rsa.pub</pre>
<p>El comando "umask" es necesario, ya que el servidor se negará a leer el archivo <em>/home/user/.ssh/authorized_keys</em> si ha perdido permisos.<br id="d-nt" /> <br id="uacv" /> Ahora se puede editar el arhivo /home/.ssh/config y añadir un par de líneas:<br id="qfnv" /></p>
<pre lang="text">
Host aliasHostremoto
Hostname hostremoto
user usuario_en_host_remoto 
</pre>
<p>La linea Host permite utilizar un alias para el nombre del servidor (para hacerlo incluso más corto). La línea Hostname es el nombre completo del servidor, y la línea user, es obviamente, el login. Como ejemplo:<br id="qfnv" /></p>
<pre lang="text">
Host etsii
Hostname hostremoto.etsii.ull.es
user mi_usuario
</pre>
<p>Por tanto, para conectarme a mi cuenta de la facultad únicamente necesito hacer: <br id="qfnv" /></p>
<pre lang="text">
$ ssh etsii
Last login: Wed Apr 23 13:34:00 2008 from mi.maquina
</pre>
<p>Y ya está. Es recomendable echarle un vistazo a todos los comandos utilizados, y conocer las opciones no comentadas que puedan ser útiles en otras situaciones similares. </p>
<div><strong><em>Fuentes:</em></strong><br />
<a title="SSH Authentication" href="http://search.cpan.org/%7Ecasiano/GRID-Machine/lib/GRID/Machine.pod#INSTALLATION">SSH Authentication</a>.<br />
<a title="SSH Boucing" href="http://www.hackinglinuxexposed.com/articles/20040830.html">SSH Bouncing - How to get through firewalls easily.</a> (para hacer cosas más sofisticadas).</div>
