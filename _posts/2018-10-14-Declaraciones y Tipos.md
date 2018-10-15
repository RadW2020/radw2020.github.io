---
layout: post
title: Declaraciones y Tipos en Typescript
---

Si conoces algún lenguaje de POO tipado como puede ser Java o C# todo esto te va a parecer tan evidente te será imposible terminar el artículo. De todas formas, a modo ilustrativo, si se va a manejar Typescript es interesante conocer cual es su lugar en el ecosistema Javascript :)

Sirva este repaso a modo de resumen y de toma de contacto.

# Declaraciones de Variables

_let_ y _const_ son dos maneras relativamente nuevas de declarar variables en Javascript. Como Typescript es un Superlenguaje de Javascript los soporta de manera nativa.

Haciendo uso de let  y const estamos tipando los datos con los que trabajamos, así aumentamos el control sobre ellos, reducimos posibles errores y facilitamos la depuración.

### let declarations


```typescript
let hello = "Hello!";
```

Aparentemente se usa igual que el clásico _var_ de javascript. Pero la diferencia clave no está en la sintaxis, sino en cómo se interpreta.

#### Ámbito de bloque

Cuando definimos una variable con _let_ sabemos que el alcance que tendrá está delimitado  por el bloque donde se ha creado.
Las variables definidas con _let_ no son visibles fuera del alcance de su bloque donde han sido creadas.

```typescript
function f(input: boolean) {
    let a = 100;

    if (input) {
        // OK: Aquí se puede acceder a la variable 'a'
        let b = a + 1;
        return b;
    }

    // Error: 'b' no existe aquí
    return b;
    let a; // Terminamos con un SyntaxError.
    var a; // Terminamos con un SyntaxError.
}
```
En este ejemplo las dos variables locales, a y b, tienen alcances diferentes, limitados por sus respectivos bloques.

Cuando nos referimos al alcance que tienen, es a todos los niveles. No se pueden leer ni escribir ni antes de ser creadas ni después de su zona de actuación.

Las variables declaradas dentro de una _catch clause_ se comportan de manera similar.




#### Shadowing

El acto de introducir una nueva variable de un bloque anidado con el mismo nombre que una variable de un bloque superior se llama _shadowing_. Si se hace bien no da ningún error, pero es una práctica a **evitar**, salvo muy contadas excepciones.

```typescript
function sumMatrix(matrix: number[][]) {
    let sum = 0;
    for (let i = 0; i < matrix.length; i++) {
        var currentRow = matrix[i];
        for (let i = 0; i < currentRow.length; i++) {
            sum += currentRow[i];
        }
    }

    return sum;
}
```
Este ejemplo funciona correctamente, aunque lo único que ganamos es que sea mas difícil su lectura.


### const declarations

_const_ es otra manera de declarar una variable. En este caso la estamos declarando como una variable _inmutable_. Su valor es constante en su ámbito.


Se comporta igual que _let_, con la diferencia que una vez declarada no se puede alterar su valor. 

No hay que confundirse con que el valor no pueda ser alterado fuera de la variable.

```typescript
const numLivesForCat = 9;
const kitty = {
    name: "Aurora",
    numLives: numLivesForCat,
}

// Error
kitty = {
    name: "Danielle", // Aquí se pretende cambiar el valor de la _const_ y da error
    numLives: numLivesForCat
};

// todo "ok"
kitty.name = "Rory";
kitty.name = "Kitty";
kitty.name = "Cat";
kitty.numLives--; // Aquí no estamos realmente cambiando el valor de la _const_
```


### Destructuring

#### Array destructuring

La forma mas simple de una Destructuración es con un Array:

```typescript
let input = [1, 2];
let [first, second] = input;
console.log(first); // outputs 1
console.log(second); // outputs 2
```

Esto crea dos nuevas variables _first_ y _second_. Es el equivalente a usar indexado:

```typescript
first = input[0];
second = input[1];
```

Funciona también con parámetros de una función:

```typescript
function f([first, second]: [number, number]) {
    console.log(first);
    console.log(second);
}
f([1, 2]);
```


#### Object destructuring

También se puede destructurar objetos:

```typescript
let o = {
    a: "foo",
    b: 12,
    c: "bar"
};
let { a, b } = o;
```
Esto crea dos nuevas variables: a y b, de o.a y de o.b respectivamente.

Se puede crear una variable con los elementos restantes de un objeto usando ...:

```typescript
let { a, ...passthrough } = o;
let total = passthrough.b + passthrough.c.length;
```

#### Spread

El operador _spread es lo contrario a _destructurar_. Se puede por ejemplo recoger varios arrays en un array tal que:

```typescript
let first = [1, 2];
let second = [3, 4];
let bothPlus = [0, ...first, ...second, 5];
```
Esto da a bothPlus el valor [0, 1, 2, 3, 4, 5]. _First_ y _second_ no cambian, _spread_ hace uso de una copia.

También se puede hacer spread en objetos:

```typescript
let defaults = { food: "spicy", price: "$$", ambiance: "noisy" };
let search = { ...defaults, food: "rich" };
```
Cuando se hace spread se aplica de izquierda a derecha. Esto quiere decir que si algún atributo se sobreescribe, predomina el que se asigna el último.


# Tipos Básicos

### Boolean

El tipo de datos más básico. Tiene dos valores posibles _true_ o _false_.

```typescript
let isDone: boolean = false;
```

### Number
Todos los números en typescript son coma flotante. Los límites que puede representar son -(2<sup>53</sup> - 1) y 2<sup>53</sup> - 1.

También tenemos disponibles _hexadecimal_, _decimal_, _binary_ y _octal_.

```typescript
let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
```
### String

Dato tipo texto. TypeScript admite comillas dobles o simples.

```typescript
let color: string = "blue";
color = 'red';
```

La manera de introducir código en un String es con el carácter (`), y embebiendo la expresión tal que ${ expr }.

```typescript
let fullName: string = `Bob Bobbington`;
let age: number = 37;
let sentence: string = `Hello, my name is ${ fullName }.

I am ${ age + 1 } years old.`;
```
This is equivalent to declaring sentence like so:
```typescript
let sentence: string = "Hello, my name is " + fullName + ".\n\n" + "I am" + (age + 1) + " years old.";
```
### Array

Dos maneras de declarar un array:

```typescript
let list: number[] = [1, 2, 3];
```
y
```typescript
let list: Array<number> = [1, 2, 3];
```
### Tuple

Una Tupla nos permite expresar un array con un número determinado de elementos conocido.

Por ejemplo, podemos querer trabajar con un array que tenga primero un _string_ y después un _number_:

```typescript
let x: [string, number];
x = ["hello", 10]; // OK
x = [10, "hello"]; // Error
```

Se le pueden añadir elementos:

```typescript
x[3] = "world"; // OK, 'string' can be assigned to 'string | number'
```
Pero una vez asignado un tipo, no se puede cambiar.


### Enum

Un _enum_ es un conjunto de valores.

```typescript
enum Color {Red, Green, Blue}
let c: Color = Color.Green;
```

Por defecto su numeración empieza por 0. Podemos cambiar esto de manera manual alterando el primer elemento:

```typescript
enum Color {Red = 1, Green, Blue}
let c: Color = Color.Green;
```
O incluso cambiar el índice de todos los elementos:

```typescript
enum Color {Red = 1, Green = 2, Blue = 4}
let c: Color = Color.Green;
```

### Any

Si necesitamos trabajar con variables cuyo tipo desconocemos, una entrada de datos dinámica  por ejemplo, podemos usar el typo _any_.


```typescript
let notSure: any = 4;
notSure = "maybe a string instead";
notSure = false; // okay, definitely a boolean
```

El tipo _any_ es una herramienta muy poderosa en Javascript. Nos permite definir los tipados de manera gradual en caso de que lo necesitemos.

Es muy útil por ejemplo cuando tenemos un array de valores dispares:

```typescript
let list: any[] = [1, true, "free"];

list[1] = 100;
```

### Void

_void_ es lo contrario de _any_. Se usa principalmente cuando de manera explícita se define una función que no devuelve ningún valor.


### Null and Undefined

Por defecto _null_ y _undefined_ son subtipos de cada uno de los tipos anteriores. Esto significa que podemos asignar _null_ a un _number_ o un _undefined_ a un _string, por ejemplo.


### Never

El tipo _never_ representa el tipo que nunca ocurre.
Esto puede ser el typo de dato que retorna una función que no puede retornar.
Digamos que _void_ representa el conjunto vacío. Pues con _never_ no hay conjunto.


### Object

Un _object_ es un objeto. Un tipo de dato no primitivo.

Todos los _object_ en JavaScript descienden de la clase superior **Object**. Todos los objetos heredan métodos y propiedades de **Object.prototype**, aunque se pueden sobreescribir.

### Type assertions

Es tomar el control y decirle directamente al compilador el tipo de dato que vamos a manejar. Es similar al _cast_ en otros lenguajes.


Se puede hacer de dos maneras: 

```typescript
let someValue: any = "this is a string";

let strLength: number = (<string>someValue).length;
```

o

```typescript
let someValue: any = "this is a string";

let strLength: number = (someValue as string).length;
```
