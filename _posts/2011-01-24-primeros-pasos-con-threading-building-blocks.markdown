---
layout: post
status: publish
published: true
title: Primeros pasos con Threading Building Blocks
author:
  display_name: Juanjo
  login: juanjo
  email: juanjo@jjcoellov.es
  url: http://www.jjcoellov.es
author_login: juanjo
author_email: juanjo@jjcoellov.es
author_url: http://www.jjcoellov.es
wordpress_id: 214
wordpress_url: http://jjcoellov.es/?p=214
date: '2011-01-24 19:33:53 +0000'
date_gmt: '2011-01-24 18:33:53 +0000'
categories:
- Tecnología
- Coding
- Informática
tags: []
---
<p>Hace poco, como tema de una presentación en la Facultad, <a href="http://twitter.com/jmbarroso">@jmbarroso</a> y yo estuvimos “jugando” con una librería de paralelización de Intel de la que no tenía ni idea de su existencia y que me dejó francamente sorprendido. Se llama <strong>Threading Building Blocks</strong> (TBB), lleva algunos años en el mercado y en este post explicaré someramente qué es, para qué sirve, y qué viene a mejorar en el mundo de la paralelización.</p>
<p><strong>TBB - Qué es</strong></p>
<p>TBB es una librería escrita en C++, para programas hechos en este lenguaje (por ahora), que facilita la paralelización de los mismos en procesadores multicore gracias a las funciones y estructuras que provee. Su objetivo es lograr un paralelismo escalable, haciendo uso de C++ estándar, que además abstraiga al programador de los detalles de la plataforma y del manejo de hilos, que exprese el paralelismo de una manera más simple y que realice un mejor aprovechamiento de los recursos de los procesadores.</p>
<p><strong>TBB - Ventajas</strong></p>
<p>TBB permite expresar el paralelismo como <em>Tareas</em> en lugar de <em>Hilos</em>. De esta forma, no es necesaria llevar a cabo manualmente la gestión de los mismos: no más create, join, manage, etc. Dichas tareas son asignadas automáticamente a hilos, haciendo un uso eficiente de los recursos del procesador.</p>
<p>Una característica curiosa es el uso de una técnica denominada <em>task stealing</em>; la librería se encarga de asignar/desasignar tareas entre procesadores de manera transparente al programador, según la carga de trabajo actual, para equilibrar el trabajo de todos. Toda esta “abstracción” permite desarrollar soluciones más simples de alto nivel.</p>
<p>Además, es compatible con otros paquetes de paralelización, por lo que se puede optar por usar algunos componentes de TBB bajo ciertas circunstancias, y usar diferentes soluciones (<strong>OpenMP</strong>, gestión de hilos manualmente) en otras.</p>
<p><strong>TBB - Contenido</strong></p>
<p>La librería provee soluciones de distinta índole para facilitar la paralelización de las aplicaciones, que se pueden dividir en:</p>
<p><strong>Algoritmos básicos:</strong><br />
• parallel_for<br />
• parallel_reduce<br />
• parallel_scan</p>
<p><strong>Algoritmos avanzados:</strong><br />
• parallel_while<br />
• parallel_do<br />
• pipeline<br />
• parallel_sort</p>
<p><strong>Contenedores:</strong><br />
• concurrent_queue<br />
• concurrent_vector<br />
• concurrent_hash_map</p>
<p><strong>Reserva de memoria escalable:</strong><br />
• scalable_malloc<br />
• scalable_free<br />
• scalable_realloc<br />
• scalable_calloc</p>
<p><strong>Exclusión mutua:</strong><br />
• mutex<br />
• spin_mutex<br />
• queuing_mutex<br />
• spin_rw_mutex<br />
• queuing_rw_mutex<br />
• recursive mutex</p>
<p><strong>Operaciones atómicas</strong><br />
• fetch_and_add<br />
• fetch_and_increment<br />
• fetch_and_decrement<br />
• compare_and_swap<br />
• fetch_and_store</p>
<p><strong>Timing:</strong><br />
• Método thread_save portable para procesar el tiempo transcurrido.</p>
<p><strong>Planificador de tareas</strong><br />
• Acceso directo para controlar la creación y la ejecución de tareas</p>
<p><strong>Instalando TBB.</strong></p>
<p>La última versión estable de la librería para Windows, Linux y Mac se puede encontrar <a href="http://www.threadingbuildingblocks.org/download.php">aquí</a>.</p>
<p>La instalación resulta bastante sencilla. En mi caso con la versión para Mac OS, que no diferirá mucho de la disponible para Linux:</p>
<p>Se descomprime el tgz descargado. Yo lo hice en un directorio de mi home donde instalo los frameworks y librerías que utilizo (grails, maven, gradle, mercurial, etc) pero /opt/ podría ser otra ubicación adecuada. También he creado un enlace simbólico “tbb” que apunte a la última versión, para usarlo al referirme a la librería, en vistas a simplemente actualizar el enlace en caso de que siga descargando en el futuro versiones de la librería y quiera cambiar fácilmente entre ellas:</p>
<pre lang="text">
juanjo:bin juanjo$ pwd
/Users/juanjo/bin
juanjo:bin juanjo$ ls -ltr
drwxr-xr-x   4 juanjo  juanjo       136 24 ene 17:21 tbb30_20101215oss
juanjo:bin juanjo$ ln -s tbb30_20101215oss/ tbb
juanjo:bin juanjo$ ls -ltr
drwxr-xr-x   4 juanjo  juanjo       136 24 ene 17:21 tbb30_20101215oss
lrwxr-xr-x   1 juanjo  juanjo        22 24 ene 17:28 tbb -> tbb30_20101215oss/
</pre>
<p>Es necesario modificar el archivo bin/tbbvars.sh para asignar a la variable <strong>TBB30_INSTALL_DIR</strong> la ruta al directorio raíz de la librería:</p>
<pre lang="text">
juanjo:tbb juanjo$ pwd
juanjo:bin juanjo$/Users/juanjo/bin/tbb
juanjo:bin juanjo$ cat -n bin/tbbvars.sh

# Threading Building Blocks Home
    30    TBB30_INSTALL_DIR=/Users/juanjo/bin/tbb
</pre>
<p>Cargamos las variables definidas en el fichero, que se deberá hacer cada vez que se abra una terminal y se desee trabajar con la librería. La alternativa es añadir la línea al fichero ~/.bash_profile para hacerlo automáticamente al cargar sesión:</p>
<pre lang="text">
juanjo:bin juanjo$ source bin/tbbvars.sh
</pre>
<p>Para probar si todo está configurado correctamente, intentamos compilar y ejecutar uno de los ejemplos incluídos en la distribución:</p>
<pre lang="text">
juanjo:tbb juanjo$ cd examples/GettingStarted/sub_string_finder/
juanjo:sub_string_finder juanjo$ make
g++ -O2 -DNDEBUG  -o sub_string_finder sub_string_finder.cpp -ltbb
g++ -O2 -DNDEBUG  -o sub_string_finder_extended sub_string_finder_extended.cpp -ltbb
g++ -O2 -DNDEBUG  -o sub_string_finder_pretty sub_string_finder_pretty.cpp -ltbb
./sub_string_finder_extended
Done building string.
Done with serial version.
Done with parallel version.
Done validating results.
Serial version ran in 8.01188 seconds
Parallel version ran in 4.1834 seconds
Resulting in a speedup of 1.91516
</pre>
<p>En efecto, todo funciona, y ya estamos en disposición de empezar a utilizar los componentes que nos provee TBB. De hecho, en el ejemplo que lanzamos se observa una de las bondades: un <a href="http://en.wikipedia.org/wiki/Speedup">speedup</a> del 91% que no está nada mal.</p>
<p>En el próximo artículo veremos cómo hacer uso de los componentes incluídos en la librerías, paralelizando un código secuencial y desgranando el código fuente del mismo. </p>
<p>Más información:</p>
<p>• Página Oficial de <a href="http://www.threadingbuildingblocks.org/">Threading Building Blocks</a>.</p>
