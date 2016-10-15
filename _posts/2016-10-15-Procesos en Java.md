---
layout: post
title: Procesos en Java, operaciones básicas
---


Vamos a hacer un pequeño ejercicio muy básico para ver como se comportan los procesos en Java.
El objetivo es tener un proceso que inicialize otros procesos. Lo vamos a hacer de manera gráfica y así quedará bastante mas claro e intuitivo.

En este caso vamos a usar Netbeans 8.1 con JDK 1.8 sobre Windows 10
![](http://i63.tinypic.com/k4xnib.jpg)

Creamos un nuevo proyecto

![](http://i66.tinypic.com/2ue7fuu.jpg)

Buscamos los ejemplos en la carpeta samples/java el que se llama **ClientEditor**

![](http://i63.tinypic.com/16bka3p.jpg)


Se define el nombre y guardamos

![](http://i63.tinypic.com/260sc2g.jpg)

Este es el ejemplo ClientEditor cargado en nuestro IDE

![](http://i67.tinypic.com/zleyb5.jpg)

Hacemos un Build Project para que se compile el archivo jar que vamos a necesitar mas adelante

![](http://i68.tinypic.com/5njati.jpg)

También debemos ejecutar *run* la aplicación desde el IDE para comprobar que no haya problemas

![](http://i63.tinypic.com/r70w2a.jpg)

Esta ventana es el resultado de la ejecución

![](http://i67.tinypic.com/2ms1p1g.jpg)

Debemos tener localizado el archivo ClientEditor.jar que estará dentro de la carpeta *dist*

![](http://i65.tinypic.com/2woapa8.jpg)

Ahora vamos a crear otra aplicación muy simple con un botón para que cada vez que se pulse el botón se ejecute la aplicación que acabamos de compilar.

![](http://i64.tinypic.com/n63m9y.jpg)

Definimos nombre y guardamos. No va a ser necesario definir el main para la prueba que vamos a hacer.

![](http://i64.tinypic.com/2hy9kl1.jpg)

Creamos un JFrame Form

![](http://i63.tinypic.com/2ephrur.jpg)

Añadimos un botón. Se puede arrastrar y soltar sobre nuestro frame.

![](http://i64.tinypic.com/30ii5wh.jpg)

Editamos el texto. Una manera es con botón derecho del ratón *Edit Text*

![](http://i64.tinypic.com/11icu2d.jpg)

Podemos editar mas opciones en el panel de propiedades del botón, como por ejemplo el tamaño.

![](http://i66.tinypic.com/35jje53.jpg)

Ahora usando el menu flotante que aparece con el botón derecho del ratón, vamos a asiganr un evento del ratón cuando se haga click.

![](http://i63.tinypic.com/54cgag.jpg)

Vemos como el IDE nos crea un método vacío, listo para que lo definamos

![](http://i63.tinypic.com/2ezkbw8.jpg)

Podemos definir dentro del método directamente la lógica de funcionamiento, pero es mejor definir un método nuevo con la funcionalidad que se va a ejecutar. En este caso *crearNuevoEditor()*.
Desde el método *JButton1MouseClicked()* lo ejecutamos, y así queda ordenado en el caso que queramos ampliar la funcionalidad con mas método que hagan otras cosas.

En el método *crearNuevoEditor()*  usamos la [clase process](http://docs.oracle.com/javase/8/docs/api/java/lang/Process.html) para llevar a cabo un [Runtime.getRuntime().exec](https://docs.oracle.com/javase/7/docs/api/java/lang/Runtime.html#exec(java.lang.String) y así ejecutar el jar que teníamos creado inicialmente como un proceso independiente

![](http://i64.tinypic.com/2z7imqc.jpg)

Ejecutamos nuestro frame, el IDE nos avisa que no hay main, se lo asignamos y continuamos.
![](http://i65.tinypic.com/2qu3ec5.jpg)

Este es el resultado de hacer click sobre el botón tres veces.

![](http://i65.tinypic.com/earthe.jpg)

Comprobamos la lista de procesos en el sistema con tasklist en la linea de comandos

![](http://i67.tinypic.com/2lj0xz6.jpg)

Podemos identificar los PID de los procesos en cuestion. Tenemos el de netbeans identificado por su nombre, y después cuatro procesos java, uno del lanzador y tres de los lanzados.

![](http://i63.tinypic.com/2w4l893.jpg)

Si lo deseamos podemos terminar con un proceso con el comando taskkill /PID numDeProces

![](http://i65.tinypic.com/2agoe8.jpg)

Este es el resultado después de matar un proceso

![](http://i67.tinypic.com/10pzll4.jpg)

También podemos cerrar un proceso desde el administrador de tareas de Windows

![](http://i63.tinypic.com/win9f.jpg)

Ya solo nos queda uno. Que también se puede cerrar como si fuera una ventana gracias al interfáz gráfico que hemos obtenido con swing.

![](http://i65.tinypic.com/20sw48w.jpg)

Saludos!
