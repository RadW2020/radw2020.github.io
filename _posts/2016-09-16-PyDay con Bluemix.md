---
layout: post
title: PyDay con Bluemix
---

Hoy he participado en un taller organizado por Hacklab Almería e IBM sobre Watson y Bluemix.

![](https://i.imgur.com/ddkwHng.png)

El objetivo era montar una aplicación Python en los servidores de Bluemix, que haga uso de los servicios de la IA Watson para analizar el tono emocional de los mensajes de twitter de las cuentas que queramos.

En la [página del evento](http://hacklabalmeria.net/actividades/2016/09/15/taller-de-watson.html) está la introducción al taller y los enlaces necesarios para llevarla a cabo. Una vez seguidos los pasos previos, pasamos a la acción.

Creamos una app en nuestro panel de control de Bluemix.

![](https://i.imgur.com/VcwcIJN.png)

Tipo Web
![](https://i.imgur.com/q9U7Zp5.png)

Empezamos con Python
![](https://i.imgur.com/ljQFcSi.png)

Seguimos los pasos poniendo un nombre a la aplicación
![](https://i.imgur.com/FDpsnx2.png)

En los pasos previos descritos en la web de HacklabAl, instalamos la interfaz de linea de comandos de Cloud Foundry y la de Bluemix.
Podemos saltar este paso.
Nosotros vamos a usar el ejemplo sobre twitter, así que podemos obviar la descarga del código inicial. Aunque también le podemos echar un vistazo ya que es un ejemplo sencillo con "Hola mundo" y siempre es instructivo.
![](https://i.imgur.com/HRW4EZP.png)

Seguimos las pasos 5 y 6 tal y como nos aparezca para ver que no hay problemas con las conexiones.
![](https://i.imgur.com/bliGXfC.png)

Antes de subir nuestro código vamos a instalar el servicio (API) que interpreta el tono de los mensajes de twitter.
![](https://i.imgur.com/1TrI19W.png)

Se trata de la app cognitiva Tone Analyzer
![](https://i.imgur.com/RuBJwqF.png)

Tomamos nota del nombre del servicio, ya que luego nos hará falta. También podemos ver que IBM nos brinda las primeras 1000 llamadas API de cada mes de manera gratuita. También podemos preveer el coste de nuestra app en el caso que estemos planeando hacer algo mas ambicioso.
![](https://i.imgur.com/O53rG5j.png)

Debemos tomar nota de nuestras credenciales de servicio, ya que nuestra app en Python las usará para conectarse a la API.
![](https://i.imgur.com/K1Hbzfu.png)

Ahora podemos ir a nuestro panel de control y comprobar que tenemos listo lo que hemos creado.
![](https://i.imgur.com/wgtaoe4.png)

Dentro de nuestra app de prueba, vamos a enlazar la API Tone Analyzer. Aparece un menú con las APIs o servicios que tengamos iniciados. Si es la primera vez que usas Bluemix aparecerá solo uno. Lo enlazamos y ya lo tenemos listo.
![](https://i.imgur.com/a3HnJq3.png)

Ahora falta editar los archivos del proyecto que hemos descargado en local.
Primero editamos manifest.yml
* name y host son iguales, se pone la primera parte de la ruta a nuestra app.
* domain debemos comprobar que es igual a la segunda parte de la ruta de nuestra app.
* services debemos introducir el nombre que ha tomado nuestro servicio, tal y como hemos apuntado anteriormente.
![](https://i.imgur.com/5KYv4Rm.png)

Aquí es uno de los sitios donde podemos consultar la ruta a nuestra app.
![](https://i.imgur.com/1IHZUV1.png)

Vamos a nuestro gestor de apps de twitter y creamos una nueva si no lo hemos hecho ya.
![](https://i.imgur.com/zBWyYDl.png)

Tomamos nota de nuestros keys y tokens de acceso.
![](https://i.imgur.com/Q7fCf1T.png)

Los introducimos en el archivo scope.py
También debemos completar el usuario y password del Tone Analyzer que tenemos disponible en nuestro espacio en Bluemix. Esto es las credenciales que hemos comentado antes.
![](https://i.imgur.com/MTYVkyA.png)

Una vez que tenemos todo listo ya podemos subir nuestra app local en python a bluemix.

```cf push "nombre de nuestra app"```

Ya podemos ver nuestra app funcionando en su dirección.
En los cuatro campos debemos poner cuatro cuentas de twitter que queramos analizar. La aplicación leerá los cuatro últimos tweets de cada una y analizará el tono emocional devolviendo unos parámetros.

![](https://i.imgur.com/q4O1Y43.png)

En mi caso voy a poner a cuatro actores. Es bien sabido que son de mucho twitear así que viene bien para hacer pruebas ;)
![](https://i.imgur.com/Bn735qJ.png)

El gráfico generado en nuestra app es interactivo si pasamos el ratón sobre él.
![](https://i.imgur.com/BtkeGoz.png)

Para saber mas sobre este resultado debemos ver primero como se comunica la app con el Tone Analyzer en el archivo ```score.py```

Por último, y no por ello menos interesante :D , podemos ver en el archivo ```index.html``` el script que se usa para representar el gráfico. Nos lleva a una web repleta de soluciones para mostrar información que hará las delicias de aficionados y profesionales del Big Data.

![](https://i.imgur.com/ATBgOxF.jpg)

Saludos!
