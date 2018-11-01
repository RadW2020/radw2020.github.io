---
layout: post
title: Angular Router. Un acercamiento desde la teoría.
image: featured_image_TS.bmp
---

El Router de Angular permite el uso de la aplicación navegando de una vista a otra como si de páginas web se tratara.

Un navegador web ofrece un modelo de uso muy familiar:
- Introduce una URL en la barra de direcciones para ir a la página correspondiente.
- Permite hace click en enlaces que llevan a otras páginas.
- Navega adelante y atrás en el histórico de páginas del navegador.

El Router de Angular toma prestado este modelo. Puede interpretar la URL del navegador para ir a una vista generada en el cliente. Puede aceptar parámetros de manera opcional. Y el router crea un log de actividad en el historial del navegador de tal modo que los botones adelante y atrás funcionan bien.

### <base href>

Se debe añadir un elemento de tipo _<base>_ al index.html como el primer hijo en el _<head>_ para decirle al router como componente las URLs.

Por ejemplo:

``` html
<base href="/">
```

### Router imports

El Router de Angular es un servicio opcional y no es parte del núcleo de Angular. Se encuentra en su propia librería @angular/router.

### Configuration

El router en una aplicación Angular funciona como una instancia de tipo singleton 
A routed Angular application has one singleton instance of the Router service. When the browser's URL changes, that router looks for a corresponding Route from which it can determine the component to display.

A router has no routes until you configure it. The following example creates five route definitions, configures the router via the RouterModule.forRoot method, and adds the result to the AppModule's imports array.