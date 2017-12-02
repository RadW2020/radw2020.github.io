---
layout: post
title: Hibernate - Un poco de Teoría y ejemplos
---
(Continuación del anterior post)

Base de datos usada para el artículo: [script SQL](https://github.com/RadW2020/Hibernate-Toma-de-Contacto)

Repositorio con el proyecto de Netbeans usado para el anterior artículo y este: [Repositorio Github](https://github.com/RadW2020/Hibernate_Empresaz)



Hablemos de algo de teoría relacionada con Hibernate

## Singleton

Esto es un patrón de diseño que garantiza que una clase sólo tenga una instancia y proporciona un punto de acceso global a esta instancia.
A veces, varios clientes distintos precisan referenciar a un mismo elemento y queremos asegurarnos de que no hay mas de una instancia de ese elemento.
El funcionamiento se podría reducir en los siguientes conceptos:

1. Ocultar el constructor para que los clientes no puedan crear instancias.
2. Declarar en la clase Singleton una variable miembro privada que contenga la referencia a la instancia única que queremos gestionar.
3. Proveer en la clase Singleton una función que brinde acceso a la única instancia gestionada por el Singleton. Los clientes acceden a la instancia a través de esta función o propiedad.

En el tema que nos ocupa, Hibernate, el patrón Singleton debe usarse para implementar objetos tipo SessionFactory. Estos objetos son muy pesados ya que contienen la información de conexión a la Base de Datos, datos de configuración de Hibernate, información de mapeado y rutas.
Por eso se ha de crear una sola instancia de SessionFactory por aplicación.
En resumen, un objeto SessionFactory por aplicación y un objeto Session por cliente.
(Para esta nota final entendemos una aplicación que tiene solo una fuente de datos.)

_Un poco mas de teoría..._

### Diferencia entre session.get() y session.load()

Hay mucha teoría y se puede profundizar en los conceptos gracias a enlaces como estos. Pero para simplificar al máximo diremos que el método get devuelve el objeto de la base de datos y el método load() devuelve un objeto proxy con un identificador.
Más en:

[Hibernate, get() y load()](http://www.dosideas.com/noticias/java/835-hibernate-y-los-metodos-get-y-load)

[Hibernate Proxies](https://coderanch.com/t/606310/databases/Hibernate-load-confused-Hibernate-Proxies)

## ¿Que es un objeto proxy en Hibernate?

Un proxy es una clase generada dinámicamente por Hibernate para ayudar con la carga perezosa "lazy loading".
Carga perezosa significa que una entidad será cargada solo cuando se acceda a ella por primera vez. Y si esta tiene hijos, y sus hijos mas hijos, estos no se cargarán hasta que se acceda a ellos. Esta práctica evita que grandes bases de datos con objetos con complejas herencias sean cargadas en memoria al completo de primeras. Aumentando considerablemente el rendimiento.

Otra definición mas informal puede ser: Un objeto que no contiene todos los datos que necesitas pero que sabe como obtenerlos.


## Ejemplos Hibernate
Estos ejemplos continúan el proyecto del artículo anterior.

Aquí se estan usando los métodos load() y get() desde el mismo main para probar su funcionamiento y diferencias.

![](https://i.imgur.com/GmEQIGr.jpg)

Esta es la salida por consola.

![](https://i.imgur.com/3gtoAv7.jpg)

Método para insertar un empleado en la tabla

![](https://i.imgur.com/ayHyO2W.jpg)

Método que modifica el salario y comisión de un empleado dado su número de identificación.

![](https://i.imgur.com/efqk4og.jpg)

Método para borrar un empleado.

![](https://i.imgur.com/fAwKU04.jpg)


Si encontráis fallos en este código no dudéis en revisar el [repositorio original](https://github.com/RadW2020/Hibernate_Empresaz), seguramente está corregido, actualizado y/o ampliado. Y si no es así sois bienvenidos a modificar lo que queráis ;)


Saludos!
