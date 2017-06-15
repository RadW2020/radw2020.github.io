---
layout: post
title: Compile Link and Go JCL COBOL
---


[JCL](https://es.wikipedia.org/wiki/Job_Control_Language) es tan parco que 
no tiene ni logotipo. Igual que [COBOL](https://es.wikipedia.org/wiki/COBOL).
 Así son ellos. 
No necesitan de frontends ni modernuras atractivas para llamar la atención. 
No lo necesitan. Están ahí, ocupando su merecido espacio en la industria de 
la información, y ningun hype-stack les va a mojar la oreja por mucho tiempo. 

Pero si voy a poner una foto de los nuevos mainframes de IBM, porque están MUY chulos.

![](http://3.bp.blogspot.com/-8IEJ8iNheT8/VLVXdpMQ9kI/AAAAAAAAAxk/dm-I5IWigew/s1600/01-z13-Front.jpg)

:D

Este minitutorial explica de que manera se puede compilar y ejecutar 
un código fuente COBOL en un mainframe de IBM con zOS 110, usando ISPF.
Lo que se conoce en el argot anglosajón como COMPILE LINK AND GO.

Por lo pronto esta es la version usada. Cosa importante
 ya que muchas librerías tienen otros nombres dependiendo de la versión.

![](http://i.imgur.com/W9VUXuY.png)

Esta es la estructura de datasets que he usado para realizar este ejercicio. 
Son todos PDS con su respectivo espacio para alojar miembros.
- COBOL para el código fuente
- COBOL.COPYS para las copias
- COBOL.LOAD para alojar el ejecutable
- COBOL.OBJ para las posibles rutinas
- COBOL.JCL para los Jobs

![](http://i.imgur.com/jpso8IE.png)

Podemos ver su información usando la barra como comando y después usando la opción *info*

![](http://i.imgur.com/JmL40gd.png)

Todos los datasets relacionados con COBOL tienen record length de 80. Aunque el que va a 
alojar los archivos fuente me ha quedado algo pequeño con solo 5 espacios. 
El resto me he curado en salud y los he puesto a 100.

![](http://i.imgur.com/JrqAgq8.png)

Información del PDS que guarda los scripts jcl. 

![](http://i.imgur.com/3ACEwY9.png)

Importante si os quedais si espacio en un dataset, lo podeis comprimir mientras 
pensais que nuevo diseño vais a usar cuando se os llene de nuevo.

El programa COBOL que vamos a compilar es un algoritmo simple que calcula si un año
es bisiesto en un intervalo dado.

El código se puede encontrar 
[AQUI](https://gist.github.com/RadW2020/c87ef711bdbd03e2544e43bf6776542d)
 
Aunque un profesional de verdad jamas usaría github teniendo ISPF :p
 
![](http://i.imgur.com/HgfJOP3.png)

Codificar un programa COBOL, para alguien con experiencia en lenguajes de 
programación, puede ser relativamente trivial. La complejidad viene dada 
sobre todo por los datos a tratar. Ya sean registros VSAM o una base de datos DB2.

En este caso es un ejemplo simple para dejar una base sobre la que ir trabajando
futuros ejemplos. 

Tener un JCL bien formado y un entorno de trabajo funcional no es tarea sencilla
si eres nuevo en este campo, por mucho linux que tengas a la espalda.

Este es el código JCL usado para la ejecución del ejercicio 
[JCl-JOB](https://gist.github.com/RadW2020/ab963b92f97e2e8c58ba2290179596c5)

Y su implementación en ISPF.

![](http://i.imgur.com/nEQb7pJ.png)

Entrar a describir al detalle cada uno de los elementos aquí formados, puede ser
tarea ardua e indeseada, sobre todo por mí. Bromas aparte, merece toda una serie 
de posts y empezar por ejemplos mas sencillos que este. 

En próximos posts pondré algún ejemplo de funcionalidad de JCL para el manejo
y edición de datasets, sin entrar en compilaciones.

Lo que si haré, al menos, es comentar que este JOB se compone de varios pasos:
- PASOCOMP que se encarga de compilar haciendo uso del compilador 
[IGYCRCTL](https://www.tutorialspoint.com/jcl/jcl_run_cobol_programs.htm) [**compile**]
- PASOLKED que enlaza las posibles rutinas necesarias 
para la ejecución de nuestro programa y preparar un "ejecutable" listo para usar 
por ejemplo en un BATCH [**link**]
- PASOEXEC que ejecuta nuestro programa compilado [**load**]

Lanzamos el job con SUB y nos preparamos a depurar como si no hubiera un mañana.

Aquí se puede ver el log una vez superados los tres pasos.
Para comprobar la salida nos vamos al sublog de ejecución.

![](http://i.imgur.com/sYcVEQk.png)

Aquí el resultado de la ejecución correcta. 

![](http://i.imgur.com/MzfaoGu.png)

Me he saltado las horas de búsqueda de errores y documentación que he necesitado 
para ver funcionar el programa. Mi aliciente es saber que casi todos eran errores triviales
tipo formateo del código fuente, características de los datasets, librerías que ahora
tienen otro nombre, y cosas del estilo. 
Nada que no se pueda dominar con un poco de práctica ;)

Saludos 





