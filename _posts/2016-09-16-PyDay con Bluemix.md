---
layout: post
title: PyDay con Bluemix
---

Hoy he participado en un taller organizado por Hacklab Almería e IBM sobre Watson y Bluemix.

![](http://dii.ufv.es/wp-content/uploads/2016/02/ibm-bluemix.png)

El objetivo era montar una aplicación Python en los servidores de Bluemix, que haga uso de los servicios de la IA Watson para analizar el tono emocional de los mensajes de twitter de las cuentas que queramos.

En la [página del evento](http://hacklabalmeria.net/actividades/2016/09/15/taller-de-watson.html) está la introducción al taller y los enlaces necesarios para llevarla a cabo. Una vez seguidos los pasos previos, pasamos a la acción.

Creamos una app en nuestro panel de control de Bluemix.

![](http://i66.tinypic.com/i2io1g.png)

Tipo Web
![](http://i64.tinypic.com/2pqizgx.png)

Empezamos con Python
![](http://i65.tinypic.com/jpiyh4.png)

Seguimos los paso poniendo un nombre a la aplicación
![](http://i67.tinypic.com/zyd7wo.png)

En los pasos previos descritos en la web de HacklabAl, instalamos la interfaz de linea de comandos de Cloud Foundry y la de Bluemix.
Podemos saltar este paso.
Nosotros vamos a usar el ejemplo sobre twitter, así que podemos obviar la descarga del código inicial. Aunque también le podemos echar un vistazo ya que es un ejemplo sencillo con "Hola mundo" y siempre es instructivo.
![](http://i68.tinypic.com/1g0vbr.png)

Seguimos las pasos 5 y 6 tal y como nos aparezca para ver que no hay problemas con las conexiones.
![](http://i64.tinypic.com/29ei3vt.png)

Antes de subir nuestro código vamos a instalar el servicio (API) que interpreta el tono de los mensajes de twitter.
![](http://i63.tinypic.com/mhrfhk.png)

Se trata de la app cognitiva Tone Analyzer
![](http://i65.tinypic.com/30c5211.png)

Tomamos nota del nombre del servicio, ya que luego nos hará falta. También podemos ver que IBM nos brinda las primeras 1000 llamadas API de cada mes de manera gratuita. También podemos preveer el coste de nuestra app en el caso que estemos planeando hacer algo mas ambicioso.
![](http://i67.tinypic.com/2lt4lf9.png)

Debemos tomar nota de nuestras credenciales de servicio, ya que nuestra app en Python las usará para conectarse a la API.
![](http://i68.tinypic.com/sfdts6.png)

Ahora podemos ir a nuestro panel de control y comprobar que tenemos listo lo que hemos creado.
![](http://i68.tinypic.com/2isxv6r.png)

Dentro de nuestra app de prueba, vamos a enlazar la API Tone Analyzer. Aparece un menú con las APIs o servicios que tengamos iniciados. Si es la primera vez que usas Bluemix aparecerá solo uno. Lo enlazamos y ya lo tenemos listo.
![](http://i63.tinypic.com/j75jb7.png)

Ahora falta editar los archivos del proyecto que hemos descargado en local.
Primero editamos manifest.yml
* name y host son iguales, se pone la primera parte de la ruta a nuestra app.
* domain debemos comprobar que es igual a la segunda parte de la ruta de nuestra app.
* services debemos introducir el nombre que ha tomado nuestro servicio, tal y como hemos apuntado anteriormente.
![](http://i66.tinypic.com/308jwus.png)

Aquí es uno de los sitios donde podemos consultar la ruta a nuestra app.
![](http://i63.tinypic.com/2qib7ue.png)

Vamos a nuestro gestor de apps de twitter y creamos una nueva si no lo hemos hecho ya.
![](http://i66.tinypic.com/zlelnc.png)

Tomamos nota de nuestros keys y tokens de acceso.
![](http://i63.tinypic.com/k1vvx4.png)

Los introducimos en el archivo scope.py
También debemos completar el usuario y password del Tone Analyzer que tenemos disponible en nuestro espacio en Bluemix. Esto es las credenciales que hemos comentado antes.
![](http://i65.tinypic.com/dsbbs.png)

Una vez que tenemos todo listo ya podemos subir nuestra app local en python a bluemix.

```cf push "nombre de nuestra app"```

Ya podemos ver nuestra app funcionando en su dirección.
En los cuatro campos debemos poner cuatro cuentas de twitter que queramos analizar. La aplicación leerá los cuatro últimos tweets de cada una y analizará el tono emocional devolviendo unos parámetros.

![](http://i68.tinypic.com/uwi69.png)

En mi caso voy a poner a cuatro actores. Es bien sabido que son de mucho twitear así que viene bien para hacer pruebas ;)
![](http://i67.tinypic.com/35mic7r.png)

El gráfico generado en nuestra app es interactivo si pasamos el ratón sobre él.
![](http://i66.tinypic.com/2hgzg9z.png)

Para saber mas sobre este resultado debemos ver primero como se comunica la app con el Tone Analyzer en el archivo ```score.py```

Por último, y no por ello menos interesante :D , podemos ver en el archivo ```index.html``` el script que se usa para representar el gráfico. Nos lleva a una web repleta de soluciones para mostrar información que hará las delicias de aficionados y profesionales del Big Data.

![](http://i65.tinypic.com/25t80ex.jpg)

Saludos!
