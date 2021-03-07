---
layout: post
status: publish
published: true
title: Imagen de cabecera aleatoria
author:
  display_name: Juanjo
  login: juanjo
  email: juanjo@jjcoellov.es
  url: http://www.jjcoellov.es
author_login: juanjo
author_email: juanjo@jjcoellov.es
author_url: http://www.jjcoellov.es
wordpress_id: 41
wordpress_url: http://jjcoellov.es/?p=41
date: '2009-01-10 22:43:59 +0000'
date_gmt: '2009-01-10 21:43:59 +0000'
categories:
- Coding
tags: []
---
<p>Como comenté en el <a href="http://jjcoellov.es/2009/01/10/algunos-cambios-en-la-apariencia-del-blog/">post anterior</a>, he añadido al blog un cambio que me agrada bastante: la de poder cargar una imagen aleatoria al entrar en la página. Bastante fácil todo, excepto por un detalle: como el theme que utilizo define la propiedad de la imagen en el CSS (background-image:url(ruta-imagen)), la generación de la alatoriedad no sabía cómo llevarla a cabo exactamente, hasta que descubrí que <a href="http://jquery.com/">jQuery</a> permite la modificación de atributos de las hojas de estilo (<a href="http://www.webintenta.com/cambiar-propiedades-css-con-jquery.html">enlace</a>). jQuery es una librería de funciones JavaScript que, básicamente, hace <em>mil virguerías</em>. Recomiendo pasarse por la página y echarle un vistazo. Pues bien, al final el código quedó tal que así: </p>
<p>En la cabecera, añadimos la librería:</p>
<pre lang="javascript">
<script src="http://www.jjcoellov.es/scripts/jquery.js" 
   type="text/javascript"></script>
</pre>
<p>Y luego en el cuerpo agregamos este código:</p>
<pre lang="javascript">
   <script type="text/javascript">
   /* Cambiar la imagen de la cabecera aleatoriamente */ 
   
  /* Calcular un valor aleatorio entre 0 y el tamaño del array 
   *  pasado por parametro */
   function randomPos(a) {
      return Math.floor((Math.random() * a.length) % a.length);
   }
   
   /* Array con las rutas de las imágenes a utilizar */
   var rutasImg = [ "/imagenes/cabecera1.jpg", 
                    "/imagenes/cabecera2.jpg",
                    "/imagenes/cabecera3.jpg",];

   /* Hacemos uso de jQuery para modificar (o asignar) el valor 
    *  del atributo "background-image" al elemento 
    *  con id "cabecera"  */
   $(document).ready(function() { 
      var imagen = "url(" + rutasImg[randomPos(rutasImg)] + ")";
      $("#cabecera").css("background-image", imagen);
   });
  
   </script> 
</pre>
<p>Y eso es todo. Podría ser mucho más sofisticado: obtener todas las imagenes de un directorio especificado (aunque necesitaría algún lenguaje del lado del servidor para llevarlo a cabo), o generalizarlo para que obtenga una imagen aleatoria en cualquier elemento, simplemente ubicando el código dentro del mismo. Tambiés puede resultar innecesario añadir jQuery para hacer esta nimiedad, pero como resulta bastante sencillo utilizarlo decidí incluirlo. Es muy probable que haya métodos alternativos haciendo uso de funciones nativas de javascript, pero como primera aproximación creo que es adecuado. Si alguien busca algo similar, espero que le sirva de ayuda. </p>
