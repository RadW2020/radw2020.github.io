---
layout: post
title: Comunicación entre Componentes en Angular
image: featured_image_com_comp_ang.png
---

Hay varias maneras de hacer que los componentes interactúen entre ellos en Angular. 
Una de ellas es hacer que uno de los componentes emita un evento. Podemos llamar al componente que emite el evento _componente hijo_ y, al componente que escucha el evento emitido lo llamamos _componente padre_.

En Angular esta técnica se aplica de la siguiente manera:

## Construimos un componente hijo

La clase HijoComponent define su atributo _opina_ con el decorador **@Output()**. Este es inicializado como un **EventEmitter** del tipo _boolean_.

Posteriormente, en el método ```voto(opinion: boolean)``` se implementa la funcionalidad de la emisión de su propio argumento como un evento del emisor de eventos ```this.opina.emit(opinion);```

```typescript
import { Component, EventEmitter, Input, Output } from '@angular/core';

@Component({
  selector: 'app-hijo',
  template: `
    <h4>{{nombre}}</h4>
    <button (click)="voto(true)"  [disabled]="haOpinado">a favor</button>
    <button (click)="voto(false)" [disabled]="haOpinado">en contra</button>
  `
})
export class HijoComponent {
  @Input()  nombre: string;
  @Output() opina = new EventEmitter<boolean>();
  haOpinado = false;

  voto(opinion: boolean) {
    this.opina.emit(opinion);
    this.haOpinado = true;
  }
}
```
Vemos en esta imagen, que aparece con el nombre Fulanito, como quedaría este componente representado. Este nombre le ha sido dado por el componente padre mediante una asignación a su propiedad (property binding). 

![](https://i.imgur.com/OTn9POA.png)

También podemos ver como los botones están _disabled_. Esto es porque se le habrá hecho click a alguno de los botones, y por ello el atributo _haOpinado_ ha quedado en _false_.

>  El objetivo de este artículo es entender la emisión de eventos de un  componente a otro, estableciendo una relación de _hijo a padre_. Esto se hace con el decorador **@Output** y con **EventEmitter**. Pero aprovechando el ejemplo, podemos  ver como el componente hijo también es modificado por el padre mediante **@Input**, obteniendo así una comunicación de _padre a hijo_.

## Construimos un componente padre

La relación padre a hijo se determina en este caso por el hecho de que el componente padre es el que invoca el hijo en el template. Esto es, el componente padre hace de marco y aloja a cada una de las invocaciones del componente hijo. 

```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-padre',
  template: `
    <h2>¿Queréis que hagamos una paella?</h2>
    <h3>A favor: {{aFavor}}, En contra: {{enContra}}</h3>
    <app-hijo *ngFor="let hijo of hijos"
      [nombre]="hijo"
      (opina)="cuentaVoto($event)">
    </app-hijo>
  `
})
export class PadreComponent {
  aFavor = 0;
  enContra = 0;
  hijos = ['Fulanito', 'Menganito', 'Zutanito'];

  cuentaVoto(aFavor: boolean) {
    aFavor ? this.aFavor++ : this.enContra++;
  }
}
```
Concretamente en nuestro caso el componente hijo es instanciado tres veces gracias al bucle **ngFor** que itera sobre el array _hijos_.

Haciendo uso de los atributos de **app-hijo**, _nombre_ y _opina_, podemos comunicarnos con él desde el componente padre. 

Por un lado estamos asignando un nombre al componente hijo desde el componente padre al pasar un elemento del array mediante la asignación del atributo **[nombre]** (property binding).

Y por otro lado tenemos el componente hijo comunicándose mediante el evento **$event** que es emitido a través de su generador de eventos **(opina)** (event binding), y que en nuestro caso es usado como argumento en el método _cuentaVoto_

![](https://i.imgur.com/bIGePpb.png)

Nótese que en el caso del property binding, para asignar una información hacia el componente instanciado, el hijo, se usa los corchetes.
Y para el caso del event binding, para extraer información de los eventos emitidos desde el componente instanciado, se usan los paréntesis.

Esto ayuda bastante a identificar rapidamente la estructura de un componente hijo y que opciones de comunicación tenemos.





