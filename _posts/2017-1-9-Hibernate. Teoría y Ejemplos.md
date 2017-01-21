---
layout: post
title: Hibernate: Teoría y ejemplos
---

Base de datos usada para el artículo: https://github.com/RadW2020/Hibernate-Toma-de-Contacto

Repositorio con el proeycto de Netbeans usado para el anterior artículo y este.


Hablemos de algo de teoría relacionada con Hibernate
## Singleton
Esto es un patron de diseño que garantiza que una clase sólo tenga una instancia y proporciona un punto de acceso global a esta instancia.
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

** Diferencia entre session.get() y session.load() **

Hay mucha teoría y se puede profundizar en los conceptos gracias a enlaces como estos. Pero para simplificar al máximo diremos que el método get devuelve el objeto de la base de datos y el método load() devuelve un objeto proxy con un identificador.
Más en:

http://www.dosideas.com/noticias/java/835-hibernate-y-los-metodos-get-y-load

https://coderanch.com/t/606310/databases/Hibernate-load-confused-Hibernate-Proxies

** ¿Que es un objeto proxy en Hibernate? **

Un proxy es una clase generada dinamicamente por Hibernate para ayudar con la carga perezosa "lazy loading".
Carga perezosa significa que una entidad será cargada solo cuando se acceda a ella por primera vez. Y si esta tiene hijos, y sus hijos mas hijos, estos no se cargarán hasta que se acceda a ellos. Esta práctica evita que grandes bases de datos con objetos con complejas herencias sean cargadas en memoria al completo de primeras. Aumentando considerablemente el rendimiento.

Otra definición mas informal puede ser: Un objeto que no contiene todos los datos que necesitas pero que sabe como obtenerlos.


## Ejemplos Hibernate

`public static void insertaEmp(Empleados emp){
  Session sesion = null;
  try{
      //obtiene una sesion
      SessionFactory sf = HibernateUtil.getSessionFactory();
      //abre la sesion
      sesion = sf.openSession();
      //comienza una transaccion
      Transaction tx = sesion.beginTransaction();
      System.out.println("Inserta un empleado en la tabla Empleados");
      sesion.save(emp);
      tx.commit();            
  } catch (HibernateException hex){
      System.err.println("Error " + hex.getCause() + ", " + hex.getMessage());
  } finally {
      sesion.close();
  }

}`
