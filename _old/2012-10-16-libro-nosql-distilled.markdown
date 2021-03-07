---
layout: post
status: publish
published: true
title: 'Libro: NoSQL Distilled'
author:
  display_name: Juanjo
  login: juanjo
  email: juanjo@jjcoellov.es
  url: http://www.jjcoellov.es
author_login: juanjo
author_email: juanjo@jjcoellov.es
author_url: http://www.jjcoellov.es
wordpress_id: 261
wordpress_url: http://jjcoellov.es/?p=261
date: '2012-10-16 00:14:46 +0100'
date_gmt: '2012-10-15 22:14:46 +0100'
categories:
- Tecnología
- Coding
- Informática
- Libros
tags:
- nosql
- martin fowler
- bbdd
- mongodb
- redis
- hadoop
- cap theorem
---
<p>Hace poco he terminado de leer el libro <a href="http://www.amazon.com/gp/product/0321826620" title="NoSQL Distilled" target="_blank">NoSql Distilled</a> [<strong>M. Fowler</strong> & <strong>P. Sadalange</strong>]. Es una introducción bastante concisa (unas 150 páginas) sobre NoSQL: Qué es, qué viene a cubrir en contraposición a las bases de datos relacionales de toda la vida, por qué surgieron, cuáles son los tipos de bases de datos NoSQL más famosos y algunos consejos sobre cuándo utilizar unos u otros. </p>
<p>No entra en mucho detalle en ninguno de los apartados que menciona, pero lo que cubren basta para aportar una idea general sobre NoSQL, qué hay bajo el paraguas de esta (por otra parte bastante laxa) definición, y las opciones que se tienen a la hora de elegir cuál es la mejor opción en la capa de persistencia de nuestra aplicación. </p>
<p>Los primeros capítulos explican el motivo por el que el término NoSQL está en alza, así como los modelos de datos que se usan en este tipo de bases de datos (Aggregate Data Model). También explica cómo conseguir modelos distribuidos, bien a través del particionado (sharding) o la replicación, siendo ambas técnicas no excluyentes entre sí. </p>
<p>En el capítulo de Consistencia, se explican los distintos conflictos que se pueden obtener, así como el <a href="http://en.wikipedia.org/wiki/CAP_theorem" title="CAP Theorem" target="_blank">teorema del CAP</a> (Consistency - Availability - Partition tolerance) y por qué (en principio) no se pueden conseguir las tres propiedades en un sistema distribuido. Otro apartado que podría tratarse como Consistencia es el de los Version Stamps, que ayudan a detectar conflictos de concurrencia entre versiones del mismo dato. La técnica de Map-Reduce (en la que se basa p.e. <a href="http://hadoop.apache.org/" title="Hadoop" target="_blank">Hadoop</a>) también es explicada más o menos en detalle. </p>
<p>Hay un capítulo para cada uno de los tipos "principales" de bases de datos NoSQL: los de almacenamiento Key-Value (p.e. <a href="http://redis.io/" title="Redis" target="_blank">Redis</a>), Documents (p.e. <a href="http://www.mongodb.org/" title="MongoDB" target="_blank">MongoDB</a>), Graph Databases (p.e. <a href="http://neo4j.org/" title="Neo4J" target="_blank">Neo4j</a>) o Column-Oriented (p.e. <a href="http://cassandra.apache.org/" target="_blank">Cassandra</a>), así como sus puntos fuertes/débiles, y bajo qué dominios de aplicación se deberían usar unos u otros. </p>
<p>Los últimos capítulos versan sobre la persitencia políglota (Polyglot Persistence) o como usar la tecnología que mejor se adapte al dominio del problema, sin necesidad de utilizar siempre el mismo sistema (p.e. información de sesiones en key-value, datos de negocio en una base de datos relacional y el sistema de recomendaciones en una base de datos de grafos)</p>
<p>Por último, comenta que los dos principales motivos para utilizar NoSQL son para mejorar la productividad de los desarrolladores a través del uso de bases de datos que se adaptan mejor al dominio de la aplicación, o para mejorar el rendimiento de acceso a los datos. Sin embargo, aconsejan llevar a cabo una etapa de pruebas antes de decidirse finalmente por una solución NoSQL.</p>
<p>En la web de M. Fowler se puede encontrar una sección completa con la documentación que recabaron para escribir el libro: <a href="http://martinfowler.com/nosql.html" title="NoSQL" target="_blank">NoSQL</a>. En particular, se pueden encontrar los puntos claves de muchos de los capítulos del libro, que sirven como un buen resumen general del mismo: <a href="http://martinfowler.com/articles/nosqlKeyPoints.html" title="Key Points from NoSQL Distilled" target="_blank">Key Points from NoSQL Distilled</a> </p>
<p>Personalmente el libro me ha gustado. Es fácil de leer, y aporta una visión general del ecosistema de bases de datos NoSQL, las características de cada uno de ellos, así como los motivos por los cuáles se podría elegir alguna solución u otra (o combinar varias). Sirve también como punto de partida para abordar libros más específicos sobre cada una de las tecnologías que relata.</p>
