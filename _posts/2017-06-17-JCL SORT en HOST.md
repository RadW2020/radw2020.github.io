---
layout: post
title: JCL SORT en HOST
---
 
[Introduce aquí tu excusa preferida para seguir leyendo este post]
 
Vamos a ordenar un dataset que contiene registros de información usando la librería SORT.
Tenemos un set de datos de caracteres con una serie de registros con un número y el nombre de un pais.
Mediante el script lo vamos a leer, ordenar como queramos, y guardar el resultado en otro archivo.
  
Antes de ponernos manos a la obra tenemos que afilar las herramientas y preparar la partida de trabajo. Lo que 
en el argot gastronómico se conoce como [*Mise en place*](https://es.wikipedia.org/wiki/Mise_en_place). 

Este paso lo voy a hacer un poco mas exhaustivo para que sirva en futuros ejercicios.

Primeramente la estructura de direcciones.

![](https://i.imgur.com/jkfgLjr.png)

Y los detalles pormenorizados. 

Hay que tener en cuenta que los miembros de cada PDS heredan las 
características del dataset en el que están alojados (si han sido creados dentro de él). 

COBOL 

![](https://i.imgur.com/KuWS6P1.png)

COPYS

![](https://i.imgur.com/5h1TzR2.png)

LOAD

![](https://i.imgur.com/b0GCfg9.png)

OBJ

![](https://i.imgur.com/WhoET1F.png)

DATA

![](https://i.imgur.com/2sSOmqe.png)

JCL

![](https://i.imgur.com/pAH2zhu.png)

Este es el archivo de ejemplo que vamos a ordenar. 

Está creado de manera arbitraria con algunos
códigos iguales para ver como se comporta en estos casos. 

![](https://i.imgur.com/GRwc49s.png)

El JOB que lanza esta operación se compone de dos pasos. Uno que borra el archivo resultante, 
para el caso de que ya exista, como ocurrirá cuando lanzemos el job mas de una vez. Y el otro que lee, 
ordena y escribe una salida.

![](https://i.imgur.com/KYop49A.png)

El paso DELETE ejecuta la herramienta IDCAMS. Esta sirve para realizar operativas sobre ficheros VSAM.
Con ella podemos por ejemplo crear un archivo, borrarlo, copiarlo o imprimirlo.

El Card SYSPRINT indica el lugar al que deseamos que se envíen todos los mensajes generados durante 
el proceso de ejecución. Si ponemos SYSOUT=* entonces dicha información se enviará directamente 
al SPOOL (a la MSGCLASS indicada en nuestro job).

El Card SYSIN sirve para introducir la instrucción que queremos que ejecute IDCAMS. En este caso
borrar un fichero dado. Se fuerza la salida MAXCC a cero para evitar que se pare el job dando un error
 si no encuentra el fichero.

![](https://i.imgur.com/jA3oP4O.png)

El paso ORDENA ejecuta la herramienta SORT.

Se define el archivo de entrada (el de los paises en este caso) en SORTIN, y el archivo que 
queremos crear con la salida en SORTOUT.

Enviamos la salida de mensajes generados al SPOOL igual que en IDCAMS.

Y por último introducimos los parámetros que queremos aplicar en SYSIN.

![](https://i.imgur.com/jFrMkpZ.png)

SORT FIELDS tiene en este caso dos instrucciones. 

La primera ordena de las columnas 1 a 3,
tomando el dato como BI ( unsigned binary(2,4 o 8 bytes), de manera Ascendente.

La segunda ordena leyendo las columnas 3 a 15, tomando el dato como CH (alfanumérico), de manera 
Ascendente.

El resultado de la ejecución lo podemos ver abriendo el archivo creado por SORT.
Vemos como ha ordenado de menos a mayor según el código (siguiendo la primera isntrucción)
, y de manera ascendente según el texto en el caso de coincidencias, vease los 66.

![](https://i.imgur.com/wn2O1aV.png)

Esto es todo por ahora :)

Saludos!



  










