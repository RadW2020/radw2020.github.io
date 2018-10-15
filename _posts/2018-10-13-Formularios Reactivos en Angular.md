---
layout: post
title: Formularios Reactivos en Angular
---

# Reactive Forms
Los _Formularios Reactivos_ nos proveen de una manera de manejar las entradas de datos del usuario cuyos valores cambian en el tiempo.

Cada cambio que ocurre en el formulario devuelve un nuevo estado, lo que ayuda a mantener la integridad del modelo entre cada cambio. Los formularios reactivos están basados en flujos de datos de tipo _Observable_, donde cada entrada y cada valor toman la forma de un flujo de datos que puede ser accedido de manera asíncrona.

|                 |  REACTIVE   |  TEMPLATE-DRIVEN |
|----------|:-------------:|------:|
|                 | Mas explícito, creado en la clase del componente | Menos explícito, creado por directivas |
| Modelo de Datos |	Estructurado  | Desestructurado |
| Predictabilidad | Syncrono      | Asíncrono |
| Validación      | Funciones     | Directivas |
| Mutabilidad     | Inmutable     |	Mutable |
| Escalabilidad   |	Acceso a API de bajo nivel | Abstracción sobre la API |


Los Formularios Reactivos son mas escalables, reusables y fáciles de probar. Cada Elemento de la vista está directamente enlazado al modelo mediante una instancia de **FormControl**. Las actualizaciones de la vista al modelo y del modelo a la vista son síncronas y no dependen de la representación en la Interfaz de Ususario del cliente.

Un ejemplo de flujo de datos de la vista a modelo podría ser:
- El usuario escribe un valor en un campo.
- El elemento del formulario de ese campo emite un evento tipo **"input"** con el último valor.
- El _controlador_ de eventos que está escuchando envía el nuevo valor a la instancia de **FormControl**.
- La instancia de **FormControl** emite el nuevo valor a través del _Observable_  **ValueChanges**.
- Cualquier suscriptor al _Observable_ **ValueChanges** recibe el nuevo valor.

El ejemplo de flujo de datos del modelo a la vista sería:
- Por ejemplo, un método cambia el valor del **FormControl**.
- **FormControl** emite el nuevo valor a través del _Observable_ **ValueChanges**.
- Cualquier suscriptor al _Observable_ **ValueChanges** recibe el nuevo valor.
- El _controlador_ de eventos que está escuchando actualiza el elemento pertinente con el nuevo valor.


## Mutabilidad

Los formularios Reactivos mantienen el modelo de datos con una estructura inmutable. 

Cada vez que se produce un cambio en el formulario, **FormControl** devuelve un nuevo modelo de datos en lugar de actualizar el ya existente.

Incluso cuando no se produce un cambio, el _controlador_ está pendiente de todo lo que sucede en cada elemento del formulario y asigna estados en cada momento. Estos son los mas comunes:

- PRISTINE: el valor del control no ha sido cambiado por el usuario
- DIRTY: el usuario ha modificado el valor del control.
- TOUCHED: el usuario ha tocado el control lanzando un evento _blur_ al salir.
- UNTOUCHED: el usuario no ha tocado y salido del control lanzando ningún evento _blur_.


## Escalabilidad

Si los formularios forman parte central de tu apliación, la escalabilidad es muy importante. Poder **reusar** modelos de formulario entre componentes es esencial.

Los _Formularios Reactivos_ hacen mas fácil la escalabilidad al facilitar el acceso a APIs de bajo nivel y dar acceso síncrono al modelo del formulario.


## Form validation


En un _Formulario Reactivo_ en lugar de ir añadiendo validaciones a cada atributo del _template_,  se añaden funciones directamente Control del Formulario en el componente de la clase. Angular llama cada función de validación cada vez que cambia el valor. 



####  Funciones de validación

Hay dos tipos de Funciones de Validación:
    
- **Síncronas**: Funciones que inmediatamente devuelven el error si lo hay. Se pueden pasar como segundo argumento cuando se instancia un **FormControl**.

- **Asíncronas**: Funciones devuelven una Promesa o un Observable que mas tarde emiten el error si lo hay. Se pueden pasar como tercer argumento cuando se instancia un **FormControl**.


Por razones de rendimiento, Angular solo ejecuta Validaciones asíncronas si todas las Validacines Síncronas han pasado previamente.


#### Validaciones

Se puede hacer uso los _validators_ que nos ofrece Angular por defecto, o si necesitamos nuestra propia validación, podemos definir nuestros propios **Custom Validators**.

Por defecto Angular ejecuta las validaciones cada vez que cambia un valor. Es muy normal que las validaciones asíncronas ejecuten algún tipo de _HTTP request_. Esto puede llevar a un exceso de uso de la API del backend y hay que evitarlo siempre que se pueda.

Para ello se puede cambiar la propiedad **updateOn** a **submit** o **blur** 
