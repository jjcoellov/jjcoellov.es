---
layout: post
status: publish
published: true
title: 'Tips de Supervivencia: Atajos de teclado en Eclipse'
author:
  display_name: Juanjo
  login: juanjo
  email: juanjo@jjcoellov.es
  url: http://www.jjcoellov.es
author_login: juanjo
author_email: juanjo@jjcoellov.es
author_url: http://www.jjcoellov.es
wordpress_id: 75
wordpress_url: http://jjcoellov.es/?p=75
date: '2009-02-07 02:22:03 +0000'
date_gmt: '2009-02-07 01:22:03 +0000'
categories:
- Tips Supervivencia
- Coding
- Informática
tags: []
---
<p>Después del primer tip de supervivencia sobre la <a href="http://jjcoellov.es/2008/04/27/tip-de-supervivencia-autenticacion-automatica-en-ssh/">autenticación automática vía SSH</a> (que me permite ahorrar unos cuantos segundos al día) publico este otro sobre los atajos de teclado en <a href="http://www.eclipse.org">Eclipse</a>, para aprovechar una de las características más útiles del editor. </p>
<p>Todos los programas tienen <a href="http://en.wikipedia.org/wiki/Keyboard_shortcut">shortcuts</a> (atajos de teclado), y prácticamente todo el mundo utiliza alguno. Probablemente todo el que trabaje con algún entorno de programación hace uso de varios de ellos con total naturalidad, casi sin percatarse. Pero también me he dado cuenta de que hay muchos compañeros de clase que se conforman con muy pocos, casi todos básicos, bien porque no conocen los demás atajos, bien porque no consideran necesario realizar el esfuerzo de aprenderlos y utilizarlos (no solo en Eclipse, sino en otras herramientas: Vim, la Terminal, etc). Bien, yo creo que son <strong>indispensables</strong> si se desea programar con rapidez y soltura, o manejar las perspectivas/opciones/vistas de Eclipse con celeridad sin tener que hacer uso del ratón, que si bien es más cómodo, nos obliga a retirar las manos del teclado (nuestra <em>herramienta de codificación</em>), haciéndonos perder algunos segundos innecesariamente. </p>
<p>Yo no los aprendí todos de golpe; poco a poco los fui asimilando paulatinamente, conforme alguien me revelaba su existencia y su utilidad. Paso a detallar los shortcuts que utilizo diariamente:</p>
<p>Primero, los más básicos no sólo de Eclipse, sino de cualquier editor (de texto, imágenes, etc):</p>
<ul>
<li><strong>CTRL + X :</strong> Cortar la selección.</li>
<li><strong>CTRL + C :</strong> Copiar la selección.</li>
<li><strong>CTRL + V :</strong> Pegar la selección.</li>
<li><strong>CTRL + Z :</strong> Deshacer última acción.</li>
<li><strong>CTRL + Y :</strong> Rehacer última acción desecha.</li>
</ul>
<p>Estoy seguro que todos los usamos periódicamente. Es más cómodo también realizar la selección desde el teclado, haciendo uso de <strong>SHIFT + Flechas</strong>, ayudado de las teclas <strong>Inicio</strong>, <strong>Fin</strong>, <strong>RevPág</strong>, <strong>AvPág</strong>, y <strong>CTRL </strong>(Windows/Linux) o <strong>ALT </strong>(Mac).</p>
<p>Los siguientes son específicos de Eclipse, y son los que contienen la verdadera <em>chicha </em>del tema. Están organizados de mayor relevancia (bajo mi singular y subjetivo punto de vista) a menor:</p>
<ul>
<li><strong>CTRL + BARRA_ESPACIADORA :</strong> Autocompletado de  metodos/variables/etc.</li>
<li><strong>CTRL + SHIFT + R :</strong> Búsqueda de un recurso (código fuente, jar, xml, properties...) en los proyectos abiertos (sin tener que ir al explorador de paquete a buscarlo).</li>
<li><strong>CTRL + SHIFT + G :</strong> Buscar referencias al método/clase en el Workspace.  El único caso en que yo prefiero usar el botón derecho <strong>-> References -> Proyect</strong>, porque si hay muchos proyectos abiertos tarda más en hacer la búsqueda.</li>
<li><strong>CTRL + O :</strong> Ver métodos/atributos de la Clase.</li>
<li><strong>CTRL + D :</strong> Eliminar una línea.</li>
<li><strong>CTRL + M :</strong>  Maximizar/Minimizar la ventana activa.</li>
<li><strong>CTRL + I :</strong> Corregir indentacion.</li>
<li><strong>ALT + UP_ARROW / DOWN_ARROW :</strong> Subir/Bajar una línea. Respecto a éste, me costó muchísimo quitarme la <em>maña </em>de seleccionar las líneas que deseaba, cortarlas, moverme a donde quería, y pegarlas.</li>
<li><strong>CTRL + T :</strong> Arbol de Herencia (para ver las clases que implementan una interfaz, por ejemplo).</li>
<li><strong>CTRL + F :</strong> Búsqueda en el fichero actual.</li>
<li><strong>CTRL + H :</strong>  Buscar en todo el proyecto/workspace (dentro de ficheros java, jars, xmls, htmls, Spring beans...)</li>
<li><strong>CTRL + '/' (CTRL + SHIFT + 7):</strong> Añadir/quitar comentarios "//".</li>
<li><strong>CTRL + L :</strong> Ir a una línea específica.</li>
<li><strong>CTRL + SHIFT + L :</strong> Ver todos los atajos de teclado.</li>
<li><strong>ALT + SHIFT + C :</strong> Cambiar la firma del método actual (parámetros, nombre, tipo retornado, etc... los cambia en todas las clases que hagan uso del método).</li>
<li><strong>CTRL + AV_PAG / REV_PAG :</strong>  Siguiente/Anterior pestaña de las abiertas en la ventana activa.</li>
<li><strong>CTRL + E :</strong>  Ver las pestañas de código fuente para seleccionar una.
</li>
<li><strong>CTRL + '+' (del teclado numérico) :</strong> Expandir un bloque entre llaves (cuando solo se muestra la firma).</li>
<li><strong>CTRL + '-' (del teclado numérico) :</strong> Contraer un bloque (para mostrar sólo la firma).</li>
</ul>
<p>En modo Debug añadiría también:</p>
<ul>
<li><strong>F5 :</strong> Entrar en una llamada.</li>
<li><strong>F6 :</strong> Ir a la siguiente línea de código ("Step").</li>
<li><strong>F7 :</strong>  Ir a la sentencia de retorno del método.</li>
<li><strong>F8 :</strong> Continuar hasta el siguiente breakpoint.</li>
<li><strong>CTRL + Q (sobre un elemento) :</strong> Inspeccionar estructura y valores del elemento (p.e. una variable).</li>
</ul>
<p>Hay otros dos atajos que debería usar, pero no lo hago. El primero, porque utilizo CTRL + F, y el segundo, porque sigo usando el ratón (aunque ya me he comprometido conmigo mismo a cambiar esto :P)</p>
<ul>
<li><strong>CTRL + J :</strong>  Búsqueda incremental (como Firefox).</li>
<li><strong>CTRL + 1 :</strong> Arreglo rápido. Es equivalente a pulsar sobre la "x" que sale al lado de la línea que contiene errores en el código fuente, sugiriendo soluciones.</li>
</ul>
<p>Para finalizar, dos apuntes más:</p>
<p>- Todos estos atajos son <strong>configurables</strong>; pueden ser adaptados a nuestras preferencias personales. En <strong>Windows->Preferences->General->Keys </strong>está la lista de todos los ellos y su configuración asociada<br />
.<br />
- Existe un Plugin para Eclipse llamado <a href="www.mousefeed.com">MouseFeed </a>que te muestra el shortcut asociado a una acción que se lleve a cabo con el ratón, de tal forma que así podemos aprender nuevas funcionalidades en el teclado para irnos desprendiendo de <em>Mickey</em>.</p>
<p>¿Usas algún atajo más? Compartelo con todos en un comentario ;)</p>
<p><strong>Bonus Tip:</strong> escribir "<strong>syso</strong>" y luego hacer uso del shortcut de autocompletado (CTRL + Barra Espaciadora) nos da como resultado "System.out.println("");. Ahi lo dejo, aunque como <em>todos somos buenos programadores</em>, los mensajes los imprimimos usando loggers, y la consulta de valores de variables lo hacemos mediante el debugger, <em>¿no?</em> :P:P </p>
