# PMDM 05
# Creación de videojuegos.

## 1.- Introducción a los videojuegos.


**Podemos definir un videojuego como un juego electrónico que interactúa con uno o varios jugadores con el fin de que se consigan ciertos objetivos y que muestra visualmente una respuesta a sus acciones.**


### 1.1.- Orígenes de los videojuegos.

Es difícil poner una fecha exacta al origen de los videojuegos, pero podemos comenzar en 1947. Fue en ese año cuando se registró una patente en Estados Unidos acerca de un dispositivo de entretenimiento que consistía en disparar a aviones en una pantalla de tubo de rayos catódicos (CRT). Thomas T. Goldsmith, Jr. y Estle Ray Mann aparecen como sus autores. Bien pudieron ser los padres del concepto de videojuego.

### 1.2.- Los videojuegos en la actualidad.

Mucho ha cambiado en el campo desde los tiempos de esos primeros videojuegos. Los de hoy en día pueden llegar a ser auténticas producciones multimillonarias que superan en presupuesto a las grandes películas de Hollywood e involucran a cientos de personas.

Hoy en día, la industria de los videojuegos está centrada en 3 grandes plataformas: los ordenadores personales, las consolas y los dispositivos móviles. 

Por lo general, los saltos tecnológicos aparecen primero en los ordenadores ya que están en permanente evolución y sus posibilidades de expansión permiten la inclusión de nuevos tipos de dispositivos. Eso sucedió es su momento con la introducción de las tarjetas de sonido, los gráficos 3D o las tarjetas de aceleración de cálculos físicos. Las novedades más demandadas pasan poco después al mundo de las consolas. 
Programar para una de estas plataformas implica una serie de ventajas y de inconvenientes respecto a las demás. Veamos algunos aspectos interesantes:

- **Consolas**: Son dispositivos diseñados exclusivamente para ejecutar videojuegos. Su hardware evoluciona con cada iteración (que en ellas se llama "generación"), lo que suele suceder cada varios años. La gran ventaja desde el punto de vista de la programación de videojuegos es que el hardware no varía durante este tiempo lo que permite concentrar los esfuerzos en una única plataforma. 
- **Ordenadores personales**: los ordenadores personales han sido uno de las primeras plataformas en permitir la ejecución de juegos. Los equipos de última generación casi siempre van a superar a las consolas en potencia y memoria ya que adaptan las nuevas tecnologías con mayor velocidad. La cruz de la moneda es que los videojuegos tienen que soportar un abanico muy amplio de hardware 
     
- **Dispositivos móviles**: Si bien hace años que existen las videoconsolas portátiles el concepto ha evolucionado para dar soporte a teléfonos móviles y a otros dispositivos similares 

### 1.3.- Clasificación de los videojuegos.


No existe una clasificación unificada de los géneros de videojuegos, ni siquiera los expertos se ponen de acuerdo.  
Ejemplos: Acción, Aventura, Lucha, FPS, Plataformas, Estrategia, MOBA, MMORPG, Puzle, Simuladores, Sandbox, RPG, Careras, Deportivos, Musical, Minijuegos, Tradicionales, Educativos, Serios.


1.4.- La industria del videojuego.


**El desarrollador (puede ser una empresa o un particular) es el encargado de diseñar e implementar el videojuego**. Suele estar especializado en unos determinados géneros y/o plataformas:

- Un desarrollador interno es el que trabaja siempre para el mismo editor o fabricante de hardware.
- Un desarrollador de terceros firma contratos con los editores para llevar a cabo un proyecto.
- Un desarrollador independiente es un equipo pequeño, puede que incluso unipersonal. Suele autopublicar sus propios juegos y, al no estar atado a un editor, tienen plena libertad creativa.

### 1.4.1.- El equipo de desarrollo.

**Hoy en día lo normal es que un proyecto se lleve a cabo por decenas de personas**. 

La parte del equipo dedicada al diseño suele incluir un **diseñador principal** (en inglés, "Lead Designer").

Debe haber programadores que se encarguen de la creación del código específico. Los equipos de programadores suelen construirse alrededor del **programador principal** (en inglés: "Lead Programmer"), que suele ser el más experimentado. 
Si el tamaño del equipo es grande, puede aparecer el rol de **director técnico** ("Technical Director").

### 1.5.- Motores de juegos.

Hoy en día en la gran mayoría de los videojuegos presentan tres grandes componentes a grandes rasgos: el código específico del juego, el motor de juegos y los recursos.

1. **El código específico** es donde se implementa la lógica de ese juego es particular, es decir, el sitio donde se definen las reglas, el comportamiento de los elementos del juego (por ejemplo, la pelota, los enemigos, etc.), cómo se reacciona ante las posibles acciones del jugador, las condiciones para ganar, etc.
El código específico y los recursos se aplican al motor de juegos para crear el videojuego.
Elaboración propia.
2. El **motor de juegos** contiene la funcionalidad sobre la que se apoya el código específico para realizar esas actividades. Como veremos más adelante, un buen motor de juegos es independiente del tipo de juego que se está implementando y sólo incluye conceptos genéricos como la captura de eventos del teclado/ratón, la gestión de recursos, la visualización de los objetos, las comunicaciones por red, la reproducción de sonidos, etc.

El motor de juegos nos permite abstraernos del hardware del equipo y el sistema operativo, aunque usan sus servicios para llevar a cabo sus funciones. Esto es muy interesante, veamos la razón con un ejemplo: si nuestro motor de juegos soportara 3 clases de consola y 3 sistemas operativos distintos de ordenadores personales, podemos tener un juego funcionando en 6 plataformas con muy poco esfuerzo adicional.

3.) El tercer componente, los **recursos** (o assets, en inglés), es el compendio de los contenidos del juego. Entre esos contenidos podemos encontrar música, efectos de sonido, modelos 3D, fondos de pantalla, tipos de letra, niveles, etc. El motor de juegos cargará los recursos según le indique el código específico. De la creación de los contenidos suelen encargarse los diseñadores artísticos, ingenieros de sonido, escritores, diseñadores de niveles, etc. aunque su desarrollo puede estar supervisado por programadores.

Lo lógico es comenzar seleccionando un motor de juegos.

#### 1.5.1.- Clasificación de motores de juegos.

Un motor de juegos expone una interfaz de programación de aplicaciones (API) que permite al código específico utilizar su funcionalidad. 

**Según el nivel de abstracción cubierto por el motor de juegos, podemos distinguir 3 tipos de complejidad creciente:**

- Motores diseñados únicamente para facilitar la representación en pantalla y el acceso al hardware.
- Motores que, además de lo anterior, añaden un soporte total o parcial a la lógica del juego. 
- Motores que, además de todo lo anterior, incluyen plataformas para la creación, modificación o integración de contenidos. 


Para proyectos personales o no comerciales es posible encontrar motores que no nos supongan ninguna inversión, lo que puede ser determinante. 
 
Teniendo todo esto en cuenta, podemos clasificar los motores en dos grandes grupos según el tipo de licencia de uso:

- **De código abierto**: No es necesario pagar por su uso e incluyen el código fuente del motor. Hay que prestar atención al tipo de licencia concreto, pues algunas restringen el uso del motor a la creación de videojuegos que también sea software libre.
- **Propietario**: Son desarrollados por empresas que cobran por la comercialización de juegos basados en sus motores. En algunos casos pueden ofrecerse de forma gratuita si se cumplen determinadas condiciones. 

##### 1.5.1.1.- Programación de un motor. APIs básicas.

Cada motor soporta solamente determinados lenguajes de programación para el código específico del juego, así que debemos elegirlo con cuidado. 

Un motor de juegos está especializado solamente en determinados aspectos, no todos incluyen las mismas características. De hecho, es posible combinar distintos motores de manera que cada uno aporte parte de la funcionalidad necesaria para completar los requisitos del juego. 

**OpenGL** o **DirectGraphics** suelen utilizarse para mostrar objetos en 2 y 3 dimensiones.

Las librerías no tienen por qué ser exclusivamente para acceder al apartado gráfico: existen muchas otras librerías para otros usos. Por ejemplo, OpenAL o FMOD hace lo mismo con el audio y OpenCL con las operaciones de computación intensiva.

#### 1.5.2.- Ventajas de la utilización de motores.

¿Qué pasaría si no usáramos un motor de juegos? De hecho, los primeros videojuegos no los utilizaban. Cuando esto ocurre, el código específico es el encargado de todas las tareas.

A priori, puede parecer una idea buena porque sólo se implementa aquello que se va a necesitar, con lo que el resultado será más óptimo. Además, el código estará más integrado.

Imaginemos que realizamos el proyecto así. ¿Qué problemas podríamos encontrarnos? Analicemos algunos escenarios posibles:

 
|Ventajas del uso de un motor de juegos Escenarios|	Sin un motor de juegos|	Con un motor de juegos|
|--------------------|---------------------------|-------------------------|
|El juego tiene tanto éxito que nos encargan una continuación.| 	Tendremos que revisar todo el código del proyecto anterior y diferenciando lo que nos sigue sirviendo de lo que no. El motivo es que no hay una separación clara entre lo genérico y lo específico del juego. |	El código del proyecto ya está separado en código específico del juego y el motor (código genérico).
|Hay que migrar el juego a una nueva plataforma. 	|

|No nos queda más remedio que revisar todo el código del proyecto anterior y analizar qué parte es dependiente de la plataforma antigua para sustituirlo por código nuevo. |
	En el momento que el motor de juegos soporte la nueva plataforma bastará con recompilar el proyecto.|
|Llega un nuevo programador a la empresa y queremos formarlo para trabajar en nuestros proyectos.| 	Habrá que explicarle la estructura del código, que será distinta para cada proyecto en el que vaya a trabajar y plataforma soportada.| 	Bastará con enseñarle a usar el motor de juego, que será el mismo en muchos proyectos. |
|Queremos incorporar a nuestro juego el efecto gráfico X de un juego de la competencia.| 	Será necesario investigar cómo funciona la característica X, implementarla en todas las plataformas del proyecto y hacer las pruebas correspondientes antes de usarla. |	Seguramente haya un motor de juego que implemente la característica X de serie en todas las plataformas.|


#### 1.5.3.- Componentes de un motor de juegos.


No todos los motores de juegos tienen las mismas funcionalidades.
, aunque sí existen algunos aspectos que son comunes entre muchos de ellos. 
Componentes más habituales que componen un motor de juegos:

- Motor gráfico 2D
- Motor gráfico o de renderizado 3D
- Detector de colisiones
- Motor de físicas
- Motor de inteligencia artificial (IA)
- Motor de sonidos
- Gestor de comunicaciones en red


##### 1.5.3.1.- Motor gráfico 2D.
 
El número de imágenes por segundo que se crean es un número llamado framerate y se mide en cuadros por segundo (FPS). Para que el ojo no perciba parpadeo, el framerate debe ser superior a 46 FPS.



Los juegos 2D son aquellos en los que los dibujos tienen dos dimensiones, por ejemplo ancho y alto, pero no profundidad. Un motor 2D permite dibujar de forma sencilla figuras geométricas.

Las animaciones en los juegos 2D se producen cambiando el dibujo del sprite rápidamente de manera que haya pequeñas diferencias entre uno y otro, lo que produce en el cerebro una sensación de continuidad.

Los motores gráficos 2D dan soporte a los sprites, ofreciendo herramientas para escalar, rotar y mover objetos por la pantalla con comodidad.

Cuando dos sprites se superponen el resultado final dependerá del orden en que se dibujen. Dicho orden normalmente se denomina plano o capa. 

En algunos motores gráficos podemos representar mundos que sean varias veces más grandes que el tamaño de la pantalla. 

Otro elemento gráfico que poseen muchos motores 2D es el de tilemap (celosía), que es una composición de imágenes pequeñas del mismo tamaño. Este recurso es muy útil para dibujar fondos, mapas y niveles.


##### 1.5.3.2.- Motor gráfico o de renderizado 3D.

Por otro lado, en los juegos 3D los objetos tienen tres dimensiones y, por tanto, pueden moverse en el espacio con total libertad. Esto intenta imitar la visión del ser humano, que también es tridimensional. El problema es que la gran mayoría de los monitores sólo son capaces de representar imágenes 2D. Para solucionarlo podemos realizar una operación llamada proyección, que transforma esa imagen 3D en una 2D. Ese proceso de generar las imágenes recibe el nombre de renderizado y es tarea del motor gráfico.

Normalmente, los objetos 3D están constituidos por vértices que juntos forman polígonos, generalmente de tres o cuatro lados.

Sobre los polígonos se pueden aplicar texturas para darle un aspecto más realista. 

Un motor gráfico 3D simplificará el trabajo con los objetos tridimensionales permitiendo al código específico realizar operaciones con ellos independientemente del hardware sobre el que se esté ejecutando el juego. Entre estas operaciones está la de crear objetos, moverlos, escalarlos, rotarlos, deformarlos, animarlos, cambiarles las texturas, etc. Además, deberá soportar la creación de luces que iluminen dichos objetos y cámaras que permitan observar el mundo renderizado desde la perspectiva que necesitemos en cada momento.

El conjunto de todos los objetos de este mundo virtual junto con las cámaras, las luces y demás elementos forman la escena. Internamente, la escena se suele almacenar mediante el denominado grafo de escena que se estudiará más adelante.


##### 1.5.3.3.- Detector de colisiones.

Una de las acciones que realizaremos más frecuentemente es comprobar si dos objetos colisionan entre sí. Por ejemplo: nos interesará saber si una bala ha chocado contra un enemigo o si nuestro coche ha llegado a la meta. Ahí es donde entran los detectores de colisiones.

Detectar colisiones no es nada fácil, especialmente en ciertas circunstancias. En el caso 2D, dos objetos no han colisionado hasta que tienen un punto (píxel) en común. **Podríamos simplificar el proceso de detección** de una colisión suponiendo que hay un círculo o una caja que envuelve cada objeto y comprobar si dichas figuras geométricas se superponen. El problema es que pueden darse falsos positivos de colisión.
 


Si el motor hace bien su trabajo, cuando las figuras geométricas colisionen realizará un estudio más cuidadoso en la zona superpuesta para saber si efectivamente han chocado; de esta forma podemos solucionar los falsos positivos.

Algunos detectores de colisiones clasifican los objetos en tipos de manera que sólo comprueban ciertas combinaciones. Por ejemplo: las colisiones de los objetos tipo "bala" con los tipo "enemigo" sí se comprueban, pero las colisiones de los objetos tipo "enemigo" con otros tipo "enemigo" no. Esto permite ahorrar mucho tiempo de cálculo.

##### 1.5.3.4.- Motor de físicas.

Muchos de los videojuegos intentan dotar a los objetos que aparecen de un comportamiento creíble. Esto es, si empuja un objeto hacia el borde una mesa, el jugador espera que el objeto caiga al suelo. Si se golpea un cristal, esperamos que se haga añicos. O si lanzo golpeo una pelota, espero que siga una trayectoria natural y al llegar a la pared rebote de una forma natural.

Todos **estos comportamientos son calculados por el motor de físicas** y pueden ir desde dotar de un efecto de gravedad al escenario donde estamos jugando hasta el cálculo de la dirección que tomarán dos objetos al chocar, calcular por donde discurre un líquido derramado, por donde se romperá un objeto al golpearlo o que al tirar de una cuerda se mueva un objeto que está atado al otro extremo. De hecho, en **entornos 3D suele ser el motor de físicas el encargado de detectar las colisiones entre objetos**. Para poder realizar todas estas actividades el motor asignará una serie de propiedades físicas a cada objeto (velocidad, aceleración, masa, etc.) y aplicará las ecuaciones de la **física newtoniana**.

**Los cálculos de este tipo de motores requieren un uso intensivo del procesador**. Es por ello que hace unos años surgieron tarjetas aceleradoras de física, que permitían dejar libre la CPU para otras tareas. En los últimos años la tendencia es que las GPU asuman estas funciones.) estaba dedicado solamente a realizar cálculos de simulaciones físicas. Poco después se trasladó esa funcionalidad a las propias GPU de las tarjetas gráficas, ya que éstas son capaces de realizar millones de cálculos por segundo en paralelo.

##### 1.5.3.5.- Motor de inteligencia artificial (IA).

Los jugadores esperan que los enemigos que aparezcan en el videojuego le supongan un desafío. De lo contrario, rápidamente se perdería el interés por jugar. Es ahí donde entra el **motor de inteligencia artificial** (IA) cuya misión es la de proveer a algunos de los elementos del juego de un comportamiento que parezca ser inteligente. Dada la complejidad de algunos de los problemas que soluciona el motor de IA y teniendo en cuenta que la **toma de decisiones tiene que hacerse en muy poco tiempo**, la mayoría de las veces se opta por usar técnicas simples y rápidas.

Un recurso muy utilizado para simular comportamientos sería el uso de máquinas de estados finitos. Su aplicación permite que un objeto se comporte de forma distinta según la situación. Por ejemplo: un guardia puede estar vigilando una zona y, en caso de detectar al jugador, dejaría inmediatamente esa tarea para proceder a perseguirlo. Si lo perdiera de vista, volvería a su tarea original. Al personaje del juego que no está bajo control directo del ordenador se le denomina NPC (personaje no jugador) y suele ser controlados por la  IA.


##### 1.5.3.6.- Motor de sonidos.

Es el encargado de controlar la reproducción de música y efectos de sonido de manera sincronizada con el resto del juego. El código específico puede disponer de esta funcionalidad de forma independiente al hardware de la plataforma. Esto quiere decir que si, por ejemplo, el hardware no soportara la reproducción de más de un sonido a la vez, el motor podría realizar la mezcla él mismo para producir el mismo efecto sin tener que cambiar el código específico.

**Tanto la música como los efectos de sonido son parte de los recursos del juego**. Ambos pueden incluirse como partitura (usando archivos MIDI) o bien de forma digitalizada, ya sea grabada directamente del mundo real o modificada con algún editor de audio como el de la figura.

Los motores de sonido pueden ser muy complejos: algunos tienen conexiones con el motor de físicas para cambiar las características del sonido según la situación. Por ejemplo, podría producir un **efecto doppler** (el que hace que sepamos si una ambulancia está acercándose o alejándose simplemente por el sonido que emite). También, otros pueden distorsionar el sonido para **simular la acústica** de una sala o de un corredor, dotando de más realismo al juego.

Por último, algunos motores permiten generar **sonido posicional en 3D**.

##### 1.5.3.7.- Gestor de conexiones en red.

Este gestor nos permite que nuestro juego no esté aislado y pueda comunicarse con otros sistemas. El uso más obvio es la creación de juegos multijugador, pero no es el único.

Otros escenarios que pueden resolverse con este componente son:

- Subida de la puntuación de la partida a un servidor Web o a una red social.
- Descarga de actualizaciones del juego.
- Implementación de salas para poder seleccionar contrincantes.
- Comunicaciones de voz y/o de texto entre varios jugadores.


Muchos de los gestores de conexiones en red facilitan la creación de juegos multijugador a través de un servidor. 

La forma de implementar el multijugador varía de un motor a otro. Algunos usan la arquitectura cliente/servidor, de manera que todos las instancias de juego se conectan a un mismo servidor, que recibe los datos de cada cliente y los reenvía a los demás. Otros usan una arquitectura distribuida o P2P (de igual a igual) donde todos se comunican directamente con todos, aunque sólo suele usarse en redes de área local donde eso no supone una penalización de rendimiento.
Para saber más


#### 1.5.4.- Librerías que dan soporte a los motores.

Librerías más utilizadas respecto al aspecto gráfico:

- **DirectGraphics (DirectDraw y Direct3D)**: son librerías de Microsoft. Las dos librerías forman parte de la colección de API DirectX. 
- **OpenGL**: es la librería gráfica 2D y 3D más utilizada. Se soporta en múltiples sistemas operativos y plataformas. 
- **OpenGL ES**: es una versión reducida de OpenGL dirigida a dispositivos empotrados o con poca potencia. Suele ser la librería utilizada en las plataformas móviles.

Respecto al audio:

- **DirectSound y DirectSound 3D**: también forman parte de DirectX. La primera de ellas, especializada en audio 2D. Sólo funcionan en software o hardware de Microsoft.
- **OpenAL**: es la equivalente de OpenGL en audio, es decir, tiene soporte multiplataforma, integrándose muy bien con la librería gráfica. Soporta efectos especiales avanzados.

Otras librerías interesantes:

- **OpenCL**: es una librería estándar de programación paralela. Puede usarse para motores de físicas o para motores de IA.

Y por último, librerías que ofrecen funcionalidad combinada:

- **SDL (Simple DirectMedia Layer)**: ofrece una interfaz de programación multiplataforma muy sencilla para acceder a los dispositivos gráficos (2D) y de sonido. Además, permite gestionar los dispositivos de entrada, como joysticks, gamepads, teclados, pantallas táctiles y ratones.
- **Allegro**: similar a SDL, aunque incorpora soporta 3D (sin aceleración, de forma limitada).

## 2.- Desarrollando juegos con libGDX.
Caso práctico

Juan quiere ponerse ya manos a la obra y empezar a utilizar los nuevos conceptos de una forma práctica. Para ello es imprescindible decantarse por un motor de juegos 2D que se ajuste a sus necesidades,
Imagen de búsqueda simple en internet.
 bnielsen Simple Globe Search

pues dependiendo de su elección tendrá a su disposición un determinado conjunto de herramientas u otro. Dado que ya tiene experiencia previa trabajando con el entorno Android Studio, decide restringir la búsqueda del motor a aquellos que funcionen correctamente con esta plataforma de desarrollo. Tras indagar durante un rato en Internet y leer páginas de comentarios en unos cuantos foros, decide finalmente probar con libGDX.

Existe una gran cantidad de motores 2D, algunos de los cuáles son de código abierto, otros simplemente gratuitos y, cómo no, también de licencia comercial. Es posible encontrar motores que incorporan sus propios lenguajes de programación y editores de recursos integrados en un entorno de desarrollo. Otros son simplemente librerías que se pueden usar en los entornos de desarrollo que nosotros queramos. No menos importante es tener en cuenta la cantidad y fecha de sus últimas actualizaciones, pues muchos motores llevan meses o años abandonados a su suerte.

Como imaginarás, la elección de un motor depende aún de muchos otros factores:

    Lenguaje de programación a usar.
    Plataformas a las que queremos destinar el producto final.
    Características técnicas que nos ofrece, etc.

En nuestro caso vamos a continuar en la línea de usar Java como lenguaje de programación y utilizaremos como entorno de desarrollo el ya conocido AndroidStudio, aunque complementado con otras herramientas externas que nos pueden facilitar el trabajo (editores de mapas, etc.)

Es conveniente recordar que los conceptos básicos son similares en la gran mayoría de motores, así que lo que aprendamos a lo largo de esta unidad será aplicable a otros, independientemente del lenguaje de programación o de las herramientas que tenga disponibles.

Con el fin de aprender todos estos conceptos usaremos LibGDX, un motor de juegos 2D y 3D multiplataforma, que utiliza Java como lenguaje soporte, y que permite generar proyectos para una amplia base de plataformas, entre ellas, plataformas de escritorio, como Windows o Linux, plataformas móviles, como pueden ser Android e IOS, y plataformas web, todo ello partiendo de la base del mismo código para todas y cada una de dichas plataformas.

¿List@ para comenzar la aventura de construir tu propio videojuego?
2.1.- Introducción a LibGDX.
Logotipo de libGDX
Badlogic Games English: This is libGDX logo

libGDX, es un framework (marco de desarrollo) multiplataforma de desarrollo de juegos y gestión de visualización, para Windows, Linux, Mac OS X, Android, Blackberry, iOS y HTML5. Está escrito en Java con una mezcla de C/C++ para dar soporte y rendimiento a tareas relacionadas con el uso de la física y procesamiento de audio. De esta forma, sólo tendremos que preocuparnos por la parte que codificaremos en lenguaje Java, mientras el framework se encarga de empaquetar todo el código nativo de nuestras aplicaciones.

Otra de las características interesantes de libGDX, es que te permite escribir, probar y depurar nuestra aplicación en el ordenador personal y utilizar el mismo código para el resto de plataformas. Esto se debe a que uno de sus objetivos principales, es proporcionar una arquitectura unificada para trabajar, garantizando el mismo comportamiento en todas las plataformas para las cuáles hayas creado el juego en cuestión. Aún sí, hay ciertas cosas que debemos tener en cuenta cuando estemos trabajando en un mismo juego para PC y para Android, ya que el rendimiento puede ser muy bueno en el ordenador de escritorio y muy malo en Android u otras plataformas, ya que las diferencias de hardware pueden llegar a ser muy importantes.

libGDX también nos permite utilizar rutinas de bajo nivel cada vez que lo necesitemos, con las que podremos acceder directamente al sistema de archivos, dispositivos de entrada, audio y OpenGL a través de un interfaz unificado para OpenGL ES v2.0 y v3.0. Por encima de esas herramientas de bajo nivel, se ha construido un conjunto muy potente de APIs, que nos ayudarán en las tareas más comunes relacionadas con el desarrollo de juegos, como puede ser la representación de los sprites y el texto, construir el interfaz de usuario, reproducir música y efectos de sonido, realizar cálculos algebraicos y trigonométricos, trabajar con JSON y XML y un largo etcétera.

El framework proporciona un entorno para el prototipado e iteración rápidos. En lugar de desplegar a todas las plataformas, tras cada cambio en el código, podemos ejecutar y depurar el juego en nuestro ordenador de escritorio de forma nativa. La máquina virtual de escritorio tiene características, como hotswapping de código, que reduce considerablemente el coste en tiempo de cada iteración en el desarrollo, ya que permite ver el efecto de un cambio en el código Java en una aplicación que ya esté en ejecución, sin tener que volver a compilar la misma. Esta característica no se encuentra disponible en plataformas móviles, por lo que siempre será preferible realizar el desarrollo de la aplicación sobre la versión de escritorio y así poder aprovechar esa ventaja fundamental.
Recomendación

Puedes visitar la galería de juegos realizados con libGDX, para hacerte una idea de lo que puedes llegar a hacer con este framework, aunque ten en cuenta que juegos avanzados, incluso con soporte 3D, suelen requerir de la intervención de equipos de desarrollo compuesto con perfiles diferenciados, grafistas, programadores, músicos, etc.

Galería de juegos realizados con libGDX.
2.1.1.- Herramientas que forman LibGDX.

Como ya se ha mencionado, LibGDX está compuesto por una serie de librerías y herramientas que nos permiten confeccionar aplicaciones multimedia y juegos en particular. Las herramientas, entre otras, son las siguientes:

    Un modulo de aplicación que nos permitirá manejar el ciclo de vida (creación, pausa, reanudación y destrucción) de nuestra aplicación.
    Un módulo de gráficos que nos proporciona una forma de dibujar objetos en la pantalla.
    Un módulo de audio para reproducir música y efectos de audio.
    Un módulo de entrada para recibir toda la información del usuario proveniente del ratón, teclado, pantalla táctil, acelerómetro, etc.
    Un módulo de acceso a ficheros para leer y escribir datos como texturas, mapas o archivos de configuración.
    Un módulo de red, que nos permitirá acceder a recursos en red y manejar sockets para implementar aplicaciones con características cliente/servidor.

Imagen que muestra los módulos que componen, de forma estándar, LibGDX, junto con sus interrelaciones.
Elaboración propia (CC BY-NC)

A parte de estos módulos, podríamos añadir dos más:

    Math, permite la gestión rápida de cálculos matemáticos orientados al desarrollo de videojuegos.
    Physics, que básicamente es una envoltura de Box2D y permite controlar la gestión de colisiones y efectos de física, para dotar de interacción realista a los objetos.

En el siguiente diagrama, pueden verse como se interrelacionan estos módulos:
Diagrama que describe las interacciones entre los distintos componentes de LibGDX
badlogicgame (Apache 2.0 license)

En cualquier caso, las posibilidades de este framework no se reducen a estas que se han expuesto, ya que permite su ampliación mediante el uso de plugins o añadidos, y se trata de un proyecto Open Source completamente vivo y con una comunidad de desarrollo y apoyo muy activa.
Para saber más

Si quieres saber más posibilidades del mismo, puedes visitar este enlace, donde se muestran todas y cada una de las características del mismo.

Página oficial de LibGDX (en inglés).
2.1.2.- Configurando Android Studio.
Anagrama de Android Studio
Google Inc. - Android.com Android Studio product icon

Para desarrollar nuestras aplicaciones LibGDX con Android Studio, necesitaremos las siguientes herramientas:

    Java Development Kit 7+ (JDK), en nuestro caso usamos la versión 8.
    Android Studio, que ya tiene integrado el Android SDK, por lo que no necesitaremos descargarlo.

Además, si queremos desarrollar para IOS o MacOSX

    Un ordenador con MacOSX, el desarrollo para iOS Development no funciona en Windows/Linux “gracias” a Apple.
    La última versión XCode, que podemos obtener desde la App Store gratis.
    Y una de estas dos alternativas: el plugin  RoboVM IntelliJ IDEA plugin from MobiDevelop's site o Intel Multi-OS Engine.

2.1.3.- Generando un proyecto con LibGDX.

Una vez tengamos convenientemente instaladas y configuradas estas herramientas, podemos pasar a crear nuestro proyecto libGDX. Para poder generar un proyecto, LibGDX nos proporciona una utilidad, denominada gdx-setup.jar,. Esta utilidad puede ejecutarse en tanto en entorno gráfico, como en línea de comando. Podemos descargar la utilidad desde este enlace.

Para lanzar la herramienta en el entorno gráfico, simplemente deberemos ejecutar el archivo a través de nuestra JVM. Una vez en ejecución se nos muestra la siguiente ventana:

Ventana que muestra las distintas opciones en la generación de un proyecto LibGDX
Elaboración propia. (CC BY-ND)

En el cuadro de diálogo que se nos muestra, tendremos que especificar el nombre de nuestra aplicación, el nombre del paquete Java para la misma, el nombre de la clase principal, el directorio de destino donde se guardará el proyecto al generarlo, y la ruta al SDK de Android. También podremos seleccionar las plataformas que queremos que nuestra aplicación soporte, teniendo en cuenta que, una vez generado el proyecto, si queremos añadir nuevas plataformas, tendremos que hacerlo manualmente.
Por último, podremos seleccionar las extensiones que queremos incluir en nuestra aplicación. Hemos de tener en cuenta que algunas de ellas puede que no funcionen correctamente en todas las plataforma, aunque se nos avisará sobre ese extremo y así tomemos la decisión oportuna al respecto.
Una vez tengamos todo bien configurado, podremos pulsar el botón "Generate", para generar la aplicación, tras lo cual, el asistente comienza la generación del proyecto. En caso de que la versión del Android SDK sea distinto al "recomendado", se nos muestra un mensaje de advertencia. En principio podemos ignorarlo y decir que siga adelante.
Tras un periodo de tiempo relativamente largo, ya que es posible que el asistente tenga que descargar determinadas librerías y archivos desde Internet, cuando se termine la generación del proyecto, se indica que se ha generado correctamente el proyecto, el tiempo que ha tardado en generarse y la forma como importarlo dependiendo del IDE que utilicemos.
Diálogo que muestra el mensaje de que la generación del proyecto libGDX se ha relizado de forma satisfactoria.
Elaboración propia. (CC BY-NC)

Autoevaluación
Pregunta 1

Cuando creamos un proyecto con el generador de proyectos LibGDX, las plataformas a las que queremos dar soporte debemos añadirlas de forma manual siempre:

Verdadero Falso
2.1.4.- Importando el proyecto en Android Studio.
Captura de la pantalla de bienvenida de AndroidStudio, donde se mos muestra el listado de los proyectos recientemente abiertos y las distintas opciones que podemos utilidar.
Elaboración propia. (CC BY-NC)

Al terminar la generación del proyecto libGDX, el siguiente paso para poder continuar con el desarrollo de nuestra aplicación será importar el mismo en nuestro IDE, desde el que realizaremos la implementación, depuración y despliegue de la misma. En nuestro caso usamos Android Studio, para lo que seleccionaremos la opción “Import project”.
Captura de la pantalla de bienvenida de AndroidStudio, donde se mos muestra el listado de los proyectos recientemente abiertos y las distintas opciones que podemos utilidar.
Elaboración propia. (CC BY-NC)

Vamos a la carpeta donde se ha generado el proyecto libGDX y seleccionamos el archivo build.gradle y pulsamos el botón "Ok", tras lo que sse mostrará un cuadro de diálogo de progreso para el proceso de importación, el cual puede tardar unos minutos en completarse, ya que se tienen que comprobar todas las dependencias y puede que tengan que descargarse determinados archivos desde Internet.

Al terminar el proceso de importación, puede que nos aparezca una ventana indicando que el plugin de Gradle del proyecto es antiguo y nos pregunte si queremos actualizarlo, seleccionamos que queremos actualizar y tras unos breves instantes, acabará el proceso:
Ventana que muestra un mensaje indicando que es recomendable actualizar la versión de Gradle del proyecto que estamos importando.
Elaboración propia. (CC BY-NC)

Tras actualizar el plugin de Gradle del proyecto, este se nos muestra en el IDE de Android Studio, y podemos observar la estructura de carpetas del proyecto, una por cada una de las plataformas para las que lo hemos generado, y una común, denominada "core", que incluye el código fuente común para cada una de ellas.
Ventana de inicio del IDE Android Studio que muestra los distintos subproyectos para los que se ha generado el proyecto libGDX, así como el lanzador principal de la aplicación.
Elaboración propia. (CC BY-NC)

Como puede observarse en la pantalla anterior, aparece un subproyecto común, denominado "core", que contendrá el código Java común para el resto de subproyectos, así como 4 subproyectos más: uno para "android", otro para "desktop", otro para "html" y, finalmente, otro para "ios", correspondiendo cada uno de ellos con las plataformas para las que hemos generado el proyecto libGDX.
Debes conocer

Dentro de la carpeta "android" hay, entre otras, una carpeta que se denomina "assets", en la que deberemos incluir todos los recursos gráficos, sonidos, fondos de pantalla, sprites, etc..., que vayamos a usar en nuestra aplicación, y que será compartida con el resto de subproyectos generados.Captura de pantalla del árbol de carpetas que tiene el subproyecto "android", destacando la carpeta "assets"
Elaboración propia. (CC BY-NC)
2.1.4.1.-Ejecutando el proyecto en Android Studio.

Una vez hemos importado el proyecto en Android Studio, podremos ejecutar el mismo para las diversas plataformas para las que hemos generado el mismo. En el siguiente vídeo puedes ver como hacerlo y el resultado.
jotajotavm. LIBGDX para Android - Tutorial 04 - Como ejecutarlo en tu Telefono - How to make games Android (Licencia de YouTube estándar)

Autoevaluación
Pregunta

Cuando importamos un proyecto en Android Studio, al ejecutar el mismo para las diferentes plataformas, podemos afirma que:
Respuestas

Opción 1

Para ejecutar el proyecto para Android, simplemente tendremos que ejecutar el subproyecto asociado, el cual se lanzará en el emulador.

Opción 2

Al lanzar el proyecto para "desktop" este se ejecuta correctamente sin que tengamos que hacer nada en la configuración del mismo.

Opción 3

La primera vez que pulsamos el botón de ejecución del proyecto en Android Studio, se lanza el subproyecto "desktop" de forma automática.

Opción 4

La primera vez que pulsamos el botón de ejecución del proyecto en Android Studio, se lanza el subproyecto "android" de forma automática.

2.1.5.- Sistema de coordenadas.
Diagrama que muestra cómo se especifican las coordenadas en libGDX: el eje X es positivo del origen hacia la derecha, y negativo del origen hacia la izquierda. El eje Y es positivo desde el origan hacia arriba, y negativo desde el origen hacia abajo. El origen, por tanto, es el punto (0,0).
K. Bolino - https://es.wikipedia.org/wiki/Archivo:Cartesian-coordinate-system.svg (CC0)

Para que podamos informar al motor de la posición de los objetos es necesario que tanto el motor como el código específico use el mismo criterio. En este caso, el criterio se denomina sistema de coordenadas y es, ni más ni menos, la forma de expresar un lugar en un plano 2D. Como tiene dos dimensiones, cualquier punto puede indicarse con un par de números que denominaremos coordenadas.

libGDX usa un sistema de coordenadas cartesiano clásico (X,Y) donde la esquina inferior izquierda del contenedor es la posición (0,0). El primer número expresa la componente horizontal, mientras que el segundo es la componente vertical. Los valores negativos serán a la izquierda y hacia abajo respecto a dicha esquina, mientras que los positivos serán hacia la derecha y hacia arriba.

2.2.- Ciclo de vida de una aplicación LibGDX.

Una aplicación libGDX cuenta con ciclo de vida bien definido, que maneja los estados en los distintos estados en los que se encuentre, esto se realiza mediante los eventos que se definen en la interfaz ApplicationListener. De esta forma, el punto de entrada para una aplicación libGDX debería ser una clase que implemente dicha interfaz, y que será en la que se implemente la mayoría del código de la aplicación. Podemos ver en el siguiente código:

public class MiJuego implements ApplicationListener {
   public void create () {
   }

   public void render () {        
   }

   public void resize (int width, int height) { 
   }

   public void pause () { 
   }

   public void resume () {
   }

   public void dispose () { 
   }
}

El significado de cada uno de los métodos anteriores podemos verlo en la siguiente tabla:
Métodos de la interfaz ApplicationListener Método	Descripción
void create() 	Este método se ejecuta una sola vez, cuando se crea la aplicación. Es el punto de entrada de la misma.
void resize(int width, int height) 	Se llama a este método cada vez que la pantalla del juego cambia su tamaño y el juego no está en el estado de pausa. También se le llama sólo una vez justo después del método create(). Los parámetros son la nueva anchura y altura de la pantalla.
void render() 	

Método llamado por el bucle del juego de la aplicación cada vez que se tiene que actualizar su representación. La actualización del juego también tiene lugar aquí antes de la representación real.
void pause()
	El método de pausa se ​llama ​justo antes que se destruya la aplicación. Además, en Android se llama cuando se pulsa el botón de inicio o haya una llamada entrante. En el escritorio se llama justo antes de dispose() al salir de la aplicación. Es un buen lugar para guardar el estado del juego en Android, ya que no se garantiza que sea reanudado.
void resume()
	Este método es llamado sólo en Android, cuando la aplicación recibe el foco y en él sería recomendable recuperar el estado del juego, en caso de haberlo hecho previamente al ejecutarse el método pause(). En el resto de plataformas, este método no será llamado nunca.
void dispose() 	Este método se ejecuta cuando vamos a destruir la aplicación. Siempre es precedido por una llamada al método pause().


Ya sabemos que si una clase usa una interfaz, tiene que implementar de forma obligada todos y cada uno de los métodos que dicha interfaz especifica, pero puede darse el caso de que no queramos utilizar todos los métodos anteriores. En estos casos, en lugar de implementar la interfaz ApplicationListener, podremos hacer que nuestra clase principal herede de la clase ApplicationAdapter. En el siguiente código podemos ver un ejemplo tomado de la propia aplicación generada por el generador de libGDX:

public class MiJuego extends ApplicationAdapter {
	SpriteBatch batch;
	Texture img;
	
	@Override
	public void create () {
		batch = new SpriteBatch();
		img = new Texture("badlogic.jpg");
	}

	@Override
	public void render () {
		Gdx.gl.glClearColor(1, 0, 0, 1);
		Gdx.gl.glClear(GL20.GL_COLOR_BUFFER_BIT);
		batch.begin();
		batch.draw(img, 0, 0);
		batch.end();
	}

        @Override
	public void dispose () {
		batch.dispose();
		img.dispose();
	}
 }


Independientemente de si implementamos la interfaz ApplicationListener o si heredamos de ApplicationAdapter el ciclo de vida de nuestras aplicaciones libGDX es el que se muestra a continuación:
Diagrama que describe las interacciones entre los distintos componentes de LibGDX
badlogicgame (Apache 2.0 license)

Debes conocer

libGDX está orientado a eventos, ya que esta es la forma natural del comportamiento de Android y JavaScript. Esto implica que no existe un bucle principal explícito para los juegos realizados con libGDX. Sin embargo, podemos asimilar el método ApplicationListener.render() como el cuerpo de ese bucle principal que podemos encontrar en las aplicaciones realizadas con otros motores de juegos.
2.2.1.- Las clases de lanzamiento.

Ya hemos visto que los proyectos libGDX comparte un código común, el cual se ubica en el subproyecto core, y para cada una de las plataformas existe un subproyecto en el cual se aloja el código específico para cada una de ellas. La clase en la que se ubica dicho código específico para cada plataforma, se denomina "starter class" o clase de lanzamiento y se ubica dentro de cada subproyecto específico. Así, para cada plataforma soportada por nuestro juego, estas clases de lanzamiento instanciarán una versión específica de la aplicación.

Así, por ejemplo, para la plataforma desktop, la clase de lanzamiento básica creada por el generador de libGDX, es similar a esta:

public class DesktopLauncher {
   public static void main(String[] argv) {
      LwjglApplicationConfiguration config = new LwjglApplicationConfiguration();
      new LwjglApplication(new MiJuego(), config);
   }
}


El el caso de la clase de lanzamiento para Android, tendremos el siguiente código por defecto:

public class AndroidLauncher extends AndroidApplication {
   public void onCreate(Bundle bundle) {
      super.onCreate(bundle);
      AndroidApplicationConfiguration config = new AndroidApplicationConfiguration();
      initialize(new MiJuego(), config);
   }
}

2.3.- Creando un juego básico con libGDX.
Caso práctico

Juan ya lo tiene todo preparado: ha creado el primer proyecto libGDX en su ordenador y echado un primer vistazo a la documentación. En unas horas, se reunirá con Ana para abordar juntos el aprendizaje de los elementos que componen un juego 2D. Su idea es realizar un prototipo sencillo de juego, donde un personaje animado se mueva por un mapa. Mientras que Juan se encargará de la parte de programación, Ana realizará el diseño del mapa y de los personajes usando herramientas específicas que previamente le enseñarán a usar.
Un hombre y una mujer situados sobre un dibujo circular con los puntos cardinales.
 Marine Institute.
Línea de salida de una carrera en el preciso momento que comienza.
 Deniz Alkac.

A lo largo de este apartado echaremos un vistazo a los elementos típicos de un juego 2D y cómo se pueden utilizar con LibGDX. Partiremos de un proyecto vacío al que iremos incorporando código y recursos.

Inicialmente nuestro juego será un simple mapa al que posteriormente añadiremos un personaje que se puede mover por él. Para darle más realismo, haremos que dicho personaje realice una animación mientras se desplaza. Por último, conseguiremos que el personaje reaccione con algunos elementos, como el borde del mapa u obstáculos que encuentre por el camino.

Todo ello se verá de una forma muy práctica, así que deberías seguir todas las explicaciones en un ordenador que tenga instalado el IDE AndroidStudio y el motor LibGDX, tal y como se explicó en el apartado anterior. Ten en cuenta que, por falta de tiempo, no vamos a ver todas las posibilidades de libGDX, sino que vamos a ver algunas de sus características más básicas, aunque estas servirán de base para que puedas continuar el aprendizaje de este framework.

¿Preparad@? ¿List@? ¡Ya!
2.3.1.- Creando el proyecto del juego.

El juego que vamos a realizar utilizará un mapa de baldosas (tiledmap) por el que se desplazará un personaje. En principio el tamaño de la ventana del juego será de 800 puntos horizontales y 480 verticales, y con un título de la ventana "Hora de aventuras", lo que implicará que tendremos que realizar determinadas tareas previas sobre las clases de lanzamiento de las diversas plataformas a las que va destinado el juego.
Pantalla del generador de proyectos LibGDX.
Elaboración propia. (CC BY-NC)

Si no lo tienes listo aún, genera un proyecto nuevo libGDX, siguiendo los pasos vistos anteriormente (java -jar gdx-setup.jar), para el que se usarán los siguientes parámetros:

    Nombre de aplicación: mijuego
    Nombre del paquete: com.pmdm.migame
    Clase del juego: MiJuego
    Plataformas: Desktop, Android, Html

Una vez terminado el proceso de generación del proyecto, podremos recuperarlo en nuestro entorno de desarrollo, en nuestro caso Android Studio, siguiendo las instrucciones que hemos visto en un apartado anteriores, con lo que ya estemos en condiciones de empezar nuestro recorrido.

Como recordarás, del generador de libGDX crea la clase principal como una subclase de la clase ApplicationAdapter. Esta clase nos permite implementar sólo algunos de los métodos de la interfaz ApplicationListener,  y en el caso del generador libGDX, se implementa en la clase principal del juego los métodos create() y render(), el resto de métodos de dicha interfaz sólo los implementaremos si son necesarios.

Veamos como realizar la adaptación de las clases de lanzamiento para que en todas las plataformas se adapte a la resolución deseada de la ventana del juego.

Recuerda que para poder generar un subproyecto IOS, debes disponer de un ordenador con MacOSX, en caso de no disponer de él, es inútil generar el subproyecto para esta plataforma.
2.3.1.1.- Configurando el lanzador para escritorio.

En este caso, la configuración es bastante simple y para indicar el tamaño y título de la ventana, basta con realizar lo siguiente:

public class DesktopLauncher {
	public static void main (String[] arg) {
		LwjglApplicationConfiguration config = new LwjglApplicationConfiguration();
		//Indicamos el título de la ventana del juego.
		config.title = "Hora de aventuras";
		//Indicamos la anchura de la ventana del juego.
		config.width = 800;
		//Indicamos la altura de la ventana del juego.
		config.height = 480;
		//Lanzamos el juego en su versión de escritorio.
		new LwjglApplication(new MiJuego(), config);
	}
}

2.3.1.2.- Configurando el lanzador para Android.

En este caso, tendríamos que adaptar la clase lanzadora y, en su caso, el fichero de configuración de Android, el manifiesto. En este último caso, habría que modificarlo para indicar si queremos que el juego se ejecute en vertical (portrait) o en apaisado (landscape), siendo esta última la modalidad que se genera por defecto por el generador de proyectos libGDX. Así, AndroidManifest.xml quedaría de esta forma:


<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.pmdm.migame"
    android:versionCode="1"
    android:versionName="1.0" >

    <!-- en el caso de mi Sdk uso la 25, puedes poner la 23 o la que uses -->
    <uses-sdk android:minSdkVersion="8" android:targetSdkVersion="25" />

    <application
        android:allowBackup="true"
        android:icon="@drawable/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/GdxTheme" >
        <activity
            android:name="com.pmdm.migame.AndroidLauncher"
            android:label="@string/app_name" 
            android:screenOrientation="landscape"
            android:configChanges="keyboard|keyboardHidden|orientation|screenSize">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>


Por último, en el caso de la clase lanzadora, quedaría de la siguiente forma:

public class AndroidLauncher extends AndroidApplication {
	@Override
	protected void onCreate (Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		AndroidApplicationConfiguration config = new AndroidApplicationConfiguration();
		//Deshabilitamos el uso del acelerómetro y la brújula.
		config.useAccelerometer = false;
		config.useCompass = false;
		//Lanzamos el juego.
		initialize(new MiJuego(), config);
	}
}

Debes conocer

En este caso no podemos indicar la resolución ya que esta es definida de forma automática por el propio sistema operativo Android, por lo que nuestro juego se reescalará de forma automática a la resolución del dispositivo en el que se ejecute.
2.3.1.3.- Configurando el lanzador para HTML.

En este caso, la configuración es también bastante simple y para indicar el tamaño y título de la ventana, basta con realizar lo siguiente en la clase lanzadora que podremos encontrar en el subproyecto html:

public class HtmlLauncher extends GwtApplication {

        @Override
        public GwtApplicationConfiguration getConfig () {
                return new GwtApplicationConfiguration(800, 480);
        }

        @Override
        public ApplicationListener createApplicationListener () {
                return new MiJuego();
        }
}

2.3.2.- Tilemaps (mapas de baldosas).
Reflexiona
¿Te imaginas la cantidad de espacio que sería necesaria para almacenar un juego con decenas o incluso centenas de pantallas distintas? ¿Cómo es posible que existan juegos de los años 80 con esas extensiones de terreno para explorar si los ordenadores apenas tenían unos pocos kilobytes de memoria?

El truco es que no se almacenan las pantallas como un gráfico normal sino como una composición de trozos predefinidos que se colocan cuidadosamente unos junto a otros para dar sensación de que forman un todo continuo. En realidad, lo que se almacena en memoria son las referencias de cada trozo y esas referencias pueden ocupar cientos o miles de veces menos que el trozo en sí mismo. Vaya ahorro, ¿no?

Observa la siguiente imagen que contiene trozos de una vía del tren y otros elementos decorativos:
Tileset que contiene piezas para formar vías de tren con formas complejas.
Recorte de una sección de la imagen: Zeronomous.

Está compuesta de trozos de 32x32 píxeles, cada uno de los cuáles se denomina baldosa, aunque el término más utilizado cuando hablamos de videojuegos es su traducción al inglés: tile. Puedes ver los tiles separados aquí:
Tileset que contiene piezas para formar vías de tren con formas complejas al que se han separado los tiles por una línea divisoria.
Recolocación de los tiles en la imagen original y superposición de una rejilla: Zeronomous.

 
Una captura de pantalla del editor de tilemaps Tiled.
Captura de pantalla de la aplicación Tiled bajo licencia
GNU GPL v2. Tiles que componen la imagen obtenidos de:
 Zeronomous.

Como ves, los tiles son dibujos normalmente cuadrados que suelen ir almacenados todos juntos en una única imagen. Esas imágenes se llaman tilesets, o conjunto de baldosas. Normalmente, los tilesets son procesados directamente por el motor 2D de manera que se "trocean" internamente para poder dibujar los tiles independientemente. Parte del dibujo de un tile puede ser transparente, lo cual será útil cuando vayamos a superponerlo encima de otro tile para hacer efectos visuales.

Para crear mapas o pantallas complejas se suele usar un editor de mapas de baldosas (editor de tilemaps) que permite usar este tipo de imágenes y colocar unos con otros los elementos de forma sencilla, incluso superponiendo unos encima de otros mediante capas. Un ejemplo de este tipo de programas es Tiled, aunque algunos motores incorporan un editor propio. Aprenderemos a usarlo en el próximo apartado.
Autoevaluación

Rellena los huecos con el término inglés que corresponda:

En los juegos 2D, la creación de mapas o pantallas completas se suele realizar con un editor de
Rellenar huecos (1):
, al cuál tenemos que proporcionar una o varias imágenes denominadas
Rellenar huecos (2):
que están compuestas de trozos cuadrados de imágenes que llamamos
Rellenar huecos (3):
o baldosas.

2.3.2.1.- Creando tilemaps con Tiled.
na captura de pantalla del editor de tilemaps Tiled.
Captura de pantalla de la aplicación
Tiled bajo licencia GNU GPL v2.
Tiles que componen la imagen obtenidos de:
 Zeronomous

Tiled es un editor de tilemaps, es software libre y muy versátil. Es multiplataforma, existiendo versiones para Windows, Linux y MacOS X.

Crear un tilemap con Tiled es similar a componer un collage. Podemos crear tantas capas de tiles como necesitemos. Las capas se dibujarán en orden, pudiendo mezclar unos dibujos con otros hasta conseguir el efecto deseado.

Por ejemplo: podemos dibujar los tiles que representan el suelo en la capa inferior, los árboles, paredes y demás objetos que podamos encontrar en otra capa y los tejados en la última. Dado que luego, desde el motor, podemos ocultar y mostrar las capas mediante código, podríamos ocultar el tejado cuando nuestro personaje se introduzca en una casa y volverlo a mostrar cuando salga.

Tiled nos facilita la importación de tilesets y la edición de los mapas mediante múltiples herramientas: relleno, copiado y pegado de grupos de tiles, etc. Otra de sus funciones destacables es que permite añadir atributos a los distintos elementos del mapa. Por ejemplo, si cierto tipo de tile impide el paso del jugador, podemos marcarlo con un atributo. Dichos atributos pueden ser leídos luego desde el motor de una forma sencilla.
Debes conocer

Puedes descargar Tiled para tu sistema operativo desde su página oficial.

Página oficial de Tiled.
¿Quieres echar un vistazo a su funcionamiento? ¡Bien! Observa el siguiente vídeo.
Debes conocer

Este vídeo explica las funciones básicas de Tiled, así como el flujo de trabajo. Échale un vistazo para aprender algunos trucos.

Prueba a hacer tú otro mapa similar con el mismo tileset, que puedes descargar aquí:
Tileset variado. (3,7 MB)

Llama al mapa mapatutorial.tmx y guárdalo en la carpeta misma carpeta donde tengas el tileset (esto es importante, luego veremos el motivo). Luego pasaremos ambos archivos a la carpeta data de nuestro proyecto.
Recuerda

Tal y como se comenta en el vídeo, si quieres que el tilemap, luego se pueda leer sin problemas desde LibGDX, no te olvides de cambiar en las preferencias del programa la opción “Almacenar la capa de patrones como: Base64 (con compresión gzip)”, salvo que desees desplegar la aplicación para HTML5, en cuyo caso deberías usar el formato Base64 sin comprimir, ya que el motor que da soporte a HTML5 en libGDX no soporta la compresión que realiza Tiled y se produciría un error al intentar ejecutar la aplicación tras realizar el despliegue de la misma. A partir de ese momento, todos los mapas que guardes podrán abrirse sin problemas.
Autoevaluación
Pregunta

¿Cuáles de las siguientes afirmaciones son correctas acerca del trabajo con Tiled? (Pista: marca 3):
Respuestas

Opción 1

Las acciones de cortar y pegar afectan a todas las capas.

Opción 2

Colocar un tile en una capa sustituye solamente al tile de la capa actual, no a los de las demás capas.

Opción 3

Se recomienda guardar el mapa en la misma carpeta que el tileset.

Opción 4

El aleatorizador coloca tiles en capas elegidas al azar.

Opción 5

La herramienta de relleno llena un área vacía con los tiles seleccionados.

2.3.2.2.- Dibujando tilemaps en libGDX.

Si no tienes abierto el proyecto que creamos en el apartado 2.3.1, ábrelo, ya que lo necesitarás para seguir a partir de aquí.

Lo primero que tendremos que hacer es incluir en la carpeta "assets" del subproyecto android, el tilemap que creamos en el paso anterior, junto con todas las imágenes o tilesets utilizadas para generarlo:
Captura que muestra el árbol del subproyecto android, con el tilemap y los tileset usados para crear el mismo, en la carpeta assets.
Elaboración propia. (CC BY-NC)

Respecto al código, empezaremos por declarar una variable que luego hará referencia al tilemap que acabamos de crear en un apartado anterior. La declararemos dentro de la clase MiJuego:, la cual se encuentra en el subproyecto  core .

public class MiJuego extends ApplicationAdapter {
	//Objeto que recoge el mapa de baldosas
    	private TiledMap mapa;
    	//Objeto con el que se pinta el mapa de baldosas
    	private TiledMapRenderer mapaRenderer;

 

Es en el método create() donde deben cargar los assets del videojuego, será ahí donde indicaremos a libGDX que asocie el tilemap a dicho objeto:

    @Override
    public void create() {
	// más adelante se añadirá código adicional

        //Cargamos el mapa de baldosas desde la carpeta de assets
        mapa = new TmxMapLoader().load("mapatutorial.tmx");
        mapaRenderer = new OrthogonalTiledMapRenderer(mapa);

    }

 
Reflexiona

¿Recuerdas que antes te pedimos que grabaras el mapa en la misma carpeta que el tileset? Eso evita problemas ya que la ruta hasta el tileset se almacena en el fichero del mapa como una ruta relativa a él: poniendo todo en la misma carpeta siempre lo encontrará.

 

El siguiente paso es mostrar el mapa, o usando el término técnico, renderizarlo, pero como paso previo, deberemos añadir un objeto cámara a nuestro proyecto, de esta forma, la clase principal de nuestro juego quedaría como se muestra a continuación:

public class MiJuego extends ApplicationAdapter {
    //Objeto que recoge el mapa de baldosas
    private TiledMap mapa;
    //Objeto con el que se pinta el mapa de baldosas
    private TiledMapRenderer mapaRenderer;
    // Cámara que nos da la vista del juego
    private OrthographicCamera camara;

    @Override
    public void create() {
        //Inicializamos la cámara del juego
        float anchura = Gdx.graphics.getWidth();
        float altura = Gdx.graphics.getHeight();

        //Creamos una cámara y la vinculamos con el lienzo del juego.
        //En este caso le damos unos valores de tamaño que haga que el juego
        //se muestre de forma idéntica en todas las plataformas.
        camara = new OrthographicCamera(800, 480);
        //Posicionamos la vista de la cámara para que su vértice inferior izquierdo sea (0,0)
        camara.position.set(camara.viewportWidth / 2f, camara.viewportHeight / 2f, 0);

        camara.update();

        //Cargamos el mapa de baldosas desde la carpeta de assets
        mapa = new TmxMapLoader().load("mapatutorial.tmx");
        mapaRenderer = new OrthogonalTiledMapRenderer(mapa);
    }

    @Override
    public void render() {
        //Ponemos el color del fondo a negro
        Gdx.gl.glClearColor(0, 0, 0, 1);
        //Borramos la pantalla
        Gdx.gl.glClear(GL20.GL_COLOR_BUFFER_BIT);

        //Actualizamos la cámara del juego
        camara.update();
        //Vinculamos el objeto de dibuja el TiledMap con la cámara del juego
        mapaRenderer.setView(camara);
        //Dibujamos el TiledMap
        mapaRenderer.render();
    }
}

 

Al ejecutar el proyecto en su versión "desktop" obtendremos el siguiente resultado:
Pantalla del juego que muestra unos cactus, algunas piedras, un barril, oro y herramientas para extraerlo y unas vías de tren.
Elaboración propia. (CC BY-NC)

¡Esto va tomando forma!, pero hay un problema: el mapa no se mueve. En el siguiente apartado vamos a indicar el código que haría falta para poder desplazarnos por el mapa, moviendo para ello la cámara.
2.3.2.3.- Desplazando el tilemap (I). Traslaciones.

Vamos a darle un poco de movimiento al mapa. Lo haremos usando el método camara.translate() cuyo efecto es desplazar la vista de la cámara, según las parámetros que pasemos. Este método, tiene dos parámetros que se corresponden con el desplazamiento horizontal (X) y vertical (Y) que queramos aplicar. Dado que la ausencia de desplazamiento se corresponde (0,0):

    Cualquier valor negativo en el desplazamiento X hará que la pantalla se desplace más a la izquierda.
    Cualquier valor positivo en el desplazamiento X hará que la pantalla se desplace más a la derecha.
    Cualquier valor negativo en el desplazamiento Y hará que la pantalla se desplace más hacia abajo.
    Cualquier valor positivo en el desplazamiento Y hará que la pantalla se desplace más hacia arriba.

Así, por ejemplo, si ejecutamos la siguiente instrucción, camara.translate(200, 300), la pantalla se desplazaría 200 píxeles a la derecha y 300 píxeles hacia arriba. Puedes ver a continuación el efecto que tendría esta traslación en el juego, respecto a la pantalla que se mostraba en el apartado anterior:
Pantalla del juego que muestra unos cactus, algunas piedras, un barril, oro y herramientas para extraerlo y unas vías de tren.
Elaboración propia. (CC BY-NC)

Pero lo que queremos es movernos libremente por el mapa y tendremos que saber donde situar este tipo de código. Para ello tendremos que tener en cuenta que para movernos, tendremos que usar la entrada del usuario y, en función de esta, realizar las traslaciones adecuadas. Esto implica que, en los métodos en los que se recoja dicha entrada del usuario, será donde situemos las sentencias de traslación de la cámara del juego, tal como veremos en el siguiente apartado.

Otro método relacionado que te puede resultar de utilidad alguna vez es rotate(angulo), también de la clase Camera. El parámetro es el ángulo en grados de la rotación a realizar.
Autoevaluación
Pregunta

Si llamamos al método camara.translate(0,-100) la sensación que tendrá el jugador es que el mapa del juego:
Respuestas

Opción 1

Se ha desplazado hacia la derecha.

Opción 2

Se ha desplazado hacia la izquierda.

Opción 3

Se ha desplazado hacia arriba.

Opción 4

Se ha desplazado hacia abajo.

2.3.2.4.- Desplazando el tilemap (II). Respondiendo a la entrada de usuario.

Ya tenemos un mecanismo para desplazar el mapa, haciendo que se traslade la cámara, pero ahora tenemos que ver como responder, en este caso, cuando el usuario pulse determinadas teclas, haga click con el ratón o toque la pantalla, y que la cámara se desplace en la dirección adecuada.

Para poder realizar esto, tenemos que hacer que nuestra clase principal implemente la interfaz InputProcessor, que cuenta con los siguientes métodos:

public class MyInputProcessor implements InputProcessor {
   public boolean keyDown (int keycode) {
      return false;
   }

   public boolean keyUp (int keycode) {
      return false;
   }

   public boolean keyTyped (char character) {
      return false;
   }

   public boolean touchDown (int x, int y, int pointer, int button) {
      return false;
   }

   public boolean touchUp (int x, int y, int pointer, int button) {
      return false;
   }

   public boolean touchDragged (int x, int y, int pointer) {
      return false;
   }

   public boolean mouseMoved (int x, int y) {
      return false;
   }

   public boolean scrolled (int amount) {
      return false;
   }
}


El significado de cada uno de los métodos anteriores podemos verlo en la siguiente tabla:
Métodos de la interfaz InputProcessor Método   	Descripción
boolean keyDown(int keycode)
	Este método se ejecuta cada vez que se presiona una tecla del teclado.
boolean keyTyped(char character) 	Se ejecuta este método cada vez que se teclea una tecla del teclado y, como consecuencia, se genera un carácter Unicode.
boolean keyUp(int keycode) 	

Se ejecuta cuando libera (se deja de presionar) una tecla del teclado.
boolean mouseMoved(int screenX, int screenY) 	Se ejecuta cuando se mueve el puntero del ratón por la pantalla, sin que se pulse un botón del mismo.
boolean scrolled(int amount) 	Se ejecuta cuando se utiliza la rueda de desplazamiento del ratón.
boolean touchDown(int screenX, int screenY, int pointer, int button) 	Se ejecuta cuando se pulsa un botón del ratón o cuando se toca la pantalla táctil.
boolean touchDragged(int screenX, int screenY, int pointer) 	Se ejecuta cuando se desplaza el dedo por la pantalla o el puntero del ratón mientras se pulsa un botón.
boolean touchUp(int screenX, int screenY, int pointer, int button) 	Se ejecuta cuando se suelta un botón del ratón o cuando se deja de tocar la pantalla táctil.


Dependiendo de los distintos eventos que queramos controlar, introduciremos el código necesario en los métodos adecuados anteriormente mostrados. Vamos a ver como podemos gestionar, en primer lugar, los eventos de teclado, y después los eventos de ratón y toque de pantalla para desplazar la vista de la cámara.
Para saber más

También se puede tratar la entrada del usuario mediante el módulo "Input" de libGDX, aunque en este caso el tratamiento no está orientado a eventos y la respuesta a las interacciones del usuario con el juego deben hacerse en el método render() de la aplicación. Puedes ver más sobre esta forma de interactuar en el siguiente enlace la documentación oficial de libGDX:

Input Handling (En inglés)
2.3.2.4.1.- Respondiendo al teclado.
Vista de la parte superior de un teclado numérico con las luces de bloqueo encendidas.
Ysangkok. (CC0)

Para tratar adecuadamente las entradas desde el teclado, por parte del jugador, tendremos que usar alguno de estos tres métodos:

    keyDown().
    keyUp().
    keyTyped().

En el caso del código que puedes ver a continuación, se utiliza keyUp() para manejar las teclas pulsadas por el usuario, que pueden ser los cursores, para desplazar la vista de la cámara en la dirección adecuada, los números 1 ó 0 para alternar la visibilidad de la primera o segunda capa, respectivamente, del mapa de baldosas del juego:

    @Override
    public boolean keyUp(int keycode) {
        //Si pulsamos uno de los cursores, se desplaza la cámara
        //de forma adecuada.
        if(keycode == Input.Keys.LEFT)
            camara.translate(-32,0);
        if(keycode == Input.Keys.RIGHT)
            camera.translate(32,0);
        if(keycode == Input.Keys.UP)
            camara.translate(0,32);
        if(keycode == Input.Keys.DOWN)
            camara.translate(0,-32);
        //Si pulsamos la tecla del número 1, se alterna la visibilidad de la primera capa
        //del mapa de baldosas.
        if(keycode == Input.Keys.NUM_1)
            mapa.getLayers().get(0).setVisible(!mapa.getLayers().get(0).isVisible());
        //Si pulsamos la tecla del número 2, se alterna la visibilidad de la segunda capa
        //del mapa de baldosas.
        if(keycode == Input.Keys.NUM_2)
            mapa.getLayers().get(1).setVisible(!mapa.getLayers().get(1).isVisible());
        return false;
    }

¡Ya podemos darnos una vuelta por el mapa usando el teclado!, en el siguiente apartado veremos como hacerlo usando el ratón o el toque de pantalla.
Debes conocer

Si has observado el código anterior, los desplazamientos a la derecha, izquierda, arriba o abajo, se producen en una cantidad de 32 píxeles, ya que ese es el tamaño de las baldosas del mapa.
2.3.2.4.2-. Respondiendo al ratón y al toque de pantalla.
Icono de tocar la pantalla con un dedo.
Gnome.org (GNU/GPL)


En este caso, al hacer clic en la pantalla o tocarla, queremos desplazar la vista de la cámara en la dirección adecuada. Para ello tenemos a nuestra disposición los siguientes métodos:

    touchDown().
    touchUp().
    touchDragged().
    mouseMoved().
    scrolled().

En el siguiente código, vamos a utilizar el método touchDown() para tratar las pulsaciones del teclado o toques de pantalla y desplazar el foco de la cámara hacia la dirección adecuada en función de donde se haya realizado tal evento:

    @Override
    public boolean touchDown(int screenX, int screenY, int pointer, int button) {
        int incrementox=0, incrementoy=0;
        //Si tocamos a la derecha de la posición de la cámara,
        //se mueve esta 32 pixels a la derecha.
        if (camara.position.x<screenX){
            incrementox = 32;
            //Si tocamos a la izquierda de la posición de la cámara,
            //se mueve esta 32 pixels a la izquierda.
        } else if(camara.position.x>screenX){
            incrementox = -32;
        }
        //Si tocamos por encima de la posición  de la cámara,
        //se mueve esta 32 pixels arriba.
        if (camara.position.y<screenX){
            incrementoy = 32;
            //Si tocamos por debajo de la posición  de la cámara,
            //se mueve esta 32 pixels abajo.
        } else if(camara.position.y>screenX){
            incrementoy = -32;
        }
        camara.translate(incrementox,incrementoy);
        return true;
    }

Debes conocer

Si analizas el código anterior, puedes observar que los desplazamientos de la cámara se realizan en bloques de 32 píxeles, y que el desplazamiento puede realizarse arriba/abajo y derecha/izquierda de forma simultánea. En el siguiente enlace tienes el proyecto Android Studio para que puedas comprobar su funcionamiento en este punto del desarrollo del juego.

Código fuente de la clase MiJuego.java (java - 4.66 KB).
2.3.3.- Sprites.
Imagen que contiene los frames de animación de 12 personajes de fantasía medieval.
 Antifarea. Procedencia.

Ya tenemos un fondo en nuestro contenedor que somos capaces de desplazar a nuestra voluntad, pero sin elementos que pueblen el mapa, se muevan por él e interactúen entre sí no podemos hacer gran cosa. Es ahí donde entra el concepto de sprite, palabra anglosajona que podría traducirse por duende o hada, y que no es más que un dibujo 2D que puede colocarse en la pantalla y ser manipulado como una entidad independiente.

 

Los sprites suelen describirse de forma similar a un tilemap en el sentido que todas las imágenes que pueden representar su estado (corriendo, saltando, parado, agachado, etc.) están juntas en una imagen más grande. El motor del juego se encargará de alternar entre una u otra imagen en función de las instrucciones del código específico. A este concepto se le llama animación y permite dar una sensación más natural al sprite.

Fíjate en la diferencia entre tilemap y sprite: ambos son gráficos que se pueden desplazar, pero su concepción y utilización son muy distintas. Mientras un tilemap se considera una especie de fondo de pantalla compuesto de imágenes pequeñas que se colocan unas junto a otras los sprites son elementos que se mueven por él y cuya imagen puede cambiar.

Los motores 2D suelen estar optimizados para mostrar un gran número de sprites simultáneamente en el contenedor. Piensa que cada jugador, cada enemigo e incluso cada bala es un sprite que se puede mover y animar de forma independiente a los demás.

¡Aprendamos a usarlos a nuestros proyectos!
2.3.3.1.- Creando un sprite estático.

Vamos a incorporar un personaje a nuestro mapa: un mosquetero. Nuestro sprite no estará animado por ahora, ya lo resolveremos más adelante.
Imagen fija de un mosquetero pixelado mirando al frente.
Recorte de un fragmento de la imagen:
 InsaneJP.

Descarga el fichero siguiente, cópialo con el nombre mosquetero1.png a la carpeta assets de tu subproyecto android, ya que lo vas a necesitar para poder utilizar el código que viene a continuación.
Sprite de un mosquetero. (0,001 MB)

Para poder usar un sprite en nuestro juego, empezaremos por crear una serie de atributos nuevos en la clase principal:

public class MiJuego extends ApplicationAdapter implements InputProcessor{
    // Objeto que recoge el mapa de baldosas
    private TiledMap mapa;
    // Objeto con el que se pinta el mapa de baldosas
    private OrthogonalTiledMapRenderer mapaRenderer;
    // Cámara que nos da la vista del juego
    private OrthographicCamera camara;
    // Atributo en el que se cargará la imagen del mosquetero.
    private Texture img;
    // Atributo que permitirá la representación de la imagen de textura anterior.
    private Sprite sprite;
    // Atributo que permite dibujar imágenes 2D, en este caso el sprite.
    private SpriteBatch sb;


Como podemos ver, se han creado tres nuevos atributos: el primero de la clase Texture nos permitirá cargar la imagen que se mostrará en el sprite, el segundo es el propio sprite y se trata de un objeto de la clase es Sprite, por último el tercero es un objeto de la clase SpriteBatch, el cual nos va a permitir dibujar adecuadamente en la pantalla el propio sprite. Los objetos son creados en el método create() de nuestra clase principal. Puedes ver cómo en el siguiente trozo de código, que muestra como quedaría dicho método:

    @Override
    public void create() {
        // Ponemos el tamaño del mapa de baldosas
        float anchura = 1000;
        float altura = 1000;

        //Creamos una cámara y la vinculamos con el lienzo del juego.
        //En este caso le damos unos valores de tamaño que haga que el juego
        //se muestre de forma idéntica en todas las plataformas.
        camara = new OrthographicCamera(800, 480);
        //Posicionamos la vista de la cámara para que su vértice inferior izquierdo sea (0,0)
        camara.position.set(camara.viewportWidth / 2f, camara.viewportHeight / 2f, 0);
        //Indicamos que los eventos de entrada sean procesados por esta clase.
        Gdx.input.setInputProcessor(this);

        camara.update();

        // Cargamos la imagen del mosquetero en el objeto img de la clase Texture.
        img = new Texture(Gdx.files.internal("mosquetero1.png"));
        // Asignamos la imagen al objeto sprite para que pueda ser presentada en pantalla.
        sprite = new Sprite(img);
        // Creamos el objeto SpriteBatch que nos permitirá representar adecuadamente el sprite
        // en el método render()
        sb= new SpriteBatch();

        // Cargamos el mapa de baldosas desde la carpeta de assets
        mapa = new TmxMapLoader().load("mapatutorial.tmx");
        mapaRenderer = new OrthogonalTiledMapRenderer(mapa);

    }


También vamos a cambiar la respuesta a los clic de ratón y toque de pantalla, que ahora cambian el valor de la posición del jugador y no el desplazamiento global del fondo. Para poder hacer esto, y que el sprite sea representado adecuadamente respecto a al cámara, se deben transformar las coordenadas donde se haya producido el clic o toque de pantalla, a las coordenadas válidas de nuestra cámara. Esto se realizar usando el método unproyect() de la clase Camera. También hemos modificado la forma como se reacciona a las teclas de los cursores, para que también afecten al mosquetero y no al fondo. Puedes ver como se hace en el siguiente código, que muestra como quedaría el método touchDown() y el método keyUp():


    @Override
    public boolean touchDown(int screenX, int screenY, int pointer, int button) {
        // Vector en tres dimensiones que recoge las coordenadas donde se ha hecho clic
        // o toque de la pantalla.
        Vector3 clickCoordinates = new Vector3(screenX,screenY,0);
        // Transformamos las coordenadas del vector a coordenadas de nuestra cámara.
        Vector3 position = camara.unproject(clickCoordinates);
        // Mostramos el sprite en la posición adecada respecto a nuestra cámara.
        sprite.setPosition(position.x, position.y);
        return true;
    }

    @Override
    public boolean keyUp(int keycode) {
        //Si pulsamos uno de los cursores, se desplaza el sprite
        //de forma adecuada un pixel.
        if(keycode == Input.Keys.LEFT)
            sprite.translate(-1,0);
        if(keycode == Input.Keys.RIGHT)
            sprite.translate(1,0);
        if(keycode == Input.Keys.UP)
            sprite.translate(0,1);
        if(keycode == Input.Keys.DOWN)
            sprite.translate(0,-1);
        //Si pulsamos la tecla del número 1, se alterna la visibilidad de la primera capa
        //del mapa de baldosas.
        if(keycode == Input.Keys.NUM_1)
            mapa.getLayers().get(0).setVisible(!mapa.getLayers().get(0).isVisible());
        //Si pulsamos la tecla del número 2, se alterna la visibilidad de la segunda capa
        //del mapa de baldosas.
        if(keycode == Input.Keys.NUM_2)
            mapa.getLayers().get(1).setVisible(!mapa.getLayers().get(1).isVisible());
        return false;
    }


Por último, el sprite es mostrado en el método render() y, para ello, usaremos el objeto de la clase SpriteBatch  que creamos anteriormente. Podemos ver como hacerlo en el siguiente código:


    @Override
    public void render() {
        //Ponemos el color del fondo a negro
        Gdx.gl.glClearColor(0, 0, 0, 1);
        //Borramos la pantalla
        Gdx.gl.glClear(GL20.GL_COLOR_BUFFER_BIT);

        //Actualizamos la cámara del juego
        camara.update();
        //Vinculamos al objeto de dibujo el TiledMap con la cámara del juego
        mapaRenderer.setView(camara);
        //Dibujamos el TiledMap
        mapaRenderer.render();
        //Inicializamos el objeto SpriteBatch
        sb.begin();
        //Pintamos el objeto Sprite a través del objeto SpriteBatch
        sprite.draw(sb);
        //Finalizamos el objeto SpriteBatch
        sb.end();

    }

Captura de la pantalla del juego en el que se muestra el mapa de baldosas y el sprite del mosquetero en la esquina inferior izquierda.
Elaboración propia. (CC BY-NC)


El resultado de ejecutar el juego en este punto puedes verlo en la captura de pantalla que se muestra a la derecha. Como puedes observar, al no haber indicado ningunas coordenadas iniciales para la ubicación del sprite, este se muestra en la esquina inferior izquierda de la pantalla. En el enlace siguiente, puedes descargar el código completo de la clase principal MiJuego, para que puedas incorporarla a tu proyecto y puedas ejecutarlo.
Descarga de MiJuego.java (0,002 MB)
Autoevaluación
Pregunta

Si queremos que el sprite se mueva hacia arriba y a la derecha, ¿cómo variarán las coordenadas, X e Y, del jugador?
Respuestas

Opción 1

Tanto X como Y se incrementarán.

Opción 2

X se decrementará, Y se incrementará.

Opción 3

X se incrementará, Y se decrementará.

Opción 4

Tanto X como Y se decrementarán.
Retroalimentación
2.3.3.2.- Creando un sprite animado (I). Constructores.

Nuestro héroe se mueve, pero parece un trozo de cartón más que una personaje. La solución para darle un toque natural es usar animaciones. Ya vimos antes que una animación no es más que una secuencia de imágenes que cuando se muestran secuencialmente producen un efecto de dinamismo y movimiento.

Fíjate en la siguiente imagen:
Imagen compuesta de 12 subimágenes, cada una de las cuáles contiene un frame de animación de un mosquetero.
Recorte de un fragmento de la imagen:
 InsaneJP.

 

En ella se pueden apreciar 4 filas, cada una de las cuáles es la animación que tendrá el sprite al moverse en la dirección arriba, derecha, abajo e izquierda respectivamente. Si extraemos una de esas imágenes independientes el trozo se denomina cuadro o frame de la animación. El conjunto de la imagen global que contiene los cuadros se denomina hoja de sprites o spritesheet. Es importante tener en cuenta que los diversos frames tienen que tener el mismo tamaño, para que de esa forma puedan extraerse adecuadamente los mismos.

Descarga el spritesheet siguiente, cópialo con el nombre mosquetero.png a la carpeta assets de tu subproyecto android:
Spritesheet de un mosquetero. (png - 26265 B)

Tomando el caso concreto de libGDX, hay que indicar cuánto tiempo queremos que dure un determinado frame, cambiando de un frame al siguiente una vez que ha transcurrido ese tiempo estipulado de forma automática.

Para manejar imágenes para sprites, ya hemos visto en el apartado anterior que tenemos que usar un objeto de la clase Texture para cargar dichas imágenes. El problema que tenemos en este caso, es que en el fichero de imagen que contiene la hoja de sprites contiene más de un frame y necesitaremos un mecanismo para poder procesarlos e individualizarlos. En libGDX esto se realiza usando objetos de la clase TextureRegion, que especifican un trozo rectangular de una determinada textura, representada esta por un objeto Texture. Necesitaremos un vector de objetos TextureRegion por cada animación que deseemos representar, que deberemos llenar con cada uno de los frames implicados en cada una de ellas. En el caso que nos ocupa, tendremos cuatro vectores que contendrán 3 objetos TextureRegion, uno por cada imagen de cada fila de la hoja de sprites. En el siguiente apartado veremos el código para realizar esa individualización de los frames.

Una vez tenemos correctamente individualizados los frames a representar, la clase que se utiliza para realizar animaciones en libGDX es Animation. Tiene varios constructores para adaptarse a casi cualquier fuente de frames. A continuación destacamos algunos de las más interesantes, si deseas ampliar información, puedes consultar en la documentación de LibGDX sobre la clase Animation:
Constructores de la clase Animation Constructor	Descripción
Animation(float duration, Array<? extends TextureRegion> cuadros) 	Crea una animación con todas las imágenes pasadas en el array cuadros. Cada una de ellas se mostrará durante duracion segundos.
Animation(float duration, Array<? extends TextureRegion> cuadros, Animation.PlayMode modo) 	

Crea una animación con todas las imágenes pasadas en el array cuadros. Cada una de ellas se mostrará durante duracion segundos. modo, permite reproducir la animación en varios modos:

    NORMAL, este es el modo por defecto, de principio al fin y se para al finalizar.
    REVERSED, se ejecuta desde el final al principio y se para
    LOOP se ejecuta de forma continua desde el principio al final.
    LOOP_REVERSED, se ejecuta de forma continua del final al principio
    LOOP_PINGPONG, se ejecuta de forma continua, la animación se realiza primero en un sentido y luego en el contrario, para luego volver a empezar. Es como si rebotara al llegar el final de la animación..
    LOOP_RANDOM, se ejecuta de forma continua y los frames se muestran de forma aleatoria.

Animation(float duration, TextureRegion... cuadros) 	Crea una animación con todas las imágenes pasadas en el array cuadros. Cada una de ellas se mostrará durante duracion segundos.

 

2.3.3.3.- Creando un sprite animado (II). Cargando los frames.

Vamos a crear cuatro animaciones, una por cada dirección en la que puede moverse nuestro personaje, y otra más que será la animación que se muestre en cada momento. Estos son los cambios que vamos a hacer a nuestro código fuente, añadiendo, una serie de atributos que se muestran a continuación:


public class MiJuego extends ApplicationAdapter implements InputProcessor {
    //Objeto que recoge el mapa de baldosas
    private TiledMap mapa;
    //Objeto con el que se pinta el mapa de baldosas
    private OrthogonalTiledMapRenderer mapaRenderer;
    // Cámara que nos da la vista del juego
    private OrthographicCamera camara;
    // Atributo en el que se cargará la hoja de sprites del mosquetero.
    private Texture img;
    //Atributo que permite dibujar imágenes 2D, en este caso el sprite.
    private SpriteBatch sb;

    //Constantes que indican el número de filas y columnas de la hoja de sprites.
    private static final int FRAME_COLS = 3;
    private static final int FRAME_ROWS = 4;

    //Animación que se muestra en el método render()
    private Animation jugador;

    //Animaciones para cada una de las direcciones de movimiento del personaje del jugador.
    private Animation jugadorArriba;
    private Animation jugadorDerecha;
    private Animation jugadorAbajo;
    private Animation jugadorIzquierda;

    //Posición en el eje de coordenadas actual del jugador.
    private float jugadorX, jugadorY;

    // Este atributo indica el tiempo en segundos transcurridos desde que se inicia la animación,
    // servirá para determinar cual es el frame que se debe representar.
    private float stateTime;

    // Contendrá el frame que se va a mostrar en cada momento.
    private TextureRegion cuadroActual;

 

Como podemos comprobar en los comentarios del código anterior, se han añadido varios atributos adicionales a los que ya había en nuestra clase principal del juego, y que juegan el rol que se indica en dichos comentarios. Una vez hemos declarado estos atributos, en el método create(), deberemos dar valores a algunos de ellos, en particular, a los objetos de la clase Animation, a los que daremos los frames que mostrarán y el tiempo que cada frame va a consumir en la representación de la propia animación. En nuestro caso, los frames de cada objeto de animación son tomados de la hoja de sprites en forma de filas, cada una de las cuales tiene tres elementos, de tal forma que la animación del mosquetero subiendo en el mapa, se corresponderá con la primera fila, la número 0, la del mosquetero desplazándose a la derecha, la fila 1, la del mosquetero desplazándose abajo, la fila 2 y, por último, la del mosquetero desplazándose a la izquierda, la fila 3. En el caso del tiempo que cada frame estará visible, será de 0.125 segundos.
Se ve una imagen compuesta de 12 subimágenes, cada una de las cuáles contiene un frame de animación de un mosquetero. Justo a su derecha, la misma imagen con cada uno de los frames separados por cuadros, y numerados en horizontal y vertical.
Hoja de sprites, mostrando las filas y columnas del mismo:
  InsaneJP.

 

El código del método create(), donde se crean e inicializan los objetos del juego, es el siguiente:

    @Override
    public void create() {
        //Ponemos el tamaño del mapa de baldosas
        float anchura = 1000;
        float altura = 1000;

        //Creamos una cámara y la vinculamos con el lienzo del juego.
        //En este caso le damos unos valores de tamaño que haga que el juego
        //se muestre de forma idéntica en todas las plataformas.
        camara = new OrthographicCamera(800, 480);
        //Posicionamos la vista de la cámara para que su vértice inferior izquierdo sea (0,0)
        camara.position.set(camara.viewportWidth / 2f, camara.viewportHeight / 2f, 0);
        //Vinculamos los eventos de entrada a esta clase.
        Gdx.input.setInputProcessor(this);
        camara.update();

        // Cargamos la imagen de los frames del mosquetero en el objeto img de la clase Texture.
        img = new Texture(Gdx.files.internal("mosquetero.png"));

        // Sacamos los frames de img en un array de TextureRegion.
        TextureRegion[][] tmp = TextureRegion.split(img, img.getWidth() / FRAME_COLS, img.getHeight() / FRAME_ROWS);

        // Creamos las distintas animaciones, teniendo en cuenta que el tiempo de muestra de cada frame
        // será de 150 milisegundos, y que les pasamos las distintas filas de la matriz tmp a las mismas
        jugadorArriba = new Animation(0.150f, tmp[0]);
        jugadorDerecha = new Animation(0.150f, tmp[1]);
        jugadorAbajo = new Animation(0.150f, tmp[2]);
        jugadorIzquierda = new Animation(0.150f, tmp[3]);

        // En principio se utiliza la animación del jugador arriba como animación por defecto.
        jugador = jugadorArriba;

        // Posición inicial del jugador.
        jugadorX = jugadorY = 0;

        // Ponemos a cero el atributo stateTime, que marca el tiempo e ejecución de la animación.
        stateTime = 0f;

        // Creamos el objeto SpriteBatch que nos permitirá representar adecuadamente el sprite
        // en el método render()
        sb = new SpriteBatch();

        // Cargamos el mapa de baldosas desde la carpeta de assets
        mapa = new TmxMapLoader().load("mapatutorial.tmx");
        mapaRenderer = new OrthogonalTiledMapRenderer(mapa);

    }


Una vez hemos creados los objetos en el método create(), la animación propiamente dicha, se representa en el método render(). En el código que sigue, puedes ver como quedaría dicho método para representar adecuadamente el sprite animado del mosquetero:


    @Override
    public void render() {
        //Ponemos el color del fondo a negro
        Gdx.gl.glClearColor(0, 0, 0, 1);
        //Borramos la pantalla
        Gdx.gl.glClear(GL20.GL_COLOR_BUFFER_BIT);

        //Actualizamos la cámara del juego
        camara.update();
        //Vinculamos el objeto de dibuja el TiledMap con la cámara del juego
        mapaRenderer.setView(camara);
        //Dibujamos el TiledMap
        mapaRenderer.render();

        // extraemos el tiempo de la última actualización del sprite y la acumulamos a stateTime.
        stateTime += Gdx.graphics.getDeltaTime();
       
        // Extraemos el frame que debe ir asociado al momento actual.
        cuadroActual = (TextureRegion) jugador.getKeyFrame(stateTime); // 1
       
        // le indicamos al SpriteBatch que se muestre en el sistema de coordenadas
        // específicas de la cámara.
        sb.setProjectionMatrix(camara.combined);

        // Inicializamos el objeto SpriteBatch
        sb.begin();
        // Pintamos el objeto Sprite a través del objeto SpriteBatch
        sb.draw(cuadroActual,jugadorX,jugadorY); // 2
        // Finalizamos el objeto SpriteBatch
        sb.end();

    }


Como puede observarse, en realidad el sprite animado se representa cuadro a cuadro, y en cada una de las actualizaciones del mismo, se extrae el cuadro actual en la línea marcada con el comentario "1", el cual se dibuja en la pantalla en la línea marcada con el comentario "2".

Ya tenemos las animaciones cargadas y el código que las representa, en el siguiente apartado veremos como hacer que el sprite animado se mueva por la pantalla y se represente la animación adecuada, en función de la dirección del movimiento.
2.3.3.4.- Moviendo el sprite animado.

Ya queda poco para dotar de animación a nuestro personaje. La imagen que realmente se dibujará dependerá del estado de la animación y de la dirección en la que queramos que el sprite se mueva.

Para mover al sprite tendremos que hacer estos cambios en el método keyUp(), que es en el que capturamos cuando pulsamos una tecla del teclado, en este caso los cursores, que serán los que nos permitan mover el mosquetero por la pantalla:


    @Override
    public boolean keyUp(int keycode) {
        //Si pulsamos uno de los cursores, se desplaza el sprite
        //de forma adecuada 5 pixeles, y se pone a cero el 
        //atributo que marca el tiempo de ejecución de la animación,
        //provocando que la misma se reinicie.
        stateTime = 0;

        if (keycode == Input.Keys.LEFT) {
            jugadorX += -5;
            jugador = jugadorIzquierda;            
        }
        if (keycode == Input.Keys.RIGHT) {
            jugadorX += 5;
            jugador = jugadorDerecha;
        }
        if (keycode == Input.Keys.UP) {
            jugadorY += 5;
            jugador = jugadorArriba;
        }
        if (keycode == Input.Keys.DOWN) {
            jugadorY += -5;
            jugador = jugadorAbajo;
        }

        //Si pulsamos la tecla del número 1, se alterna la visibilidad de la primera capa
        //del mapa de baldosas.
        if (keycode == Input.Keys.NUM_1)
            mapa.getLayers().get(0).setVisible(!mapa.getLayers().get(0).isVisible());
        //Si pulsamos la tecla del número 2, se alterna la visibilidad de la segunda capa
        //del mapa de baldosas.
        if (keycode == Input.Keys.NUM_2)
            mapa.getLayers().get(1).setVisible(!mapa.getLayers().get(1).isVisible());
        return false;
    }

 

Al detectar una tecla pulsada hacemos tres operaciones:

    Actualizar la posición del jugador.
    Asignar al jugador la animación que corresponda con la dirección del movimiento.
    Poner a cero el atributo que marca el tiempo de ejecución de la animación, lo que provoca que la misma comience desde cero y sea representada en su totalidad.

magen animada de un mosquetero andando en dirección a los cuatro puntos cardinales secuencialmente.
Recorte de un fragmento de la imagen:
 InsaneJP.

También podríamos modificar el comportamiento del juego a los clic del ratón y los toques de pantalla, de forma que el sprite del mosquetero también se mueva por la pantalla de forma similar a como lo hace cuando se pulsan las teclas del cursor. De esta forma, si se hace clic o se toca por encima de la posición del sprite, se realizaría lo mismo que si se pulsa la tecla de la flecha arriba, si se toca por debajo, como el cursor abajo, y de forma similar si es por la derecha o izquierda. El código del método touchDown() es el siguiente:


    @Override
    public boolean touchDown(int screenX, int screenY, int pointer, int button) {
        // Vector en tres dimensiones que recoge las coordenadas donde se ha hecho click
        // o toque de la pantalla.
        Vector3 clickCoordinates = new Vector3(screenX, screenY, 0);
        // Transformamos las coordenadas del vector a coordenadas de nuestra cámara.
        Vector3 posicion = camara.unproject(clickCoordinates);

        //Se pone a cero el atributo que marca el tiempo de ejecución de la animación,
        //provocando que la misma se reinicie.
        stateTime = 0;

        //Si se ha pulsado por encima de la animación, se sube esta 5 píxeles y se reproduce la
        //animación del jugador desplazándose hacia arriba.
        if (jugadorY < posicion.y) {
            jugadorY += 5;
            jugador = jugadorArriba;
        //Si se ha pulsado por debajo de la animación, se baja esta 5 píxeles y se reproduce
        //la animación del jugador desplazándose hacia abajo.
        } else if (jugadorY > posicion.y) {
            jugadorY -= 5;
            jugador = jugadorAbajo;
        }

        // Si se ha pulsado a la derecha de la animación, se mueve esta 5 píxeles a la derecha y
        // se reproduce la animación del jugador desplazándose hacia la derecha.
        if (jugadorX < posicion.x) {
            jugadorX += 5;
            jugador = jugadorDerecha;           
        // Si se ha pulsado a la izquierda de la animación, se mueve esta 5 píxeles a la
        // izquierda y se reproduce la animación del jugador desplazándose hacia la izquierda.
        } else if (jugadorX > posicion.x) {
            jugadorX -= 5;
            jugador = jugadorIzquierda;
        }
        return true;
    }

Reflexiona

Si analizas el código y lo ejecutas en tu proyecto, podrás ver que al intentar desplazar el sprite con el ratón o el toque de pantalla, casi nunca se muestra la animación de arriba o abajo, ya que es muy difícil que toquemos en una zona de la pantalla que no esté a la derecha o izquierda del punto central del sprite. Esto provoca que la animación que se muestre casi siempre sea al de la derecha o izquierda. ¿Cómo podríamos resolver este pequeño problema de forma fácil?

Cuando movemos el mosquetero hacia los bordes de la pantalla, puede llegar  perderse, ya que se mueve fuera de la vista de la cámara, en la siguiente sección vamos a ver como podemos hacer que la cámara esté centrada en el mosquetero y que este nunca se pierda de vista.
2.3.3.5.- Siguiendo al jugador (I). Centrando la vista.

Nuestro próximo reto es que el contenedor, la ventana por la que el jugador se asoma al videojuego, procure mantener al personaje dentro del alcance visual. Esto en libGDX es realmente muy simple, en comparación con lo que se debía hacer con otros motores gráficos. Sólo tenemos que hacer que las coordenadas horizontales y verticales de nuestra cámara del juego, coincidan con las coordenadas del sprite animado. Así, sólo tendríamos que añadir una línea de código en el método render() de nuestra aplicación, que quedaría como se muestra a continuación:

    @Override
    public void render() {
        //Ponemos el color del fondo a negro
        Gdx.gl.glClearColor(0, 0, 0, 1);
        //Borramos la pantalla
        Gdx.gl.glClear(GL20.GL_COLOR_BUFFER_BIT);

        //Trasladamos la cámara para que se centre en el mosquetero.
        camara.position.set(jugadorX,jugadorY,0f);
        //Actualizamos la cámara del juego
        camara.update();
        //Vinculamos el objeto de dibuja el TiledMap con la cámara del juego
        mapaRenderer.setView(camara);
        //Dibujamos el TiledMap
        mapaRenderer.render();
        // extraemos el tiempo de la última actualización del sprite y la acumulamos a stateTime.
        stateTime += Gdx.graphics.getDeltaTime();
        //Extraemos el frame que debe ir asociado a al momento actual.
        cuadroActual = (TextureRegion) jugador.getKeyFrame(stateTime);
        // le indicamos al SpriteBatch que se muestre en el sistema de coordenadas
        // específicas de la cámara.
        sb.setProjectionMatrix(camara.combined);
        //Inicializamos el objeto SpriteBatch
        sb.begin();
        //Pintamos el objeto Sprite a través del objeto SpriteBatch
        sb.draw(cuadroActual, jugadorX, jugadorY);
        //Finalizamos el objeto SpriteBatch
        sb.end();

    }

Copia este código el proyecto, sustituyendo el código del método render() y ejecútalo. Comprobarás como la cámara sigue ahora al jugador. Sin embargo ocurre un problema: cuando movemos nuestro personaje cerca de las esquinas del tilemap se ven unas antiestéticas franjas negras.
Demostración del efecto de trasladar el mapa fuera de los límites. Aparecen franjas negras a la izquierda y a la derecha de la imagen.
Captura de pantalla de una aplicación propia.
Tiles que componen la imagen obtenidos de:
 Zeronomous.
Autoevaluación

Observa el código fuente del proyecto y rellena los huecos con los datos correctos:

El tamaño de la vista de la cámara del juego es de
Rellenar huecos (1):
x
Rellenar huecos (2):
píxeles. Por otro lado, nuestro personaje tiene unas dimensiones de
Rellenar huecos (3):
x
Rellenar huecos (4):
píxeles y, cuando está siendo animado, mantiene cada frame durante
Rellenar huecos (5):
milisegundos.

2.3.3.6.- Siguiendo al jugador (II). Poniendo límites.

El problema no es difícil de arreglar, pero para entender cómo funciona vamos a tener que introducir algunos métodos de la clase TiledMapTileLayer. Esta clase permite extraer las distintas capas que componen un TiledMap, y posee unos métodos que nos van a permitir determinar las dimensiones en alto y ancho del mapa:

    .getWidth(), que nos devuelve el número de columnas de la capa del tilemap completo.
    .getHeight(), que nos devuelve el número de filas de la capa del tilemap completo.
    .getTileWidth(), que nos devuelve la anchura de una baldosa en píxeles.
    .getTileHeight(), que nos devuelve la altura de una baldosa en píxeles.

Fíjate en que si multiplicamos capa.getWidth() por capa.getTileWidth() obtendremos la anchura total del mapa en píxeles. Lo mismo ocurrirá con la altura total si hacemos lo propio sustituyendo Width por Height. Añade estas línea con los demás atributos de la clase principal del juego:

    // Tamaño del mapa de baldosas.
    private int anchoMapa, altoMapa;
    //Atributos que indican la anchura y la altura de un tile del mapa de baldosas
    int anchoCelda,altoCelda;

 

Éstas al final del método create():

        //Determinamos el alto y ancho del mapa de baldosas. Para ello necesitamos extraer la capa
        //base del mapa y, a partir de ella, determinamos el número de celdas a lo ancho y alto,
        //así como el tamaño de la celda, que multiplicando por el número de celdas a lo alto y
        //ancho, da como resultado el alto y ancho en pixeles del mapa.
        TiledMapTileLayer capa = (TiledMapTileLayer) mapa.getLayers().get(0);
        anchoCelda = (int) capa.getTileWidth();
        altoCelda = (int) capa.getTileHeight();
        anchoMapa = capa.getWidth() * anchoCelda;
        altoMapa = capa.getHeight() * altoCelda;

 

Y el resto en el método render(), justo antes de que se actualice la cámara, ya que la posición de esta es modificada:

        //Trasladamos la cámara para que se centre en el mosquetero.
        camara.position.set(jugadorX, jugadorY, 0f);
        //Comprobamos que la cámara no se salga de los límites del mapa de baldosas,
        //Verificamos, con el método clamp(), que el valor de la posición x de la cámara
        //esté entre la mitad de la anchura de la vista de la cámara y entre la diferencia entre
        //la anchura del mapa restando la mitad de la anchura de la vista de la cámara,
        camara.position.x = MathUtils.clamp(camara.position.x, camara.viewportWidth / 2f,
                anchoMapa - camara.viewportWidth / 2f);
        //Verificamos, con el método clamp(), que el valor de la posición y de la cámara
        //esté entre la mitad de la altura de la vista de la cámara y entre la diferencia entre
        //la altura del mapa restando la mitad de la altura de la vista de la cámara,
        camara.position.y = MathUtils.clamp(camara.position.y, camara.viewportHeight / 2f,
                altoMapa - camara.viewportHeight / 2f);

 

Esa sección de código se asegura de que a pesar de desplazarnos nunca nos saldremos de los límites del mapa.  Se obliga a que la posición X de la cámara tenga, como valor mínimo, el de la mitad de la anchura de la vista de la cámara, y como valor máximo, el resultado de restarle a la anchura global del mapa ese mismo dato mínimo. De forma análoga,  la posición Y de la cámara va a tener, como valor mínimo, el valor de la mitad de la altura de su ventana, y como valor máximo, el de la altura global del mapa, al que se le resta ese mismo valor mínimo.

El código de la función clamp es el siguiente:

static public long clamp (long value, long min, long max) {
        if (value < min) return min;
        if (value > max) return max;
        return value;
}

Pero, ¿por qué tomamos esos valores máximos y mínimos?. En primer lugar, hemos de tener en cuenta que las coordenadas de posición de una cámara, en libGDX, se sitúan justo en el centro de la ventana de vista de la misma. Intentemos entender el por qué con un ejemplo: imagina que nuestro tilemap tiene unas dimensiones de 1000x700 píxeles y nuestro cámara una vista de 400x300 píxeles.
Cuatro ejemplos que muestran los límites que debemos a imponer a los desplazamientos para evitar que el tilemap se salga de los límites.
Elaboración propia. (CC BY-NC)

Un desplazamiento del sprite hacia la izquierda, implica que la cámara se desplazaría en el mismo sentido y, en caso de que la posición del mosquetero se sitúe más cercano al borde izquierdo que el valor de la mitad de la anchura de la vista de la cámara, se empezaría a ver la franja negra por la izquierda. Por tanto, cuando el valor de coordenada x de la posición de la cámara, sea menor que la mitad de la anchura de su vista, tendremos que poner ese valor mínimo para evitar que se vea la franja negra y se salga la cámara de los márgenes del propio mapa, como puede verse en la imagen anterior.

Siguiendo el razonamiento, lo máximo que podremos desplazar a la derecha la cámara es la anchura del mapa, en píxeles, menos la mitad de la anchura de la vista de la cámara. Si nos desplazamos más allá, veremos una franja negra a la derecha, por eso limitamos el valor a que, como mínimo, sea ese valor.

Lo mismo se aplicaría al desplazamiento de la coordenada Y, aunque en este caso se tomarían los datos de la altura, tanto de la vista de la cámara como del mapa.

Para que quede perfecto lo único que falta es evitar que el jugador se salga del mapa y eso lo resolveremos cuando implementemos las colisiones, mientras tanto aquí puedes descargar el código de la clase principal del juego, tal como está en este momento:
Descarga de MiJuego.java (java - 11112 B)
2.3.3.7.- Índice de recursos gráficos.

Puedes encontrar muchos tilesets y spritesheets en Internet usando un buscador, aunque debes tener cuidado con la licencia de uso y los derechos de autor: algunos prohíben el uso comercial, otros son de uso libre y en otros has de informar al autor o incluirlo en los créditos de tu proyecto. Consulta bien antes de usarlos.
Una paleta de pintor con algunos colores en su superficie y un pincel reposando sobre ella.
 Stonda.
Para saber más

Aún así, hemos seleccionado unos cuantos enlaces donde podrás encontrar material con licencias poco restrictivas:

Generador online de spritesheets de personajes.

Otro generador online de spritesheets de personajes.

Colección de recursos gráficos de OpenGameArt.org

Tilesets para juegos de aventura de RPG Palace.

Personajes animados para juegos de aventura de RPG Palace.

Pixelart en devianART.

Tilesets en devianART.

Reiner's Tilesets.
2.3.4.- Colisiones.
Vista cercana de varias canicas chocando entre sí.
 Glenda Green

Por fin nuestro héroe puede moverse por todo lo ancho y alto del mapa sin salirse de sus límites y sin que lo perdamos de vista.

Aún así, hay todavía un comportamiento extraño, y es que puede pasar por encima de todos los elementos del mapa. Sería deseable evitar que el sprite invadiera tiles que se consideran obstáculos.

Para ello, la única información fiable que tenemos es el tilemap ya que la colocación de obstáculos es tarea del diseñador de mapas. En los próximos apartados aprenderemos a extraer información del él y a reaccionar de forma correcta ante los obstáculos.
2.3.4.1.- Marcando los obstáculos en el tilemap (I). Propiedades.

Antes de impedir el paso al jugador tenemos que saber por donde no puede pasar porque algún tile no se lo permite. Hay muchas formas de indicar que un tile del mapa contiene un obstáculo:

    Podríamos hacerlo de forma manual, incluyendo en el código específico una lista con las coordenadas de los tiles que hay que evitar. No es una buena idea porque cualquier cambio en el mapa implicaría modificar el código del juego. Además, sería una tarea muy laboriosa.
    Marcar desde Tiled ciertos tiles del tileset como obstáculos. Cuando carguemos el mapa, buscaremos las ocurrencias de los tiles marcados. Una vez encontrados, almacenaremos en un array bidimensional del tamaño del mapa que indique si el tile que está en esa posición es un obstáculo o no.
    Considerar todos los tiles de una capa como obstáculos. Esto sólo lo podremos hacer si el diseñador los ha colocado en una capa independiente. Se buscarán y almacenarán en un array de forma similar al punto anterior.

Centrémonos en la segunda solución: ¿Cómo puedo marcar un tile como obstáculo? En Tiled existe un concepto llamado "propiedades". Una propiedad es información adicional que puede incluirse a nivel de mapa, a nivel de capa y a nivel de tile. Constan de un nombre y un valor, ambos siendo de tipo java.lang.String.

Las propiedades del mapa se cambian desde la opción "Mapa | Propiedades del mapa...". Las de una capa, haciendo clic con el botón secundario encima de su nombre y eligiendo la opción "Propiedades de la capa..." desde el menú contextual. En el caso de un tile del tileset se hace de forma similar a la capa.
Captura que muestra cómo incorporar propiedades a un tile desde Tiled.
Captura de pantalla de la aplicación Tiled
bajo licencia GNU GPL v2.
Tiles que componen la imagen obtenidos de:
 Zeronomous.

 

Estas propiedades pueden utilizarse mediante libGDX, que añade clases e interfaces específicas para cada uno de los componentes de un mapa de baldosas de Tiled.

    TiledMap, que nos permite manejar mapas completos.
    TiledMapTileLayer, que permite manejar cada una de las capas de un TiledMap.
    TiledMapTileLayer.Cell y TiledMapTile, que permite manejar cada baldosa(tile) de un TiledMap.

Todas pueden acceder a sus respectivas propiedades a través de un objeto de la clase MapProperties, el cual es en realidad una especie de matriz asociativa, en la que tenemos una serie de pares de valores del tipo clave-valor, de tal forma que cada clave está relacionada con su valor de forma biunívoca. En el siguiente código, tienes un ejemplo de un método al que se le pasa como parámetro un posición en el mapa, y determina si el tile de esa posición está o no bloquedo, en cuyo caso tendría definida una propiedad denominada "bloqueado":

 
    public boolean celdaBloqueada(float x, float y) {
        //Creamos el objeto Cell a partir de la capa donde hemos definido los obstáculos
        //en función de las coordenadas que pasamos como parámetro a este método.
        TiledMapTileLayer.Cell cell = capaObstaculos.getCell(
                (int) (x / capaObstaculos.getTileWidth()),
                (int) (y / capaObstaculos.getTileHeight()));

        //Devolvemos true si el objeto Cell no es nulo, y el objeto TiledMapTile que contiene
        //no es nulo y si en las propiedades del TiledMapTile hay una que de llama "bloqueado"
        return cell != null && cell.getTile() != null
                && cell.getTile().getProperties().containsKey("bloqueado");
    }

Autoevaluación
Pregunta

¿Por qué incluir una lista de coordenadas con obstáculos directamente en el código no es una buena idea? (marca 2):
Respuestas

Opción 1

Porque hace que el comportamiento antes los obstáculos sea menos realista.

Opción 2

Porque dificulta el control del personaje por parte del jugador.

Opción 3

Porque es más difícil mantener los mapas.

Opción 4

Porque obliga a recompilar cuando se hacen cambios a los mapas.

2.3.4.2.- Marcando los obstáculos en el tilemap (II). Leyendo las capas.
Captura de Tiled que muestra cómo colocar una capa de tiles que actuarán como obstáculos.
Captura de pantalla de la aplicación Tiled
bajo licencia GNU GPL v2.
Tiles que componen la imagen obtenidos de:
 Zeronomous.

Aún tenemos que estudiar la tercera solución. De hecho, será esa la que utilicemos para nuestro proyecto ya que nuestro tilemap tiene todos los obstáculos colocados en una capa independiente. Si cuando creaste tu mapa no lo tuviste en cuenta, modifícalo antes de seguir o no funcionará la detección de obstáculos. Recuerda que la primera capa es el suelo, la segunda la decoración y la tercera los obstáculos.

El método para detectar si hay un tile en cierta posición de una capa determinada pasa por generar un objeto Cell, en la posición dada de la capa,  a través del método  .getCell() del objeto de la propia capa, determinar si este es nulo o no. Si la llamada devuelve un objeto nulo es que en esa posición del mapa y capa no hay ningún tile. Ya que tenemos que usarla en el método create() , lo que vamos a hacer es recorrer todo el mapa buscando los obstáculos y almacenar en un array si el paso está bloqueado o no en esas posiciones. Para ello añadiremos al final de la clase principal del juego, un atributo nuevo, que este caso será una matriz booleana, con dimensiones iguales al número de filas y columnas de tiles del mapa:

 private boolean[][] obstaculo;

 

La matriz obstaculo, almacenará un booleano por cada tile del mapa indicando con true si es un obstáculo o con false si no lo es. Por último, incorpora las siguientes líneas al final del método create():

        //Cargamos la capa de los obstáculos, que es la tercera en el TiledMap.
        capaObstaculos = (TiledMapTileLayer) mapa.getLayers().get(2);

        //Cargamos la matriz de los obstáculos del mapa de baldosas.
        int anchoCapa = capaObstaculos.getWidth(), altoCapa = capaObstaculos.getHeight();
        obstaculo = new boolean[altoCapa][anchoCapa];
        for (int x = 0; x < anchoCapa; x++) {
            for (int y = 0; y < altoCapa; y++) {
                obstaculo[x][y] = (capaObstaculos.getCell(x, y) != null);
            }
        }

 

Fíjate que recorremos la capa de obstáculos del tilemap intentando crear celdas válidas en la posición dada por (x,y). Si devuelve no se puede crear una celda, porque no haya un tile en esa posición, la posición equivalente en la matriz valdrá false, en caso contrario, valdrá true.

Con estos cambios, ya podemos comprobar de una forma sencilla desde el resto del código si hay un obstáculo en determinado tile del mapa.
2.3.4.3.- Detectando la colisión con obstáculos (I). Algoritmo.
Representación que muestra qué puntos del sprite debemos tener en cuenta para calcular colisiones con los tiles.
Material propio que incluye recortes
de un fragmento de una imagen.
  InsaneJP.

Nuestro personaje debe poder moverse libremente por el mapa hasta que un obstáculo se lo impida. ¿Cómo sabemos si la posición del sprite es válida o no? Observa la siguiente imagen y fíjate en el sprite de la parte de arriba: siempre que su base no esté tocando ningún tile obstáculo debería considerarse que su posición es buena. Dado que la anchura del sprite es menor que la de un tile no será suficiente comprobar si alguno de los dos extremos de la base tocan un obstáculo (mira los puntos azules de la parte de la derecha), ya que los extremos del sprite van a tocar a dos tiles a la vez, y puede que alguno de ellos sea un obstáculo, así que, para evitar este problema, sumaremos a la coordenada x del punto azul de la izquierda una cuarta parte de la anchura del sprite, y la coordenada x del punto azul de la derecha, le restaremos esa misma cantidad. Así los puntos podrán pasar entre dos tiles que sean obstáculos.

Podrías preguntarte el motivo de considerar solamente la base en lugar del rectángulo completo, ¡es una muy buena pregunta! Se debe a la perspectiva de nuestros tiles. Observa ahora el sprite que hay justo debajo y verás como su rectángulo está dentro de un tile obstáculo, sin embargo esa posición es visualmente válida porque el jugador no está tocando el tile realmente. Es por ello que solo comprobaremos dónde pisa, es decir, la base del sprite.

Si estuviéramos usando un tileset y sprites con una perspectiva cenital (donde la acción se desarrolla solamente en horizontal y lo vemos justo desde arriba), entonces sí tendríamos que comprobar el cuadro entero. Imagina por un momento que estuviéramos programando un juego de tanques en perspectiva cenital y en el que hay tiles que representan un muro:
Representación que muestra qué puntos del sprite debemos tener en cuenta para calcular colisiones con los tiles en el caso de una vista cenital.
Material propio que incluye recortes
de un fragmento de una imagen.
InsaneJP.

Aquí no tendría sentido comprobar sólo la base porque podría ocurrir que se solaparan, como pasa con el tanque de abajo, y no se vería natural.

Volviendo al caso que nos ocupa, el problema se resume en comprobar si alguno de los extremos de la base está tocando un tile marcado como obstáculo. Para hacer los cálculos necesitaremos algunos datos que almacenaremos en nuevos atributos. Colócalos detrás de los últimos que añadimos a la clase principal del juego.

    //Atributos que indican la anchura y altura del sprite animado del jugador.
    int anchoJugador, altoJugador;

 

Este par de variables almacenará las dimensiones en píxeles del sprite (en este caso serán 48 y 72 respectivamente).  Añadamos las asignaciones de sus valores al final del método create():

        //Cargamos en los atributos del ancho y alto del sprite sus valores
        cuadroActual = (TextureRegion) jugador.getKeyFrame(stateTime);
        anchoJugador = cuadroActual.getRegionHeight();
        altoJugador = cuadroActual.getRegionHeight();

En el código anterior se determina las dimensiones en alto y ancho del sprite, tomando el primer frame del mismo y extrayendo de él esos datos.
Ejemplo de cómo convertir una coordenada medida en píxeles a una coordenada de tile.

Para saber a qué tile pertenece un punto determinado del jugador primero necesitamos tener su posición en píxeles. Luego se convierte a unidades de tiles dividiendo el componente por el tamaño de un tile.

El extremo izquierdo de la base:

    En píxeles: [jugadorX+anchoJugador/4, jugadorY]
    En tiles: [(jugadorX+anchoJugador/4)/anchoCelda, (jugadorY)/altoCelda]

El extremo derecho de la base:

    En píxeles: [jugadorX+anchoJugador*3/4, jugadorY]
    En tiles: [(jugadorX+anchoJugador*3/4)/anchoCelda, (jugadorY)/altoCelda]

Debes conocer

Como ya mencionamos en su momento, libGDX usa un sistema de coordenadas cartesiano clásico (X,Y) donde la esquina inferior izquierda del contenedor es la posición (0,0). El primer número expresa la componente horizontal, mientras que el segundo es la componente vertical. Los valores negativos serán a la izquierda y hacia abajo respecto a dicha esquina, mientras que los positivos serán hacia la derecha y hacia arriba.
Autoevaluación
Pregunta

Si estuviéramos en vista cenital, tal como se muestra en la imagen que puedes ver en esta misma página, de la perspectiva cenital del juego de tanques, también tendríamos que comprobar los extremos de la parte superior. ¿Cuál sería la posición en píxeles que habría que considerar para detectar el tile del extremo superior derecho del sprite?
Respuestas

Opción 1

[jugadorX+jugadorWidth, jugadorY+jugadorHeight]

Opción 2

[jugadorX, jugadorY]

Opción 3

[jugadorX+jugadorWidth, jugadorY].

Opción 4

[jugadorX, jugadorY+jugadorHeight]
Retroalimentación
2.3.4.4.- Detectando la colisión con obstáculos (II). Implementación.

Una vez disponemos del algoritmo ya sólo tenemos que implementarlo. Básicamente lo que haremos es guardar una copia de la posición del jugador antes de que pueda ser cambiada con las teclas del cursor. Después de procesar el teclado comprobaremos si la posición nueva es válida; si no lo es devolveremos la posición original. El método keyUp() quedaría como sigue:

    @Override
    public boolean keyUp(int keycode) {
        //Si pulsamos uno de los cursores, se desplaza el sprite
        //de forma adecuada un pixel, y se pone a cero el
        //atributo que marca el tiempo de ejecución de la animación,
        //provocando que la misma se reinicie.

        //Guardamos la posición anterior del jugador por si al desplazarlo se topa
        //con un obstáculo y podamos volverlo a la posición anterior.
        float jugadorAnteriorX = jugadorX;
        float jugadorAnteriorY = jugadorY;

        stateTime = 0;

        if (keycode == Input.Keys.LEFT) {
            jugadorX += -5;
            jugador = jugadorIzquierda;

        }
        if (keycode == Input.Keys.RIGHT) {
            jugadorX += 5;
            jugador = jugadorDerecha;
        }
        if (keycode == Input.Keys.UP) {
            jugadorY += 5;
            jugador = jugadorArriba;
        }
        if (keycode == Input.Keys.DOWN) {
            jugadorY += -5;
            jugador = jugadorAbajo;
        }

        //Si pulsamos la tecla del número 1, se alterna la visibilidad de la primera capa
        //del mapa de baldosas.
        if (keycode == Input.Keys.NUM_1)
            mapa.getLayers().get(0).setVisible(!mapa.getLayers().get(0).isVisible());
        //Si pulsamos la tecla del número 2, se alterna la visibilidad de la segunda capa
        //del mapa de baldosas.
        if (keycode == Input.Keys.NUM_2)
            mapa.getLayers().get(1).setVisible(!mapa.getLayers().get(1).isVisible());

        // al chocar con un obstáculo el jugador vuelve a su posición inicial
        // la parte izquierda de X es "X + 1/4 del ancho del jugador"
        // la parte derecha de X es "X + 3/4 del ancho del jugador"
        if ((obstaculo[(int) ((jugadorX + anchoJugador/4) / anchoCelda)][((int) (jugadorY) / altoCelda)])
                || (obstaculo[(int) ((jugadorX + 3*anchoJugador/4) / anchoCelda)][((int) (jugadorY) / altoCelda)])) {
            jugadorX = jugadorAnteriorX;
            jugadorY = jugadorAnteriorY;
        }

        return false;
    }


En el caso del método touchDown(), también deberemos añadir el código adecuado para que se detecten las colisiones con los obstáculos:

    @Override
    public boolean touchDown(int screenX, int screenY, int pointer, int button) {
        // Vector en tres dimensiones que recoge las coordenadas donde se ha hecho click
        // o toque de la pantalla.
        Vector3 clickCoordinates = new Vector3(screenX, screenY, 0);
        // Transformamos las coordenadas del vector a coordenadas de nuestra cámara.
        Vector3 posicion = camara.unproject(clickCoordinates);

        //Se pone a cero el atributo que marca el tiempo de ejecución de la animación,
        //provocando que la misma se reinicie.
        stateTime = 0;

        //Guardamos la posición anterior del jugador por si al desplazarlo se topa
        //con un obstáculo y podamos volverlo a la posición anterior.
        float jugadorAnteriorX = jugadorX;
        float jugadorAnteriorY = jugadorY;

        //Si se ha pulsado por encima de la animación, se sube esta 5 píxeles y se reproduce la
        //animación del jugador desplazándose hacia arriba.
        if ((jugadorY + altoJugador) < posicion.y) {
            jugadorY += 5;
            jugador = jugadorArriba;
            //Si se ha pulsado por debajo de la animación, se baja esta 5 píxeles y se reproduce
            //la animación del jugador desplazándose hacia abajo.
        } else if ((jugadorY) > posicion.y) {
            jugadorY -= 5;
            jugador = jugadorAbajo;
        }
        //Si se ha pulsado más de la mitad del ancho del sprite a la derecha de la animación, se
        //mueve esta 5 píxeles a la derecha se reproduce la animación del jugador desplazándose
        // hacia la derecha.
        if ((jugadorX + anchoJugador/2) < posicion.x) {
            jugadorX += 5;
            jugador = jugadorDerecha;
            //Si se ha pulsado mas de la mitad del ancho del sprite a la izquierda de la animación,
            // se mueve esta 5 píxeles a la izquierda y se reproduce la animación del jugador
            // desplazándose hacia la izquierda.
        } else if ((jugadorX - anchoJugador/2) > posicion.x) {
            jugadorX -= 5;
            jugador = jugadorIzquierda;
        }

	// al chocar con un obstáculo el jugador vuelve a su posición inicial
        if ((obstaculo[(int) ((jugadorX + anchoJugador/4) / anchoCelda)][((int) (jugadorY) / altoCelda)])
                || (obstaculo[(int) ((jugadorX + 3*anchoJugador/4) / anchoCelda)][((int) (jugadorY) / altoCelda)])) {
            jugadorX = jugadorAnteriorX;
            jugadorY = jugadorAnteriorY;

        }

        return true;
    }

Piensa

Hay otro tema que aún no hemos solucionado: el jugador puede salirse del mapa por cualquiera de sus cuatro lados sin que la cámara pueda seguirle. ¿Se te ocurre cómo podríamos arreglarlo?
Captura de pantalla del jugador intentando, sin éxito, entrar en una casilla ocupada por un tile obstáculo.
Captura de pantalla de una aplicación propia. Tiles que componen la imagen obtenidos de:  Zeronomous.

Ya que estamos detectando colisiones con obstáculos podemos aprovechar para detectar la colisión con el borde del tilemap, evitando así que el jugador pueda salir. No sería necesario realizarlo si rodeáramos el mapa con obstáculos, pero no es nuestro caso así que tendremos que considerar esta posibilidad vía código.

Es muy sencillo, solamente tenemos que preguntarnos en qué casos la posición no será válida. Veámoslo primero con la coordenada X:

    Si jugadorX es menor que 0, estaremos saliéndonos por la parte izquierda.
    Si jugadorX es mayor que anchoMapa (la anchura del mapa) quiere decir que la parte izquierda del sprite se habrá salido del mapa. Pero el sprite hace ya unos cuantos píxeles que empezó a salirse por su extremo derecho. Por tanto, a la anchura del mapa límite habrá que restarle la anchura del sprite.
    Algo similar se podría decir acerca de la coordenada Y, aunque en este caso referida a la altura del mapa.

Modifiquemos la sentencia if que acabamos de añadir con estos cambios y asunto arreglado:

        //Detectamos las colisiones con los obstáculos del mapa y si el jugador se sale del mismo.
        if ((jugadorX < 0 || jugadorY < 0 ||
                jugadorX > (mapaAncho - anchoJugador) ||
                jugadorY > (mapaAlto - altoJugador)) ||
                ((obstaculo[(int) ((jugadorX + anchoJugador / 4) / anchoCelda)][((int) (jugadorY) / altoCelda)]) ||
                        (obstaculo[(int) ((jugadorX + 3 * anchoJugador / 4) / anchoCelda)][((int) (jugadorY) / altoCelda)]))) {
            jugadorX = jugadorAnteriorX;
            jugadorY = jugadorAnteriorY;
        }

Descarga de MiJuego.java (0,005 MB)
2.3.4.5.- Añadiendo personajes no jugadores (NPC).
SriteSheet para los NPC.
SpriteSheet del villano del juego.
Tiles que componen la imagen obtenidos de:
Gon.

En un juego normalmente será necesario añadir otros sprites no controlados directamente por el jugador, tales como enemigos, balas en movimiento, personajes interactivos, etc. Con los conocimientos que ya tienes no deberías tener problemas en programarlos, pero aún así vamos a hacer un ejemplo que demuestre el potencial de libGDX.

El objetivo será crear NPC, personajes no controlados por el jugador. Su misión consistirá en moverse en línea recta desde una posición aleatoria del mapa a otra y pararse una vez llegan ahí. No entraremos en implementar colisiones con ellos, eso te lo dejamos como ejercicio si quieres profundizar.

Cada NPC será un sprite animado. Utilizaremos el spritesheet que puedes ver en la imagen de la derecha, con lo que todos serán tendrán la misma apariencia. Implementaremos el código de la manera más sencilla, pero ten en cuenta que lo óptimo sería crear una clase nueva que guarde el estado del NPC (su posición, su destino, su animación, etc.) en lugar de hacerlo con arrays, aunque después sí que se creen arrays de objetos de la clase que implemente los NPC.

El el siguiente enlace puedes descargar el fichero del spritesheet del mago rojo, el villano del juego que estamos implementando:

SpriteSheet del mago rojo. (png - 25.34 KB).

Por lo pronto tenemos que determinar qué variables son distintas para cada NPC. En este caso será la posición actual, la posición destino y la animación activa).  Añadiremos los siguientes atributos, al final de los actuales, para implementar estos datos.

    //Animaciones posicionales relacionadas con los NPC del juego
    private Animation noJugadorArriba;
    private Animation noJugadorDerecha;
    private Animation noJugadorAbajo;
    private Animation noJugadorIzquierda;

    //Array con los objetos Animation de los NPC
    private Animation[] noJugador;
    //Atributos que indican la anchura y altura del sprite animado de los NPC.
    int anchoNoJugador, altoNoJugador;
    //Posición inicial X de cada uno de los NPC
    private float[] noJugadorX;
    //Posición inicial Y de cada uno de los NPC
    private float[] noJugadorY;
    //Posición final X de cada uno de los NPC
    private float[] destinoX;
    //Posición final Y de cada uno de los NPC
    private float[] destinoY;
    //Número de NPC que van a aparecer en el juego
    private static final int numeroNPCs = 20;
    // Este atributo indica el tiempo en segundos transcurridos desde que se inicia la animación
    // de los NPC , servirá para determinar cual es el frame que se debe representar.
    private float stateTimeNPC;

 

El hecho de implementar esas variables como arrays nos permite acceder rápidamente a los datos del NPC que necesitemos en cada momento y, además, usando bucles for podemos realizar las mismas operaciones a todos ellos de una forma sencilla.

Añade esto al final de create():

        //Inicializamos el apartado referente a los NPC
        noJugador = new Animation[numeroNPCs];
        noJugadorX = new float[numeroNPCs];
        noJugadorY = new float[numeroNPCs];
        destinoX = new float[numeroNPCs];
        destinoY = new float[numeroNPCs];

        //Creamos las animaciones posicionales de los NPC
        //Cargamos la imagen de los frames del monstruo en el objeto img de la clase Texture.
        img = new Texture(Gdx.files.internal("magorojo.png"));

        //Sacamos los frames de img en un array de TextureRegion.
        tmp = TextureRegion.split(img, img.getWidth() / FRAME_COLS, img.getHeight() / FRAME_ROWS);

        // Creamos las distintas animaciones, teniendo en cuenta que el tiempo de muestra de cada frame
        // será de 150 milisegundos.
        noJugadorArriba = new Animation(0.150f, tmp[0]);
        noJugadorArriba.setPlayMode(Animation.PlayMode.LOOP);
        noJugadorDerecha = new Animation(0.150f, tmp[1]);
        noJugadorDerecha.setPlayMode(Animation.PlayMode.LOOP);
        noJugadorAbajo = new Animation(0.150f, tmp[2]);
        noJugadorAbajo.setPlayMode(Animation.PlayMode.LOOP);
        noJugadorIzquierda = new Animation(0.150f, tmp[3]);
        noJugadorIzquierda.setPlayMode(Animation.PlayMode.LOOP);

        //Cargamos en los atributos del ancho y alto del sprite del monstruo sus valores
        cuadroActual = (TextureRegion) noJugadorAbajo.getKeyFrame(stateTimeNPC);
        anchoNoJugador = cuadroActual.getRegionWidth();
        altoNoJugador = cuadroActual.getRegionHeight();

        //Se inicializan, la animación por defecto y, de forma aleatoria, las posiciones
        //iniciales y finales de los NPC. Para simplificar un poco, los NPC pares, se moveran
        //de forma vertical y los impares de forma horizontal.
        for (int i = 0; i < numeroNPCs; i++) {
            noJugadorX[i] = (float) (Math.random() * mapaAncho);
            noJugadorY[i] = (float) (Math.random() * mapaAlto);

            if (i % 2 == 0) {
                // NPC par => mover de forma vertical
                destinoX[i] = noJugadorX[i];
                destinoY[i] = (float) (Math.random() * mapaAlto);
                // Determinamos cual de las animaciones verticales se utiliza.
                if (noJugadorY[i] < destinoY[i]) {
                    noJugador[i] = noJugadorArriba;
                } else {
                    noJugador[i] = noJugadorAbajo;
                }
            } else {
                // NPC impar => mover de forma horizontal
                destinoX[i] = (float) (Math.random() * mapaAncho);
                destinoY[i] = noJugadorY[i];
                // Determinamos cual de las animaciones horizontales se utiliza.
                if (noJugadorX[i] < destinoX[i]) {
                    noJugador[i] = noJugadorDerecha;
                } else {
                    noJugador[i] = noJugadorIzquierda;
                }
            }

        }
        // Ponemos a cero el atributo stateTimeNPC, que marca el tiempo e ejecución de la animación
        // de los NPC.
        stateTimeNPC = 0f;


Fíjate que hemos activado la animación automática, ya que las instancias de animación son compartidas entre todos los NPC y con la animación temporizada manualmente se interferían entre ellos. Para elegir posiciones al azar usamos la función Math.random() que devuelve un double entre 0 y 1. Para la coordenada X, si lo multiplicamos por anchoMapa nos devolverá un número entre 0 y anchoMapa (sin llegar a él). Dado que las coordenadas se almacenan como float, hemos tenido que hacer un casting. De la misma forma se hace para las coordenadas Y.

Añade este código, justo antes de la instrucción que cierra el objeto StriteBatch, sb.end(), en el método render():

        //Dibujamos las animaciones de los NPC
        for (int i= 0; i < numeroNPCs; i++) {
            actualizaNPC(i,0.5f);
            cuadroActual = (TextureRegion) noJugador[i].getKeyFrame(stateTimeNPC);
            sb.draw(cuadroActual,noJugadorX[i],noJugadorY[i]);
        }

 

Como puedes observar, se hace la llamada al método actualizaNPC(), cuyo código tienes a continuación, y que deberás añadir a la clase principal del juego.

    //Método que permite cambiar las coordenadas del NPC en la posición "i",
    //dada una variación "delta" en ambas coordenadas.
    private void actualizaNPC(int i, float delta) {
        if (destinoY[i]>noJugadorY[i]) {
            noJugadorY[i] += delta;
            noJugador[i] = noJugadorArriba;
        }
        if (destinoY[i]<noJugadorY[i]) {
            noJugadorY[i] -= delta;
            noJugador[i] = noJugadorAbajo;
        }
        if (destinoX[i]>noJugadorX[i]) {
            noJugadorX[i] += delta;
            noJugador[i] = noJugadorDerecha;
        }
        if (destinoX[i]<noJugadorX[i]) {
            noJugadorX[i] -= delta;
            noJugador[i] = noJugadorIzquierda;
        }
    }

¡Ejecútalo, tienes el código fuente de la clase principal completa a continuación, y visita el mapa recién poblado! Puedes aumentar la población cambiando el valor de numeroNPCs.
Descarga de MiJuego.java (java - 19987 B) 
2.3.4.6.- Detectando colisiones entre el jugador y los NPC.

Ya vimos en su momento, que la forma más simple de realizar comprobaciones de colisiones entre objetos, es rodear los mismo por un rectángulo o círculo, y detectar si la figura circundante de determinados objetos se solapan. Aunque este forma de detectar colisiones es propensa a dar falsos positivos, ya que, en el caso de los rectángulos cabe la posibilidad de que haya solapamiento entre los dos rectángulos, pero, en realidad, no haya solapamiento entre las propias figuras en sí, con lo que deberíamos hacer comprobaciones adicionales si queremos que las colisiones se detecten de manera más refinada.
Detalle de como colisionan dos objetos animados en el juego, cuando sus rectángulos se solapan.
Elaboración propia. (CC BY-NC)

Las colisiones en libGDX, se pueden gestionar de forma programática, creando el propio algoritmo de colisión, o usando un motor de físicas, como Box2d. En nuestro caso utilizaremos la primera aproximación, usando para ello rectángulos que rodean a los objetos animados que van a colisionar, y detectando si dichos rectángulos se solapan o no.
Para saber más

En el siguiente enlace puedes ver la documentación oficial de libGDX respecto al uso de Box2d en nuestras aplicaciones. Ten en cuenta que la documentación está en inglés.

Uso de Box2d con libGDX (En inglés)

Si quieres ver como usar Box2d con libGDX, de forma práctica, en el enlace que sigue, puedes ver el primer tutorial, de una serie de cuatro, sobre el uso básico de este motor de físicas. Ten en cuenta que este tutorial está en inglés:

Tutorial de motor de físicas con Box2d en LibGDX, parte 1 (En inglés)

Para detectar las colisiones, usando marcos rectangulares en torno a las animaciones del juego, incluiremos un método nuevo al código de nuestra clase principal del juego, que denominaremos detectaColisiones(), y que tendría que ser invocado justo al final de la ejecución del método render():

    private void detectaColisiones() {
        //Vamos a comprobar que el rectángulo que rodea al jugador, no se solape
        //con el rectángulo de alguno de los NPC. Primero calculamos el rectángulo
        //en torno al jugador.
        Rectangle rJugador = new Rectangle(jugadorX,jugadorY,anchoJugador,altoJugador);
        Rectangle rNPC;
        //Ahora recorremos el array de NPC, para cada uno generamos su rectángulo envolvente
        //y comprobamos si se solapa o no con el del Jugador.
        for (int i=0; i<numeroNPCs; i++) {
            rNPC = new Rectangle(noJugadorX[i], noJugadorY[i], anchoNoJugador,altoNoJugador);
            //Se comprueba si se solapan.
            if (rJugador.overlaps(rNPC)){
                //hacer lo que haya que hacer en este caso, como puede ser reproducir un efecto
                //de sonido, una animación del jugador alternativa y, posiblemente, que este muera
                //y se acabe la partida actual. En principio, en este caso, lo único que se hace
                //es mostrar un mensaje en la consola de texto.
                System.out.println("Hay colisión!!!");
            }
        }
    }


Lo normal, cuando se produce una colisión entre el jugador y alguno del resto de objetos del juego, es que se produzca algún evento, que puede pasar por la reproducción de algún efecto de sonido, acompañado de que, por ejemplo, el jugador muera y se acabe la partida actual. Más adelante incluiremos un efecto de sonido cuando se produzca la colisión.
2.3.4.7.- Ajustes de profundidad.

Para terminar con la parte gráfica resolveremos otro problema que aún tenemos pendiente. Recuerda que en el tilesheet aparecían columnas y otras estructuras de varios tiles de alto. Tal y como está ahora el código, un tile o bien bloquea el paso o el jugador pasa por encima:
Efecto de no considerar la profundidad a la hora de dibujar el tilemap.
Captura de pantalla de una aplicación propia.
Tiles que componen la imagen obtenidos de:
 Zeronomous.

Lo ideal sería que pudiéramos hacer que el jugador aparezca detrás de algunos tiles:
Resultado de sí haber considerado la profundidad a la hora de dibujar el tilemap.
Captura de pantalla de una aplicación propia.
Tiles que componen la imagen obtenidos de:
 Zeronomous.

Ten en cuenta que este problema sólo lo vamos a sufrir cuando nuestro juego 2D no use la perspectiva cenital: si los sprites son planos y no tienen altura no se van a solapar si no han colisionado.

Veamos cómo conseguir este comportamiento de una manera sencilla. Lo primero será modificar nuestro tilemap y añadir una nueva capa que llamaremos "Altura". En ella colocaremos la parte superior de los objetos que tengan más de un tile de altura. Fíjate que los tiles que coloquemos en esa capa nunca podrán ser obstáculos para el jugador porque en realidad están a diferente nivel.
Captura de la aplicación Tiled en la que el usuario está colocando tiles en una nueva capa llamada “Altura”.
Captura de pantalla de la aplicación Tiled bajo licencia GNU GPL v2.
Tiles que componen la imagen obtenidos de:
 Zeronomous.

Respecto al código, tendremos que hacer unos pequeños cambios al método render(), el cual quedaría como puedes ver a continuación:

    @Override
    public void render() {
        //Ponemos el color del fondo a negro
        Gdx.gl.glClearColor(0, 0, 0, 1);
        //Borramos la pantalla
        Gdx.gl.glClear(GL20.GL_COLOR_BUFFER_BIT);

        //Trasladamos la cámara para que se centre en el mosquetero.
        camara.position.set(jugadorX, jugadorY, 0f);
        //Comprobamos que la cámara no se salga de los límites del mapa de baldosas,
        //Verificamos, con el método clamp(), que el valor de la posición x de la cámara
        //esté entre la mitad de la anchura de la vista de la cámara y entre la diferencia entre
        //la anchura del mapa restando la mitad de la anchura de la vista de la cámara,
        camara.position.x = MathUtils.clamp(camara.position.x, camara.viewportWidth / 2f,
                anchoMapa - camara.viewportWidth / 2f);
        //Verificamos, con el método clamp(), que el valor de la posición y de la cámara
        //esté entre la mitad de la altura de la vista de la cámara y entre la diferencia entre
        //la altura del mapa restando la mitad de la altura de la vista de la cámara,
        camara.position.y = MathUtils.clamp(camara.position.y, camara.viewportHeight / 2f,
                altoMapa - camara.viewportHeight / 2f);

        //Actualizamos la cámara del juego
        camara.update();
        //Vinculamos el objeto de dibuja el TiledMap con la cámara del juego
        mapaRenderer.setView(camara);
        //Dibujamos las tres primeras capas del TiledMap
        int[] capas = {0,1,2};
        mapaRenderer.render(capas);

        // extraemos el tiempo de la última actualización del sprite y la acumulamos a stateTime.
        stateTime += Gdx.graphics.getDeltaTime();
        //Extraemos el frame que debe ir asociado a al momento actual.
        cuadroActual = (TextureRegion) jugador.getKeyFrame(stateTime);
        // le indicamos al SpriteBatch que se muestre en el sistema de coordenadas
        // específicas de la cámara.
        sb.setProjectionMatrix(camara.combined);
        //Inicializamos el objeto SpriteBatch
        sb.begin();
        //Pintamos el objeto Sprite a través del objeto SpriteBatch
        sb.draw(cuadroActual, jugadorX, jugadorY);

        //Dibujamos las animaciones de los NPC
        for (int i= 0; i < numeroNPCs; i++) {
            actualizaNPC(i,0.5f);
            cuadroActual = noJugador[i].getKeyFrame(stateTime);
            sb.draw(cuadroActual,noJugadorX[i],noJugadorY[i]);
        }

        //Finalizamos el objeto SpriteBatch
        sb.end();
        //Pintamos la cuarta capa del mapa de baldosas.
        capas = new int[1];
        capas[0]= 3;
        mapaRenderer.render(capas);
        //Comprobamos si hay o no colisiones entre en jugador y los NPC
        detectaColisiones();
    }

 

En lugar de usar el método mapaRenderer.render(), sin parámetros,  que dibuja todas las capas, las dibujamos manualmente, usando para ello una versión sobrecargada de ese método, que admite como parámetro un vector de enteros que simbolizan las capas, por su número identificador, que queremos que se rendericen . El truco es renderizar las 3 primeras capas (suelo, decoración y obstáculos), luego todas las animaciones, la del jugador y los NPC, y, por último, la nueva capa.

Los NPC también pueden participar en esto: se dibujan antes de renderizar la última capa y también respetarán los tiles que están a otra altura. Eso sí, ten en cuenta que no se paran ante los obstáculos, con lo que es posible que veas cosas raras cuando pasen por la base de un dibujo de varias alturas.
Imagen en la que se aprecia cómo se pueden dibujar NPC teniendo en cuenta los efectos de profundidad.
Captura de pantalla de una aplicación propia.
Tiles que componen la imagen obtenidos de:
 Zeronomous.

Recuerda que tienes que incluir el nuevo TiledMap, al que has añadido la capa nueva de "Altura", en la carpeta assets del subproyecto android, para que el código nuevo del juego funcione adecuadamente.
2.3.5.- Efectos de sonido y multimedia.
CD de audio sobre el que destaca una nota musical.
 derivative work: KSiOM

Para acabar con esta introducción a los motores 2D veamos cómo agregar música y efectos de sonido a nuestro proyecto. Las capacidades en este ámbito varían entre un motor u otro, aunque la gran mayoría permiten reproducir una canción de fondo mientras los demás sonidos son lanzados a discreción del código específico.

Algo que debemos investigar, antes de encargar al departamento artístico la música o los sonidos, es qué formatos admite nuestro motor y si todos ellos estarán disponibles en las plataformas para las que deseamos lanzar el videojuego.

libGDX nos proporciones varias clases y métodos para reproducir, desde pequeños efectos de sonido, como piezas musicales almacenadas en ficheros de mayor tamaño, que pueden estar almacenados el los dispositivos de almacenamientos. En este sentido, el formato de audio soportado por este framework son: MP3, OGG Vorbis y WAV. Aunque estos sean los formatos soportados, hay que tener en cuenta que no todos tienen soporte en todas las plataformas. En concreto, OGG no es soportado en IOS, así que deberíamos evitar usar este formato, si queremos que ejecutar nuestra aplicación en esta plataforma, aunque si no es así, este es el formato más adecuado, ya que es mucho más completo que los otros dos soportados.

También permite acceder al hardware de audio, tanto en modo lectura, para capturar, por ejemplo, el sonido proveniente de un micrófono, como en escritura, para enviar un determinado audio digital a la salida de audio. El formato de sonido soportado en este caso, es PCM, aunque hay que tener en cuenta que este formato no está soportado en HTML5, y que en Android hay una gran latencia de retardo en la escritura al hardware de sonido.

Todo el acceso a las posibilidades de audio en libGDX, se realiza a través del módulo de audio, que pasa por usar algo parecido a lo que se muestra en el siguiente código:

Audio audio = Gdx.audio;

libGDX pausará y reanudará le reproducción del audio, en caso de que tu aplicación se ponga en pausa y se vuelva a reanudar.

Vamos a ver como reproducir efectos de sonido y música en nuestro juego.

Aunque libGDX soporta el uso de archivos WAV, estos deben tener 16 bits por muestra, si es superior, tendrás que editarlo, con un programa de edición de audio, como por ejemplo Audacity, y modificar su muestreo a ese valor, de lo contrario, obtendrás un error en la carga del archivos de sonido.
2.4.1.- Reproduciendo música.
Nota musical negra con relieve.
 nicu bucule.

Para reproducir sonidos que ocupen algo más de unos segundos, lo mejor es reproducirla a partir de un fichero de disco y no cargar todo el archivo en memoria. Esto nos permitirá reproducir la música de fondo de nuestros juegos, sin tener que ocupar demasiada memoria del dispositivo.

Para poder realizar esto, libGDX proporciona el interfaz Music, y para cargar un fichero de música mp3 en nuestro juego, primero tendremos que añadir un nuevo atributo a la clase principal del mismo:

private Music musica;

En el método create() procederemos a cargar la canción y, si así lo queremos, a ordenar la reproducción:

        //Inicializamos la música de fondo del juego y la reproducimos.
        musica = Gdx.audio.newMusic(Gdx.files.internal("dungeon.mp3"));
        musica.play();

 

Descarga la siguiente canción y cópiala con el nombre dungeon.mp3 a la carpeta assets de tu subproyecto android:
Canción de ejemplo. (mp3 - 1760.57 KB)
CC0 Katana.

¡Así de simple! Hemos de tener en cuenta que la canción se reproducirá solamente una vez y cuando termine, parará. Si necesitamos que se reproduzca indefinidamente tendremos que usar el método musica.setLooping(true).

Aquí mostramos algunos de los métodos más interesantes de la clase Music:
Métodos más interesantes de la clase Music Método	Descripción
void play() 	Reproduce la canción una única vez.
void setLooping(boolean isLooping) 	Hace que se reproduzca la canción en bucle o no, dependiendo del valor del parámetro booleano isLooping.
void stop() 	Finaliza la reproducción abruptamente.
void pause() 	Realiza una pausa en la reproducción.
void resume() 	Continúa la reproducción que había sido pausada.
boolean isPlaying() 	Devolverá true si la canción está en reproducción.
float getVolume() 	Devuelve el volumen de reproducción actual.
void setVolume(float volumen) 	Establece el volumen al indicado por el parámetro volumen (1.0f es el volumen normal).
float getPosition() 	Obtiene el tiempo de reproducción actual en segundos.
void setPosition(float posicion) 	Mueve la reproducción al instante temporal de posicion segundos.
2.4.2.- Efectos de sonido.
Representación de un sonido digitalizado de dos canales.
 Hans Jørn Storgaard Andersen.

El uso de los efectos de sonido es similar al de la música. De hecho, se crean de la misma forma salvo por el hecho de que son instancias de la clase Sound en lugar de Music.

Las diferencias entre ambos son puntuales, y el comportamiento es básicamente idéntico, aunque se permite la reproducción de varias instancias de objetos Sound simultáneamente. La cantidad de sonidos depende del sistema operativo y del hardware, pero normalmente son varias decenas.

Éstos son los algunos de los métodos más destacables de la interfaz Sound:
Métodos más interesantes de la clase Sound Método	Descripción
long play() 	Reproduce el sonido una única vez, y devuelve el id de la instancia de sonido si se hace correctamente y -1 si falla.
long play(float volume) 	Reproduce el sonido una única vez, y devuelve el id de la instancia de sonido si se hace correctamente y -1 si falla. El parámetro representa el volumen y puede tener un valor entre 0 y 1.
long loop() 	Reproduce el sonido en un bucle indefinido, y devuelve el id de la instancia de sonido si se hace correctamente y -1 si falla.
void stop() 	Finaliza la reproducción abruptamente.
void pause()
	Pone en pausa el sonido.
void resume() 	Reanuda la reproducción del sonido puesto previamente en pausa.
void dispose() 	Libera los recursos asignados al sonido.
void setVolume(long soundId, float volume) 	Permite cambiar el volumen de un sonido, dado su identificador como primer parámetro y el volumen como segundo parámetro, con un valor entre 0 y 1.
void setPitch(long soundId,
float pitch) 	

Cambia la velocidad de reproducción del sonido, dado el identificador como primer parámetro, y el segundo parámetro el multiplicador de velocidad.

Los valores posibles para el multiplicador,: 1 == valor por defecto, >1 == más rápido, <1 == más lento, el valor tiene que estar entre 0.5 y 2.0

 

Agreguemos entonces sonido a nuestro proyecto, al que añadiremos, en principio tres efectos de sonido, uno que se reproducirá cuando el jugador se desplaza, de forma que sus pasos tengan el sonido adecuado, otro efecto de sonido que se reproducirá cuando el jugador colisione con uno de los magos rojos que pululan por el mapa, el tercer sonido será el que se reproducirá cuando el jugador colisione con uno de los obstáculos. Empezaremos añadiendo tres nuevos atributos, uno por cada sonido que vamos a añadir al proyecto.

    private Sound sonidoPasos;
    private Sound sonidoColisionEnemigo;
    private Sound sonidoObstaculo;

Antes de seguir con el código, vamos a descargar los archivos de sonido que utilizaremos, los cuales ya sabemos que hay que incluir dentro de la carpeta assets del subproyecto android de nuestro proyecto de juego:
Sonido de los pasos del personaje. (ogg - 8.48 KB)
CC0 Fantozzi.
Sonido de colisión con mago rojo. (ogg - 37.99 KB)
CC-BY-SA 3.0 qubodup.
Sonido de colisión con obstáculos. (wav - 252.46 KB)
CC0 legoluft.

En el método create() procederemos a cargar los archivos de sonido, los cuales, se deberán reproducir cuando se produzca el evento que los tenga que lanzar:

//Inicializamos los atributos de los efectos de sonido.
sonidoColisionEnemigo = Gdx.audio.newSound(Gdx.files.internal("qubodup-PowerDrain.ogg"));
sonidoPasos = Gdx.audio.newSound(Gdx.files.internal("Fantozzi-SandR3.ogg"));
sonidoObstaculo = Gdx.audio.newSound(Gdx.files.internal("wall.wav"));

 

Y ahora, que tenemos los sonidos cargados, ¿en que métodos tendremos que pasa a reproducirlos?. Evidentemente, dependerá de cada uno de ellos:

    El sonido de colisión con un enemigo, deberá reproducirse cuando se determine que se ha producido una colisión entre el jugador y un mago rojo. Como ya sabemos, esa detección se produce en el método detectaColisiones().
    El sonido de los pasos del jugador, deben reproducirse cuando se mueve este, y eso implica incluir su reproducción en dos métodos, que son detectaColisiones() y detectaColisiones().
    El sonido de la colisión del jugador con los obstáculos, deben reproducirse también cuando se mueve este, ya que estas colisiones se verifican en los métodos que permiten que el jugador se mueva, y eso implica incluir su reproducción en los mismos métodos que el sonido anterior.

Descarga el código de la clase principal y comprueba la implementación de los métodos mencionados antes y cómo se ha incluido la reproducción de los efectos de sonido :
Descarga de MiJuego.java (java - 21.76 KB)
Autoevaluación
Pregunta

¿Cuáles de los siguientes métodos de Music no existen en Sound? (marca 2):
Respuestas

Opción 1

void pause().

Opción 2

float getVolume().

Opción 3

boolean IsPlaying().

Opción 4

void loop().

2.4.3.- Índice de recursos sonoros.
Para saber más

Te presentamos una lista de enlaces donde podrás encontrar canciones y/o efectos de sonidos, algunos de los cuáles tienen licencias de uso poco restrictivas.

Música con licencia libre (I).

Música con licencia libre (II).

Música con licencia libre (III).

Efectos de sonido libres (I).

Efectos de sonido libres (II).

Efectos de sonido libres (III).

Efectos de sonido libres (IV).
Fotografía de las teclas de un piano.
  JM
2.3.6- Liberando los recursos de la aplicación.
Icono que recicla elementos a una papelera.
openclipart

Los juegos son aplicaciones que suelen utilizar gran cantidad de recursos de la máquina en la que se ejecuta. Los recursos multimedia que se incluyen en este tipo de aplicaciones, suelen consumir grandes cantidades de memoria. A peores, estos objetos no son manejados de forma automática por el recolector de basura de Java, aunque esto tampoco es que sea lo más deseable.

En realidad, lo que se desea es tener el control más completo posible sobre ciclo de vida de nuestros recursos, de forma que podamos crear los recursos cuando los necesitemos, y podamos borrarlos de memoria cuando ya su ciclo de vida se haya acabado. En este sentido, hay muchas clases en libGDX que representan esos recursos que queremos controlar, y se caracterizan por que todas ellas implementan el interfaz Disposable, que indica que las instancias de esas clases, deben ser borradas de memoria, de forma manual, cuando su vida útil acabe. Para liberar los recursos, usaremos el método dispose() de cada uno de ellos.

Ten en cuenta que si estos recursos no son liberados satisfactoriamente de forma manual, podremos tener serios problemas de pérdidas de memoria y recursos de la máquina, aun cuando el juego haya finalizado.

Los recursos deben ser liberados tan pronto como no sean necesarios, liberando de esa forma la memoria asociada a los mismos. Te en cuenta, que liberar los recursos no implica poner a nulo las referencias a los mismos,  y si intentamos acceder a un recurso liberado, a través de alguna de sus referencias, obtendremos errores de tipo indefinido, por lo que tendrás que borrar también todas las referencias a los recursos liberados.

Algunas de las clases  que tienen que ser liberados sus recursos de forma manual son:

    Bitmap
    BitmapFont
    BitmapFontCache
    SpriteBatch
    SpriteCache
    Music
    Model
    ModelBatch
    ParticleEffect
    Pixmap
    PixmapPacker
    Shader
    Sound
    Stage
    Texture
    TiledMap
    TileMapRenderer

Como puedes comprobar en el anterior listado no exhaustivo, algunas de esas clases las hemos usado en el juego básico que estamos desarrollando, y si no queremos que el equipo donde se ejecute el mismo, tenga posibles pérdidas de memoria, tendremos que liberarlos antes de que el propio juego se cierre. Para ello, usaremos el método dispose() de la clase principal el cual, como ya sabemos, se ejecuta justo antes de que la aplicación sea cerrada, y será en dicho método donde realizaremos las llamadas a los métodos de liberación de dichos recursos, tal como puedes ver en el siguiente código:

    public void dispose () {
        mapa.dispose();
        mapaRenderer.dispose();
        img.dispose();
        sb.dispose();
        musica.dispose();
        sonidoObstaculo.dispose();
        sonidoPasos.dispose();
        sonidoColisionEnemigo.dispose();
    }

Debes conocer

Cuando en una aplicación se utilizan una gran cantidad de objetos, no es recomendable crear objetos sobre la marcha y liberarlos cuando se dejen de utilizar, ya que tanto la creación como borrado de objetos son procesos costosos en tiempo de cómputo. Así, para afrontar estos escenarios, se han introducido técnicas y patrones de diseño que permiten reducir, al mínimo posible, la creación/borrado de objetos. Una de estas técnicas, y la más utilizada en la creación de videojuegos, es la de utilizar pool de objetos.. Puedes ver como utilizar los pool de objetos en libGDX en el siguiente enlace de la referencia oficial de dicho framework. Ten en cuenta que esta información está en inglés:

Pool de objetos con libGDX (en inglés)
2.4.- Soporte de juegos 3D.

Crear juegos con soporte 3D es una tarea compleja y suele requerir la implicación de equipos de desarrollo en los que hayan perfiles diferenciados de tareas, entre las que podemos señalar:

    Diseñadores gráficos.
    Modeladores de objetos 3d.
    Programadores.
    Músicos.
    Etc...

libGDX, aunque se suele utilizar fundamentalmente para crear juegos en 2D, proporciona soporte completo para el desarrollo de juegos 3D, si bien se requería mucho más que el tiempo que disponemos en esta unidad de trabajo para ver sus características fundamentales con ciertas garantías. Aún así, a continuación puedes ver una relación, no exhaustiva, de lo que nos permite hacer:

    Permite la creación y manejo del mundo, que es el entorno donde se desarrolla toda la actividad e interacción de los objetos que componen los juegos.
    Permite la creación y manipulación de modelos, tanto básicos, como pueden ser esferas, cubos, prismas, como otros más complejos, así como importar modelos realizados por otras herramientas más especializadas, como puede ser Blender.
    Permite el uso de materiales y texturas, para representar adecuadamente los distintos modelos y formas, y la manipulación del entorno, de forma que podemos añadir luces de diversos tipos y cámaras con varios tipos de perspectiva.
    Permite crear animaciones 3D, así como otras realizadas con otras aplicaciones, como Blender, y texturizarlas de forma adecuada.
    Tiene soporte de físicas y colisiones en 3D, a través de la librería Bullet.
    Posee un generador de efecto de partículas que permite generar varios tipos de efectos de partículas.

Aunque libGDX tiene un gran soporte de 3D, ten en cuenta que no es una herramienta que permita la manipulación, en un editor gráfico rico, de los distintos objetos y modelos que componen una escena o mundo 3D, como puede ser el caso Unity3D. En este sentido tiene ciertas limitaciones, ya que libGDX está mas orientado al aspecto de manipulación programática de los diversos componentes de la aplicación 3D.

Aquí te dejamos un pequeño vídeo de un juego en 3D realizado con libGDX, para que te hagas una idea de lo que se puede hacer, con el tiempo y recursos adecuados, con este framework.
Канал пользователя WarlockStudio. Tank Combat : Future Battles (Licencia de YouTube estándar)

Para saber más

Si quieres avanzar en los conceptos de desarrollo 3D de libGDX, aquí tienes el enlace a la documentación oficial, dentro de la cual, se encuentran varios tutoriales básicos al respecto. Ten en cuenta que toda esta información está en inglés:

El API de gráficos 3D de libGDX.
2.5.- Despliegue de un proyecto.
Caso práctico
Una caja de cartón con una solapa abierta y la otra cerrada.
GNU General Public License.  GNOME icon artists.

Juan y Ana están de enhorabuena. En tan solo unas horas han realizado un proyecto fantástico durante el cual han aprendido muchas técnicas y conceptos nuevos: desde la preparación de un mapa, hasta el diseño de personajes y objetos, pasando por música y sonidos, por no hablar de la integración de todos esos elementos. Y todo su esfuerzo ha quedado plasmado en una aplicación. Ada ha recibido noticias de que ambos se encuentran satisfechos con sus progresos, así que ha solicitado a Juan que le mande el proyecto terminado para que pueda echarle un vistazo desde el hotel del congreso donde se encuentra alojada.

Y ahí es donde Juan encuentra otro problema, cuando ya no esperaba tener ninguno más: ¿cómo puedo hacerle llegar a Ada el proyecto sin tener que explicarle cómo instalar Android Studio y el motor? ¿Le funcionará con Windows si he desarrollado el proyecto en MacOS X?

La solución pasa por aprender a desplegar el proyecto de forma que pueda ejecutarse en cualquier máquina sin necesidad de instalar nada más.

 
 

De hecho, desplegar la aplicación no resulta complicado una vez aprendemos a colocar las carpetas en su sitio correcto, es más, cada plataforma para la que la que estemos desarrollando la aplicación, tiene una forma específica de despliegue o distribución, y todas ellas se pueden generar usando el sistema Gradle:
Instrucciones de despliegue para las diferentes plataformas Plataforma	Instrucción de despliegue       	Descripción
desktop 	gradlew desktop:dist 	

Se crea un archivo ejecutable Java .JAR localizado en la carpeta desktop/build/libs/. Contiene todo el código necesario de la aplicación, así como todos los recursos contenidos en la capeta android/assets.

Puede ser ejecutado, en cualquier dispositivo que tenga una JVM, bien haciendo doble clic en el mismo o desde línea de comando java -jar jar-file-name.jar.
android 	

gradlew android:assembleRelease
	Se crea un fichero APK sin firmar, en la carpeta android/build/outputs/apk Antes de que pueda ser instalada o publicada, tienes que firmarla.
ios 	

gradlew ios:createIPA
	Se crea un archivo IPA en la carpeta ios/build/robovm que puede ser distribuido en la Apple App Store.
web 	

gradlew html:dist
	

Se compila la aplicación a Javascript y sitúa el resultante Javascript, HTML y los ficheros de recursos en la carpeta html/build/dist/. Para desplegar, sólo tendremos que subir a un servidor web el contenido de la misma.

¡Nosotros hemos terminado con la creación de videojuegos! Pero tú acabas de comenzar una vez que has programado tu primer videojuego. Si así lo deseas, puedes descargar el código fuente final del proyecto que hemos ido desarrollando, en el siguiente enlace:
Código fuente final del proyecto. (zip - 10.96 MB)
Para saber más

En el siguiente enlace puedes ver información oficial de android sobre el proceso de firma de las aplicaciones:

Firmado de aplicaciones android.

