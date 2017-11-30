---
layout: post
title: Ruby Challenge
---

<a href="https://es.wikipedia.org/wiki/Ruby"><img src="https://upload.wikimedia.org/wikipedia/commons/7/73/Ruby_logo.svg" align="top" height="100" ></a>

Este año 2015 ha sido mi año para Ruby. Después de empaparme de recursos online (como los que puse en el anterior post) para aprender este lenguaje, decidí aventurarme en algo mas emocionante.

Encontré, a principios de año, un challenge de programación de IAs en Ruby organizado por la escuela/bootcamp Ironhack para desarrolladores.

<a href="https://www.ironhack.com/en"><img src="https://pbs.twimg.com/profile_images/466256995675160576/4L9u4Au_.png" align="top" height="100" ></a>


La idea era hacer una liga que durara varios meses, donde pudiéramos enfrentar nuestro código e ir viendo los resultados para hacer mejoras cada quince días.

Hemos estado usando la librería [RTanque](https://github.com/awilliams/RTanque). Librería que ya se había usado en otras ocasiones para competiciones en alguna universidad.

<a href=""><img src="https://awilliams.github.io/images/rtanque.png" align="top" height="150" ></a>

La evolución de mi código fue muy emocionante, y las batallas también. Pasé de tener un tanque que chocaba contra las paredes girando 90º, con un porcentaje de acierto del 0%, a implementar unas aproximaciones de Newton para anticipar la posición del enemigo y, maximizar los aciertos en los disparos. También implementé un patrón de movimiento por una matriz de puntos de diferentes densidades, con un movimiento base de tipo sinusoidal y giros bruscos aleatorios.



Inicialmente era de los últimos, y parecía no tener oportunidad contra los 18 competidores. Pero poco a poco fui subiendo hasta ser seleccionado entre los 5 mejores para hacer la final (nos enfrentaban por parejas y se ejecutaban 100 batallas de cada una). Al final quede el primero de los cinco en número de batallas ganadas.
Mi criatura se llama Cugel :)

[[![LIGA_IRONHACK_RTANQUE_5_PRIMEROS_suma.jpg](https://s11.postimg.org/g7i3znomr/LIGA_IRONHACK_RTANQUE_5_PRIMEROS_suma.jpg)](https://postimg.org/image/qubx52wrz/)

T01 el que mas caña me daba ganándome 48 de 50, lo que personalmente considero un empate.

Otra cosa interesante es que casi sin darme cuenta y poco a poco me desarrollé mi script en bash que ejecutaba multibatallas por miles entre todos los tanques que tenía disponibles para pruebas, y me resultaba unas estadísticas muy interesantes. Creo que casi disfruté más este apartado que la programación de la IA en si misma.

El plan maestro era que este script fuera guardando las estadísticas resultantes en un archivo, y que el código de la IA en Ruby leyera dinámicamente de ese archivo de estadísticas para optimizarse a si mismo (movimiento sobre todo). Esto último no lo conseguí del todo, ya vino la final y no me daba tiempo, y lo que pude codificar me iba a tardar años funcionando para obtener, quizás, alguna mejora. Cosas que pasan cuando no planificas los tiempos de ejecución en tu plan maestro :P

Aquí dejo el [enlace](https://github.com/RadW2020/RTanque) a un repositorio de GitHub donde guardo el directorio con el trabajaba el pequeño proyecto.

Como nota final he de decir que participar en este tipo de eventos es muy recomendable para aprender un lenguaje y es muy entretenido.
También agradecer al equipo de Ironhack que gestionó el evento de manera desinteresada y muy eficientemente.

Saludos.
