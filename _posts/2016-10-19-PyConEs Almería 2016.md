---
layout: post
title: PyconEs Almería 2016
---

Hace poco estuve en la conferencia nacional sobre Python, que este año se organizó en Almería.

![](https://pbs.twimg.com/profile_images/743356612086116355/6X4srwCV.jpg)

Todo un lujo tenerlos aquí y un auténtico festival para los amantes de Python y de la programación en general.



En la del evento podemos ver el calendario de talleres y conferencias, repleto de eventos a todas horas.
Por mi parte la única crítica que puedo hacer es cuando quería ver dos que ocurrían a la vez, ¡una pena!

http://2016.es.pycon.org/es/schedule/

Este calendario es interesante porque se puede encontrar el material de muchos de los participantes, ya sea presentaciones en pdf, videos, o enlaces a github.


Evidentemente no pude ir a todas. Pero si puedo algunas cosas que me llamaron la atención de lo que vi.

Comentaré alguna cosa de las que mas me llamaron la atención:

![](https://raw.githubusercontent.com/AeroPython/Taller-Algoritmos-Geneticos-PyConEs16/master/static/aeropython_name_mini.png)

Primero, mi preferida, por como estaba organizada y por la calidad de los ponentes: El taller **"Simplifica tu vida con sistemas complejos (y algoritmos genéticos)"**.

Los ejemplos que pusieron estaban orientados a la optimización de diseños industriales aeronáuticos, y esto, lejos hacerse pesado, lo hacía todo mucho mas fácil de entender. Es la explicación mas clara de estos temas que he visto/leido en mi vida.
Merece la pena echarle un vistazo a los materiales de trabajo que usaron:
(ojo, para este y otros talleres lo mejor es usar el [Jupyter notebook](http://jupyter.org/))

- introducción a los paquetes de Python Científico está en https://github.com/AeroPython/Taller-Aeropython-PyConEs16

- Algoritmos Genéticos y Sistemas complejos está en https://github.com/AeroPython/Taller-Algoritmos-Geneticos-PyConEs16

- Introducción a los Algoritmos genéticos está en http://2016.es.pycon.org/media/keynotes/Introducci%C3%B3n_a_los_algoritmos_gen%C3%A9ticos.pdf


Usaron un notebook con todo el código preparado en modo servidor y era una auténtica delicia seguir sus ejemplos y explicaciones de manera interactiva.

La parte final fue muy instructiva, se dedicaron a hacer una explicación puramente teórica sobre los algoritmos genéticos. Y entre otras cosas hablaron del ["Game of Life"](https://es.wikipedia.org/wiki/Juego_de_la_vida), impresionante https://www.youtube.com/watch?v=C2vgICfQawE



![](https://static1.squarespace.com/static/52fa93b7e4b09cd16a6f20a6/t/53cfbee9e4b0e9800a541f23/1406123754181/19thamendment_logo.png)


Otra muy interesante fue la ponencia sobre **"Deeplearning Image Recognition with Python"**. En ella el ponente, que representaba [Style Sage](http://www.stylesage.co/) , mostraba los avances en enseñar a un sistema machine learning a reconocer prendas de ropa. Su objetivo era que mediante una foto tipo modelo de catálogo de ropa pudiera identificar automáticamente si era un vestido, falda, zapatos, etc.

También resultaba una tabla de porcentajes de fiabilidad de acierto. El sistema funcionaba muy bien con fotos simples de fondos lisos y prendas normales, luego iba un poco peor con fotos mas complicadas.

Lo que si funcionaba estupendamente eran las estadísticas de previsión de acierto por cada foto. Este dato es muy importante para obtener fiabilidades de los resultados sobre grandes muestras.
Al principio me sorprendía tanto esfuerzo para temas de ropa, pero luego estaba claro: análisis automático de tendencias de moda. ¡Ahí es nada! ;)

Esta charla se completaba con la de "Análisis de colores: cómo analizar tendencias de moda automáticamente", donde el título lo dice todo, y que exponía otro integrante de la empresa Style Sage.


**py - reglas de asociación**
https://github.com/intiveda/pyreglasasociacion

Esta ponencia fue puramente teórica, los autores aun no habían usado su sistema en un caso empresarial, pero aun así fue muy interesante.
Se trata de un sistema de diseño de algoritmos usando reglas de asociación, para obtener predicciones y patrones.
Es recomendable bucear un los notebooks de su github y ver como se puede conseguir objetivos muy complicados con un diseño sencillo en intuitivo.

![](https://camo.githubusercontent.com/79e71a36859d29d387cfe2e5db79f693da087f44/68747470733a2f2f63646e2e7261776769742e636f6d2f6f70656e73697374656d61732d6875622f6f73627261696e2f6d61737465722f646f63732f736f757263652f5f7374617469632f6f73627261696e2d6c6f676f2d6e616d652e737667)

**osBrain**
https://peque.github.io/PyConES-Spain-2016-osbrain/

osBrain es parte del sistema base que usa la empresa [Open Sistemas](http://www.opensistemas.com/) que ha sido liberado para la comunidad de software libre.
El objetivo empresarial de osBrain es la inversión automática en bolsa, pero la parte liberada (en comparación con el sistema general es solo una pequeña parte) puede usarse para cualquier proyecto que requiera análisis de grandes datos y toma de decisiones o recomendaciones.

Esto es solo una muy pequeña muestra de lo que se podía encontrar en la PyConES-Spain-2016. Gran afluencia de público, muy buena organización, y satisfacción generalizada :)

También hubo un concurso de Machine Learning organizado por Cajamar en el que participé. Pero eso será en otro post.

Saludos!
