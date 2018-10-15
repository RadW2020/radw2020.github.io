---
layout: post
title: Inyección de Dependencias en Angular
---

La inyección de dependencias no es ni mas ni menos que pasar la instancia de una clase (un objeto) como argumento del constructor de otra.

Según cada lenguaje de programación o framework esto se puede conseguir de diferentes maneras.

En Angular esto se consigue siguiendo estos pasos:

- Definimos la clase que se va a inyectar. Vamos a suponer que queremos una clase que admita un dato tipo fecha y devuelva esa fecha en formato [YYYY][MM][DD]

``` typescript
export class CustomDateProvider {  
  public formatDate(input: Date): string {
      return "[" + input.getFullYear() + "][" + input.getMonth() + "][" + input.getDay() + "]";
  }
}
```

- Lo siguiente que tenemos que hacer es aplicar el decorador _Injectable_ que nos ofrece el módulo _@angular/core_

``` typescript
import {Injectable} from '@angular/core';

@Injectable()
export class CustomDateProvider {  
  public formatDate(input: Date): string {
      return "[" + input.getFullYear() + "][" + input.getMonth() + "][" + input.getDay() + "]";
  }
}
```

- Una vez lista nuestra clase debemos actualizar el método bootstrap de _main.ts_

``` typescript
import {bootstrap} from '@angular/platform-browser-dynamic';
import {AppComponent} from './app.component';
import {CustomDateProvider} from './svc.date';

bootstrap(AppComponent, [CustomDateProvider]);
```

- Y ya podemos usar nuestra clase inyectable donde queramos. Para ello, en cada módulo que se use hay que:
  
  - Añadir el import que incluya la clase inyectable.
  - Añadir la clase a la lista de _providers_ del decorador de clase.
  - Inyectar una instancia de la clase a través del constructor.

``` typescript
import {Component} from '@angular/core';
import {CustomDateProvider} from './services.date';

@Component({
  selector: 'demo-app',
  templateUrl: 'app/app.component.html',
  providers:  [CustomDateProvider]
})
export class AppComponent {
  public currentDate : string;  
  public constructor(private _dateProvider : CustomDateProvider) {
    this.currentDate = _dateProvider.formatDate(new Date());
  }
}
```


Saludos!