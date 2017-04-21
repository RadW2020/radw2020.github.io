---
layout: post
title: Implantar un sistema ERP-CRM (Teoría)
---

_En este artículo quiero aprovechar el material que escribí como trabajo para la asignatura Sistemas de Gestion Empresarial del primer año del Grado Superior en Desarrollo de Aplicaciones Multiplataforma._

_Es un resumen a modo de manual de buenas prácticas sobre la implantación de Odoo en una empresa._

_Para su desarrollo usé los materiales del curso y las referencias bibliográficas reseñadas al final. Espero que sea de vuestro interés_ :)

![](http://openerpspain.com/wp-content/uploads/odoo_new_openerp.png)
Ante la importante tarea de implantar Odoo en una empresa, lo primero que hay que hacer es formarse y documentarse al máximo posible.

Una buena opción es tener un manual personal sobre los pasos a seguir que esté bien estructurado y sea ampliable con el tiempo y la experiencia.

Este manual, inicialmente puede ser un documento personal del técnico encargado de realizar instalaciones de Odoo y posteriormente evolucionar hasta convertirse en un documento base de la empresa que relate los procedimientos a seguir.

Se divide el plan integral de implantación de Odoo en cinco fases:
1. Análisis
2. Diseño
3. Realización
4. Producción
5. Mantenimiento

## FASES DEL PROYECTO
### Fase 1: Análisis (Preparación del proyecto)

En esta primera fase el responsable hace una primera planificación general.

Se ha de definir cuál será el equipo de trabajo. Este equipo estará compuesto, en su versión más simple, por un jefe de proyecto responsable de la implantación de Odoo, y un representante del cliente, al que llamaremos Jefe de Negocio.

Las dos partes tendrán una primera reunión que servirá para definir lo funcionalidad que requiere implantar la empresa.

Este Documento Inicial debe plasmar el alcance del proyecto desde el punto de vista del usuario, que es lo que el cliente espera. Y sobre él debemos trabajar para identificar las necesidades del cliente expresadas en un lenguaje de alto nivel.

También se deben identificar en este documento qué requisitos técnicos debe cumplir la instalación de Odoo. Esto es un análisis de las capacidades técnicas actuales que tiene la empresa, un estudio de la suficiencia de ellas o la posible inversión en hardware que debe hacer el cliente si fuese necesario.

Al finalizar esta fase, después de una o varias reuniones con el cliente, se debe tener información suficiente para elaborar el **Documento de Análisis (DA)** o Plan de Trabajo. Este documento debe ser aprobado por el cliente y debe reunir los siguientes puntos expresados desde el punto de vista del usuario:

- Situación actual de la empresa
-	Solución propuesta
-	Objetivos
-	Alcance tecnológico
-	Posibles estándares industriales relacionados con los procesos
-	Resumen del plan de trabajo

### Fase 2: Diseño

Una vez terminadas las reuniones de trabajo, al inicio de la fase de diseño se ha de elaborar el **Documento de Especificación de Requisitos (DER)**.

Esta lista de requisitos funcionales debe ser completa y estar perfectamente detallada. Ha de validarse por el Jefe de proyecto y por el Cliente durante las reuniones necesarias para ello. El Cliente debe ser conocedor de las repercusiones en inversión o en Recursos humanos que se desprenden de cada requisito funcional aceptado por las dos partes.

Este DER es muy importante ya que equivale a un primer contrato de trabajo donde se puede presupuestar el coste de la implantación, nuestros servicios de consultoría y el mantenimiento.

Una vez validado el DER, este se convertirá en el primer documento técnico. Lo usaremos para detallar la documentación generada en la fase anterior.

El objetivo de esta fase es generar el **Documento de Diseño (DD)**.

Así, por ejemplo, el resumen del plan de trabajo en líneas generales que se generó en la fase de análisis ahora será un calendario exhaustivo de trabajo con fechas concretas.
El apartado de Alcance Tecnológico ha de evolucionar hacia un análisis pormenorizado de la necesidad de inversión (si la hay) que va tener que hacer el cliente para la implantación de Odoo. Por ejemplo, compra de Sistema Operativo, servidores y bases de datos entre otros. También se debe valorar el gasto en Recursos humanos, ya sea nuevos contratos o formación de la mano de obra actual.

Otro apartado importante del DD es el Manual de Operaciones. Partiendo de la experiencia de usuario recogida en la Fase de Análisis, y de los requisitos funcionales establecidos al principio de la Fase de Diseño, se ha de empezar a elaborar este manual, enfocado al cliente, que ha de mantenerse actualizado constantemente para que el cliente pueda ir haciendo pruebas mientras desarrollamos nuestro trabajo, y que no parará de evolucionar hasta la fase de mantenimiento después de la Ejecución.

El grueso del DD lo conforma la lista de módulos de Odoo a implantar. Esta lista de módulos se define para que satisfaga todas las necesidades funcionales establecidas en el DER. Ha de tener na estructura jerarquizada clara y debe representar a la empresa a nivel organizativo.

Esta lista debe ser exhaustiva, módulo a módulo de Odoo, explicando la funcionalidad que cumple, los procesos de negocio que lleva a cabo, el alcance de las modificaciones al código que se van a hacer cuando sea necesario, su instalación y su configuración.

Un ejemplo simplificado de esta lista:

- **D.2.3.2 Módulo “Canales de distribución”**
  - Requisitos: Requisitos R.1.23 y R.1.24
  - Es módulo va tener la función de almacenar y trabajar los datos de los proveedores desde el punto de vista del CRM. Deja de lado todo dato relativo datos financieros o contables y muestra unas funciones adecuadas a la búsqueda de satisfacción del cliente. Datos de contacto del distribuidor, horario de trabajo, canal de comunicación directo con sala de chat y videoconferencia, documentos de Calidad y de protección de datos…
  -	Es un módulo “hijo” de Proveedores donde se simplificará el código y se personalizará a la empresa
  -	Su instalación y configuración en cada equipo lo podrá hacer el técnico designado por el cliente siguiendo las instrucciones del Manual de Operaciones.

En este punto hay que definir qué sistema tratamiento de datos se va a usar. Por ejemplo, si es una Base de datos Relacional SQL, hay que definir si se va a usar PostgreSQL o se va a escoger otra opción.

El DD recogerá el diseño de la Base de Datos, que irá en armonía con la lista de módulos, y que servirá como base para su desarrollo en la siguiente fase.

Finalmente se puede adjuntar a esta fase de diseño, dependiendo de la complejidad del módulo: unos esquemas de la interfaz gráfica, esquemas de flujo de trabajo, flujo de procesos, casos de estudio, experiencia de usuario y gráficos UML de los requisitos más complejos, entre otros.
Una vez completado el DD ha de ser validado punto por punto por parte del cliente.

Resumiendo, al finalizar esta fase debemos tener un DD (aparte del Documento de Análisis) de donde se detallen los siguientes puntos:

-	DER
-	Estudio Tecnológico y de Recursos
-	Manual de Operaciones (en su versión inicial)
-	Módulos a implementar
-	Diagrama de la Base de Datos
-	Esquema de Interfaz de Usuario

### Fase 3: Realización
En esta fase el sistema debe quedar instalado, configurado y documentado según los documentos técnicos desarrollados en las anteriores fases.

Siempre que sea posible se usaran módulos de Odoo ya testeados. Esto reducirá costes y tiempo tanto en codificación como en pruebas.

Se instalará Odoo en el equipo final con los módulos escogidos o modificados por nosotros. Se configurará los datos de localización y otros datos propios de una primera instalación de Odoo.

Se introducirán los Datos Maestros, que son toda la información que el cliente quiere que aparezca en el sistema para que le sea entregado “llave en mano”. Este proceso puede ser muy laborioso y es recomendable que esté ampliamente supervisado por el responsable del cliente o por un representante de los futuros usuarios, incluso representantes de cada departamento si fuera necesario.

Los Datos Maestros están compuestos por una gran cantidad de información confidencial de todos los ámbitos del negocio: ventas, compras, proveedores, clientes, Finanzas, contabilidad, RRHH, Administración, …

Se entregará al cliente una o varias cuentas de administrador y se enseñará a un representante, o varios, del cliente el uso de la plataforma. Este administrador tendrá Control sobre las cuentas de usuario y los permisos de acceso. Deberá comprender el Manual de Operaciones que se hará entrega a la compañía e incluso colaborar en su mejora si fuera necesario ofreciendo retroinformación. En definitiva, debe ser un Usuario suficientemente formado para enseñar al resto de la plantilla la utilización y administración de la nueva plataforma.

Durante esta fase se llevarán a cabo las pruebas necesarias para asegurar el buen funcionamiento de la plataforma.

También se trabajará junto con el cliente para que valide las diferentes versiones del software que se vayan desarrollando.

Esta fase de realización puede ser cíclica. Esto quiere decir que una vez terminada, debe ser validada por el cliente o sujeta a posibles mejoras o cambios. Cada cambio introducido conlleva un refinamiento completo de la fase de diseño, y debe quedar reflejado en toda la documentación relacionada.

Estos ciclos, o refinamientos, tendrán modificaciones progresivamente más pequeñas. Hasta que obtengamos el producto final.

Al finalizar esta fase tendremos:
- [x]	El sistema Odoo instalado y configurado con los módulos elegidos
- [x]	La base de datos implementada y configurada
-	[x] Datos Maestros introducidos al menos hasta un 80%
-	[x] Definición de las Funciones del administrador del sistema
-	[x] Plan de Formación a trabajadores
-	[x] Jerarquía de seguridad de accesos
-	[x] Plan de pruebas de sistema
-	[x] Manual de operaciones
-	[x] Entorno de producción configurado y puesto en marcha


### Fase 4: Producción
En esta fase se terminan las pruebas de sistema, y se verifica la instalación.

  - Se programa una fecha para la puesta en marcha final
  - Se define la política de Backups
  - Se chequea la base de datos y se comprueban los Datos Maestros
  - Se testea el sistema con pruebas de estrés y de volumen
  - Se comprueba la experiencia de usuario final
  - Se entrega la cuenta de administrador de sistema al cliente
  - Se pone en marcha el Plan de Formación a trabajadores
  - Se termina el Manual de Operaciones
  - Se concluye la documentación oficial del proyecto y se prepara para su entrega

Finalmente, cuando la producción llega a su fin, y todo es correcto, se pone en marcha el sistema y se da la orden de uso a todos los empleados de la empresa.

Esta puesta en marcha puede ser en servidores del cliente, o gestionados por terceros en la nube.

Aún pueden quedar trabajo por hacer, como cuellos de botella en la transmisión de datos. Si estas tareas son secundarias y el sistema funciona de manera consistente. Se puede considerar el inicio de la fase de mantenimiento.

### Fase 5: Mantenimiento
Durante esta fase el equipo funciona y hay que centrarse en dar soporte al usuario final.

La formación aún sigue su curso y se considerará terminada cuando los usuarios se hayan enfrentado a los primeros problemas reales y se hayan resuelto con el nuestro soporte.

Se acompañará el cliente en la adaptación al nuevo sistema de gestión.

El mantenimiento también incluye posibles actualizaciones del software.




##### Enlaces bibliografía:
[https://dialnet.unirioja.es/descarga/articulo/2573348.pdf](https://dialnet.unirioja.es/descarga/articulo/2573348.pdf)

[https://books.google.es/books/about/Aproximaci%C3%B3n_a_la_ingenier%C3%ADa_del_softw.html?id=5W-nDAAAQBAJ&redir_esc=y&hl=es](https://books.google.es/books/about/Aproximaci%C3%B3n_a_la_ingenier%C3%ADa_del_softw.html?id=5W-nDAAAQBAJ&redir_esc=y&hl=es)

[http://upcommons.upc.edu/bitstream/handle/2099.1/18382/PFC_Implantaci%20n%20de%20un%20sistema%20ERP%20SAP%20en%20una%20empresa.pdf?sequence=1](http://upcommons.upc.edu/bitstream/handle/2099.1/18382/PFC_Implantaci%20n%20de%20un%20sistema%20ERP%20SAP%20en%20una%20empresa.pdf?sequence=1)

[http://www.anajuaristi.com/como-realizar-el-analisis-inicial-para-implantar-un-erp/85.html](http://www.anajuaristi.com/como-realizar-el-analisis-inicial-para-implantar-un-erp/85.html)

[http://es.openerp.wikia.com/wiki/Como_realizar_el_an%C3%A1lisis_inicial_para_implantar_un_ERP](http://es.openerp.wikia.com/wiki/Como_realizar_el_an%C3%A1lisis_inicial_para_implantar_un_ERP)

[https://es.wikipedia.org/wiki/Sistema_de_planificaci%C3%B3n_de_recursos_empresariales](https://es.wikipedia.org/wiki/Sistema_de_planificaci%C3%B3n_de_recursos_empresariales)
