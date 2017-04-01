---
layout: post
title: Hibernate - Toma de contacto
---
Esta serie de ejemplos es la que me ha servido para una primera toma de contacto con
Hibernate.

![](https://alejandromunyozsegrera.files.wordpress.com/2014/01/hibernate.png)
https://es.wikipedia.org/wiki/Hibernate

He usado Netbeans 8.2 y JDK 8 en Windows 10. La base de datos es MySQL y la manipulo con MySQL Workbench, que es una de las herramientas que se instalan con [el instalador automático](http://dev.mysql.com/downloads/installer/)

![](http://i68.tinypic.com/2hh3ol5.jpg)

En este artículo vamos a crear un proyecto en java y a configurar Hibernate para que actúe entre la base de datos MySQL, que tenemos funcionando mediante el puerto 3306, y nuestro código en Java. Gracias a Hibernate trataremos la Base de Datos relacional como si fueran objetos.

Para ello comprobamos que tenemos el plugin Hibernate instalado en nuestro Netbeans.

![](http://i65.tinypic.com/ww15op.jpg)

Aquí aparece como instalado, pero si no lo estuviera lo podemos instalar desde este mismo menú.

![](http://i63.tinypic.com/2sammhu.jpg)

Iniciamos el servicio de conexión a la BD

![](http://i68.tinypic.com/55fdw.jpg)

Introducimos contraseña. Al ser una BD en modo local no hay que configurar nada salvo comprobar el puerto.

![](http://i64.tinypic.com/o0xxex.jpg)

Ya tenemos conexión a nuestra BD MySQL. La Base de Datos Empresaz es la que vamos a usar. Se puede ver de que trata exactamente en este repositorio:
https://github.com/RadW2020/Hibernate-Toma-de-Contacto/blob/master/empresaz.sql

![](http://i67.tinypic.com/357m35z.jpg)

Conectamos

![](http://i68.tinypic.com/2qthk42.jpg)

Nos pide contraseña de nuevo

![](http://i64.tinypic.com/1zb84xy.jpg)

Ya tenemos nuestro driver JDBC configurado y funcionando en nuestro proyecto de Netbeans. (En este punto he de decir que tuve problemas al cargar la base de datos y que luego el plugin Hibernate se configurara correctamente. Cualquier fallo que he podido encontrar lo he solucionado reiniciando Netbeans)

![](http://i65.tinypic.com/2hofl7a.jpg)

Creamos un proyecto nuevo y vacío. Y añadimos las librerías pertinentes.

![](http://i64.tinypic.com/33cx63q.jpg)

Seleccionamos la más adecuada a nuestro proyecto.

![](http://i68.tinypic.com/rwqmfm.jpg)

El proyecto ya tiene las librerías cargadas.

![](http://i67.tinypic.com/2s01xsj.jpg)

Empezamos a crear los archivos de configuración Hibernate

![](http://i64.tinypic.com/350lyr6.jpg)

El asistente de configuración ayuda a crear el archivo .cfg

![](http://i63.tinypic.com/20qe3df.jpg)

Comprobamos nombre y carpeta de destino

![](http://i64.tinypic.com/2vxrm6g.jpg)

Importante seleccionar la BD con la que vamos a trabajar.

![](http://i65.tinypic.com/nv2lfn.jpg)

Ya tenemos el archivo creado, en formato xml, que Netbeans nos muestra en modo gráfico para mayor comodidad.

![](http://i63.tinypic.com/214eeki.jpg)

Si se desea editar el archivo en modo texto se puede hacer sin problema.

![](http://i68.tinypic.com/juuy3r.jpg)

Vamos a editar una propiedad. Para ello primero añadimos.

![](http://i63.tinypic.com/sx24k4.jpg)

En este caso queremos ver todo el log de depuración resultante de ejecutar operaciones SQL por consola.

![](http://i64.tinypic.com/30rshom.jpg)

Esta opción de parser, en teoría viene implementada en Hibernate por defecto desde la versión 4.1. Aun así lo podemos activar por aquí.

![](http://i67.tinypic.com/oaavt1.jpg)

Seguimos creando archivos Hibernate

![](http://i65.tinypic.com/2w32hj4.jpg)

En este caso el HibernateUtil, que nos proporciona una referencia al objeto SessionFactory para que cualquier clase tenga acceso al objeto sesión en la aplicación. Mas información en [CursoHibernate.HibernateUtil](http://www.cursohibernate.es/doku.php?id=unidades:07_arquitectura:01_hibernateutil)



![](http://i68.tinypic.com/2i9saar.jpg)

Seleccionamos nombre y paquete

![](http://i63.tinypic.com/16jecdi.jpg)

Ya tenemos nuestro archivo creado automáticamente

![](http://i65.tinypic.com/1ttvue.jpg)

Ahora vamos a por la ingeniería inversa de nuestra BD

![](http://i68.tinypic.com/aoruyh.jpg)

Va a identificar las tablas de la BD a la que estamos conectados

![](http://i67.tinypic.com/2zq525h.jpg)

Comprobamos nombre y directorio

![](http://i63.tinypic.com/1el2fc.jpg)

Añadimos las tablas sobre las que vamos a trabajar

![](http://i65.tinypic.com/1t2dkz.jpg)

Este es el archivo generado por ingeniería inversa en modo texto.

![](http://i68.tinypic.com/dgo4cm.jpg)

Por último los POJOs y los archivos de mapeado

![](http://i68.tinypic.com/3358g2x.jpg)

Definimos su propio paquete ya que nos generará una serie de archivos. Las clases java con sus atributos,  constructores y métodos de get y set.
Y los archivos xml de mapeado hibernate.
Este binomio xml-ClasesDeJava mapea la base de datos relacional y genera una capa intermedia que trata la tabla de datos relacional como una tabla objeto-relacional.
De esta forma nos podemos relacionar con la tabla como si fueran objetos Java.
Hibernate puede generar autométicamente los constructores y los metodos get y set, después podemos implementar los métodos que creamos conveniente.

![](http://i64.tinypic.com/2mdjv3l.jpg)

Ahora ya estamos listos para empezar a probar y crear métodos. Se pueden hacer consultas HQL desde Netbeans.

![](http://i68.tinypic.com/16gdefd.jpg)

Probamos algo sencillo y comprobamos los datos de la tabla empleados

![](http://i63.tinypic.com/b47qet.jpg)

Podemos crear métodos para obtener listas de datos, como este, que muestra una lista de los departamentos

![](http://i67.tinypic.com/est5jt.jpg)

También se pueden insertar filas en la BD.
El procedimiento es siempre parecido: se obtiene un objeto SessionFactory y abrimos una sesión. Se comienza el estado transacción. Se graban los datos (en este caso se crea un objeto departamento vacío y se le añaden los campos) y se graba. Finalmente la transacción se lleva a cabo con el commit().

![](http://i66.tinypic.com/2mr65ad.jpg)

Este podría ser un main en el que mostramos los departamentos, creamos un departamento nuevo, y comprobamos su inserción.

![](http://i63.tinypic.com/30hymfk.jpg)

Esta es la salida por consola. Recuerda que tenemos el modo sql debug activo, por eso nos salen todos los mensajes de funcionamiento de hibernate.

![](http://i66.tinypic.com/1e0zuc.jpg)


En el siguiente artículo seguiré investigando cosas sobre Hibernate y probando sus funcionalidades.

Usaré este [repositorio en Github](https://github.com/RadW2020/Hibernate_Empresaz) para todo el código que se muestre. Así que si habéis intentado copiar los métodos y frustrado por que era una imagen, no desesperéis ;)

Saludos!
