---
layout: post
title: Hibernate - Toma de contacto
---
Esta serie de ejemplos es la que me ha servido para una primera toma de contacto con
Hibernate.

![](https://alejandromunyozsegrera.files.wordpress.com/2014/01/hibernate.png)
https://es.wikipedia.org/wiki/Hibernate

He usado Netbeans 8.2 y JDK 8 en Windows 10. La base de datos es MySQL y la manipulo con MySQL Workbench, que es una de las herramientas que se instalan con [el instalador automático](http://dev.mysql.com/downloads/installer/)

![](https://i.imgur.com/ZGFIpWu.jpg)

En este artículo vamos a crear un proyecto en java y a configurar Hibernate para que actúe entre la base de datos MySQL, que tenemos funcionando mediante el puerto 3306, y nuestro código en Java. Gracias a Hibernate trataremos la Base de Datos relacional como si fueran objetos.

Para ello comprobamos que tenemos el plugin Hibernate instalado en nuestro Netbeans.

![](https://i.imgur.com/OELsqbK.jpg)

Aquí aparece como instalado, pero si no lo estuviera lo podemos instalar desde este mismo menú.

![](https://i.imgur.com/Ecxyz4a.jpg)

Iniciamos el servicio de conexión a la BD

![](https://i.imgur.com/SO6hDX6.jpg)

Introducimos contraseña. Al ser una BD en modo local no hay que configurar nada salvo comprobar el puerto.

![](https://i.imgur.com/aTBzmkP.jpg)

Ya tenemos conexión a nuestra BD MySQL. La Base de Datos Empresaz es la que vamos a usar. Se puede ver de que trata exactamente en este repositorio:
https://github.com/RadW2020/Hibernate-Toma-de-Contacto/blob/master/empresaz.sql

![](https://i.imgur.com/bHHhBB2.jpg)

Conectamos

![](https://i.imgur.com/LiQlOJD.jpg)

Nos pide contraseña de nuevo

![](https://i.imgur.com/6XWNfeY.jpg)

Ya tenemos nuestro driver JDBC configurado y funcionando en nuestro proyecto de Netbeans. (En este punto he de decir que tuve problemas al cargar la base de datos y que luego el plugin Hibernate se configurara correctamente. Cualquier fallo que he podido encontrar lo he solucionado reiniciando Netbeans)

![](https://i.imgur.com/f2cpDYd.jpg)

Creamos un proyecto nuevo y vacío. Y añadimos las librerías pertinentes.

![](https://i.imgur.com/KTiNYME.jpg)

Seleccionamos la más adecuada a nuestro proyecto.

![](https://i.imgur.com/v1gy3fL.jpg)

El proyecto ya tiene las librerías cargadas.

![](https://i.imgur.com/n94Okv8.jpg)

Empezamos a crear los archivos de configuración Hibernate

![](https://i.imgur.com/AdF4vJi.jpg)

El asistente de configuración ayuda a crear el archivo .cfg

![](https://i.imgur.com/3mR1156.jpg)

Comprobamos nombre y carpeta de destino

![](https://i.imgur.com/XBcLQPc.jpg)

Importante seleccionar la BD con la que vamos a trabajar.

![](https://i.imgur.com/fUEQnxH.jpg)

Ya tenemos el archivo creado, en formato xml, que Netbeans nos muestra en modo gráfico para mayor comodidad.

![](https://i.imgur.com/7RK8B5C.jpg)

Si se desea editar el archivo en modo texto se puede hacer sin problema.

![](https://i.imgur.com/d2D6jdF.jpg)

Vamos a editar una propiedad. Para ello primero añadimos.

![](https://i.imgur.com/YFeMOQy.jpg)

En este caso queremos ver todo el log de depuración resultante de ejecutar operaciones SQL por consola.

![](https://i.imgur.com/k4y4e9l.jpg)

Esta opción de parser, en teoría viene implementada en Hibernate por defecto desde la versión 4.1. Aun así lo podemos activar por aquí.

![](https://i.imgur.com/2tNF5bJ.jpg)

Seguimos creando archivos Hibernate

![](https://i.imgur.com/ELihkIi.jpg)

En este caso el HibernateUtil, que nos proporciona una referencia al objeto SessionFactory para que cualquier clase tenga acceso al objeto sesión en la aplicación. Mas información en [CursoHibernate.HibernateUtil](http://www.cursohibernate.es/doku.php?id=unidades:07_arquitectura:01_hibernateutil)



![](https://i.imgur.com/FJi3Wwt.jpg)

Seleccionamos nombre y paquete

![](https://i.imgur.com/2ym3b5b.jpg)

Ya tenemos nuestro archivo creado automáticamente

![](https://i.imgur.com/seWCvzR.jpg)

Ahora vamos a por la ingeniería inversa de nuestra BD

![](https://i.imgur.com/UGEMHRY.jpg)

Va a identificar las tablas de la BD a la que estamos conectados

![](https://i.imgur.com/euphjB8.jpg)

Comprobamos nombre y directorio

![](https://i.imgur.com/qQ0q7IR.jpg)

Añadimos las tablas sobre las que vamos a trabajar

![](https://i.imgur.com/1TVxGsd.jpg)

Este es el archivo generado por ingeniería inversa en modo texto.

![](https://i.imgur.com/AYHetcT.jpg)

Por último los POJOs y los archivos de mapeado

![](https://i.imgur.com/j41Fcev.jpg)

Definimos su propio paquete ya que nos generará una serie de archivos. Las clases java con sus atributos,  constructores y métodos de get y set.
Y los archivos xml de mapeado hibernate.
Este binomio xml-ClasesDeJava mapea la base de datos relacional y genera una capa intermedia que trata la tabla de datos relacional como una tabla objeto-relacional.
De esta forma nos podemos relacionar con la tabla como si fueran objetos Java.
Hibernate puede generar autométicamente los constructores y los metodos get y set, después podemos implementar los métodos que creamos conveniente.

![](https://i.imgur.com/AdG4vXH.jpg)

Ahora ya estamos listos para empezar a probar y crear métodos. Se pueden hacer consultas HQL desde Netbeans.

![](https://i.imgur.com/Nb5mPzS.jpg)

Probamos algo sencillo y comprobamos los datos de la tabla empleados

![](https://i.imgur.com/4hCsax2.jpg)

Podemos crear métodos para obtener listas de datos, como este, que muestra una lista de los departamentos

![](https://i.imgur.com/3vGkWdu.jpg)

También se pueden insertar filas en la BD.
El procedimiento es siempre parecido: se obtiene un objeto SessionFactory y abrimos una sesión. Se comienza el estado transacción. Se graban los datos (en este caso se crea un objeto departamento vacío y se le añaden los campos) y se graba. Finalmente la transacción se lleva a cabo con el commit().

![](https://i.imgur.com/l6tj50R.jpg)

Este podría ser un main en el que mostramos los departamentos, creamos un departamento nuevo, y comprobamos su inserción.

![](https://i.imgur.com/uldYBtj.jpg)

Esta es la salida por consola. Recuerda que tenemos el modo sql debug activo, por eso nos salen todos los mensajes de funcionamiento de hibernate.

![](https://i.imgur.com/hLg5vUf.jpg)


En el siguiente artículo seguiré investigando cosas sobre Hibernate y probando sus funcionalidades.

Usaré este [repositorio en Github](https://github.com/RadW2020/Hibernate_Empresaz) para todo el código que se muestre. Así que si habéis intentado copiar los métodos y frustrado por que era una imagen, no desesperéis ;)

Saludos!
