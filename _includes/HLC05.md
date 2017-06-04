
#HLC 05
# Servicios de geolocalización, mapas y sensores en Android.


## 1.- Geolocalización en Android.

¿Qué es es la geolocalización?

La **geolocalización** es la capacidad para obtener la ubicación geográfica real de un objeto, como un radar, un teléfono móvil o un ordenador conectado a Internet. La geolocalización puede referirse a la consulta de una futura ubicación o posicionamiento, o bien para la consulta real de la ubicación o localización de un objeto. El término geolocalización está estrechamente relacionado con el uso de sistemas de posicionamiento, pero puede distinguirse de estos por un mayor énfasis en la determinación de una posición significativa (por ejemplo, una dirección de una calle) y no sólo por un conjunto de coordenadas geográficas dadas en términos de Longitud y Latitud.

Precisamente un aspecto muy interesante que ofrece Android es el API de posicionamiento. Mediante esa API se puede conocer la posición geográfica del dispositivo. Estos servicios se basan principalmente en el GPS, aunque también pueden basarse en telefonía móvil (Cell-ID) y redes Wi-Fi

### 1.1.- Localización y posicionamiento.


La plataforma Android dispone de un interesante sistema de localización y posicionamiento que combina varias tecnologías:

- Sistema de localización basado en satélites como es el **GPS**. Este sistema sólo funciona si disponemos de visibilidad directa de los satélites.
- Sistema de localización basado en redes inalámbricas, como la información recibida de las torres de telefonía celular (**Cell-ID**) y de puntos acceso **Wi-Fi**. Este sistema funciona en el interior de los edificios.

Las APIs disponibles para construir aplicaciones basadas en localización o posicionamiento del dispositivo pueden ser:

- La API de posicionamiento de Android a través las clases del paquete android.location.
- La API de Google Play Services.


Los servicios de posicionamiento de Android se encuentran totalmente integrados en el sistema y son usados por gran variedad de aplicaciones. Por ejemplo, la aplicación ‘Locate’ de Android puede adaptar la configuración del teléfono según donde se encuentre. Podría por ejemplo poner el modo de llamada en vibración cuando estemos en el trabajo.

El sistema de posicionamiento global GPS, fue diseñado inicialmente con fines militares pero hoy en día es ampliamente utilizado para uso civil. Gracias al desfase temporal de señales recibidas por varios de los diferentes satélites desplegados, este sistema es capaz de posicionarnos en cualquier parte del planeta con una precisión de 15 metros.

El GPS es el más preciso pero presenta un inconveniente, solo funciona cuando tenemos visión directa de los satélites, además consume bastante energía de batería y no devuelve la ubicación tan rápido como desean los usuarios. Para solventar este problema, Android combina esta información con la recibida de las torres de telefonía celular y de puntos de acceso WiFi, proporcionando información sobre la ubicación de una manera que funciona en interiores como en exteriores, responde más rápido y utiliza menos energía de la batería. Para obtener la ubicación del usuario en la aplicación, puedes utilizar el GPS y el proveedor de ubicación de red, o sólo uno.

Obtener la ubicación del usuario de un dispositivo móvil puede ser complicado. Hay varias razones por las que una lectura de ubicación (independientemente de la fuente) puede contener errores y ser inexacta, como por ejemplo multitud de fuentes de ubicación y usuario en movimiento.



### 1.2.- Clases para la localización y permisos.



En los iguientes apartados nos vamos a centrar en el paquete android.location.

Los métodos del API de localización requieren de los **permisos**:

- Localización precisa (ACCESS_FINE_LOCATION) que la proporciona el GPS
- Localización imprecisa (ACCESS_COARSE_LOCATION) que la proporciona la telefonía celular y WiFi.

dependiendo del método de localización que se vaya a utilizar.

Algunas clases a destacar del paquete android.location son:

- Location. Clase para representar una localización geográfica.
- LocationManager. Esta clase proporciona acceso a los servicios de localización del sistema a través de APIs que pueden determinar y gestionar la ubicación del dispositivo. No se instancian objetos de forma directa, sino que se utiliza el método getSystemService(Context.LOCATION_SERVICE), que devuelve un objeto LocationManager.

- LocationListener. Esta interface se utiliza para recibir notificaciones de LocationManager cuando el lugar ha cambiado. Los métodos a implementar son:
	- onLocationChanged(Location location). Llamado cuando cambia la ubicación.
	- onProviderDisabled(String provider). Llamado cuando el proveedor no está habilitado
	- onProviderEnabled(String provider). Llamado cuando el proveedor está habilitado por el usuario.
	- onStatusChanged(String provider, int status, Bundle extras). Llamado cuando cambia el estado del proveedor.
- LocationProvider. Superclase abstracta para localizar proveedores de localización. Un **proveedor de ubicación** proporciona informes periódicos sobre la situación geográfica del dispositivo. Cada proveedor tiene un conjunto de criterios bajo los cuales se pueden usar, por ejemplo, algunos proveedores requieren hardware GPS y la visibilidad a un número de satélites, mientras que otros requieren el uso de la radio celular, o el acceso a la red de un proveedor específico, etc. También pueden tener diferentes características de consumo de la batería o los costos monetarios para el usuario. La clase Criteria permite seleccionar los proveedores en base a los criterios especificados por el usuario.
- Criteria. Esta clase permite indicar los criterios de aplicación para la selección de un proveedor de ubicación. Proveedores tal vez ordenados de acuerdo a la precisión, el uso de energía, capacidad de informar altitud, velocidad, y coste monetario.

### 1.3.-Ejemplo de proveedores de localización.

A continuación vas a ver y realizar el siguiente ejemplo de Localización. Consiste en lo siguiente:

La aplicación lee información de localización del dispositivo y la actualiza cada vez que se produce un cambio, mostrando una lista con todos los proveedores de localización disponibles y seleccionando el mejor que encuentra según los requisitos establecidos en la aplicación.

En este ejemplo de posicionamiento se va a utilizar tanto la localización fina o precisa, la que proporciona el GPS, como una menos precisa o la imprecisa, la proporcionada por la telefonía celular y WiFi.

Por tanto necesita los permisos (ACCESS_FINE_LOCATION y ACCESS_COARSE_LOCATION), que habrá que incluir en el fichero AndroidManifest.xml.
```
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />

<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" /> 
```
Se mostrará en modo texto la información obtenida desde el API de localización.

¿Cuál es la idea básica a seguir para construir la aplicación? Es la siguiente:

Se construye una Activity que implemente a LocationListener y se crea un objeto LocationManager.

- Mediante el método creado muestraProveedores() se listarán todos los proveedores de localización disponibles y se seleccionará al mejor.
- Mediante el método creado muestraLocaliza() se visualizará en pantalla una determinada localización.


Para conseguir que se notifiquen cambios de posición hay que llamar al método LocationManager.requestLocationUpdates() y para indicar que se dejen de hacer las notificaciones hay que llamar a LocationManager.removeUpdates(). Si queremos ahorrar batería, nos interesa que se reporten notificaciones solo cuando la aplicación esté activa. Por lo tanto, tenemos que reescribir los métodos onResume() y onPause() con el código apropiado.

El método requestLocationUpdates() dispone de 4 parámetros: el nombre del proveedor, el tiempo entre actualizaciones en ms., la distancia mínima en metros (de manera que si es menor, no se notifica) y un objeto LocationListener

Implementamos los siguientes métodos de LocationListener:

- onLocationChanged() se activará cada vez que cambie la posición.
- Los otros tres métodos pueden ser usados para cambiar de proveedor en caso de que se active uno mejor o deje de funcionar el actual. Sería buena idea llamar de nuevo aquí al método getBestProvider().


### 1.4.-Ejemplo de localización. Mi ubicación.

Con el siguiente ejemplo que vamos a desarrollar aprenderás a activar y obtener información de tu posición con el GPS. De esta manera, podrás mostrar donde estás en la aplicación de mapas. Además, verás la cuestión de cómo geolocalizar nombres de direcciones como por ejemplo “Calle Santos Zárate, Almería” o convertir un par latitud-longitud en una dirección comprensible.

Vas a desarrollar una aplicación que utiliza el GPS para obtener la posición del dispositivo móvil que va contigo, sus coordenadas latitud y longitud. Si lo deseamos, podemos mostrar esta posición en el mapa.

En el dispositivo se recibirán las coordenas (Latitud, Longitud) de la posición del dispositivo móvil que llevas contigo y al pulsar el botón Dónde estoy? se mostrará en un mapa la posición o ubicación actual.

Lo mejor es probar la aplicación en un dispositivo físico real, en el que hayamos activado el GPS y la WiFi

El GPS lo puedes activar desde Ajustes o General (al igual que la WiFi), activando Mi Ubicación o Ubicación. Además, dependiendo de la versión del dispositivo tendrás activados los Servicios de Google Play. En este caso, observa que una vez realizada la localización geográfica del dispositivo, nos permite Explorar los alrededores para mostrarnos información extra posiblemente de interés.

Para poder probar esta aplicación en un emulador o AVD, éste debe tener las Google API instaladas y puedes enviarle las coordenadas desde el Android Device Monitor;

Para ello, activa el Android Device Monitor desde el IDE Android Studio.

Y a continuación ejecutando la aplicación en un emulador, envía unas coordenadas de localización al emulador.

#### 1.4.1.-Crear la aplicación con LocationListener

Para poder usar el GPS, la actividad principal de esta aplicación debe implementar el interfaz LocationListener:
```
public class UD5_MiUbicacion extends Activity implements LocationListener{
```
**Esta interfaz contiene cuatro métodos**:

- onLocationChanged(Location location). Cuando se produzca una variación de posición mayor que la marcada o cuando haya pasado más tiempo que el indicado la aplicación será informada en este método.
- onProviderDisabled(String provider). A través de este método se informa a la aplicación que el proveedor de localización se ha deshabilitado.
- onProviderEnabled(String provider). A través de este método se informa a la aplicación que el proveedor de localización se ha habilitado.
- onStatusChanged(String provider, int status, Bundle extras). A través de este método se informa a la aplicación de cualquier cambio de estado en el proveedor de localización.

Para esta aplicación, el que nos interesa a nosotros es el primero de ellos. Por tanto, el resto simplemente los declararemos, pero no incluiremos código.
Además de declarar los atributos de clase necesarios para guardar las referencias a los elementos de la interfaz (los TextView y el Button), debes incluir lo siguiente:
```
// Referencia al servicio de posicionamiento
     LocationManager locationManager;
     // Para almacenar la latitud y longitud
     double lat;
     double lon;
     TextView latitud, longitud;
```
El método onCreate() de la actividad debe obtener las referencias a los elementos de la interfaz, como es ya habitual. Se implementará el interfaz OnClickListener para el elemento Button y su método onClick debe llamar a un método que llamaremos dondeEstoy() y que implementarás más adelante. Continuando con el método onCreate, aquí también se debe obtener el servicio de posicionamiento llamando al método getSystemService, informándole la constante LOCATION_SERVICE. Este método devolverá un objeto LocationManager.
```
// obtenemos el servicio de posicionamiento
         this.locationManager = (LocationManager) getSystemService(Context.LOCATION_SERVICE);
          if (this.locationManager == null) {
	Toast.makeText(this, "Error al recuperar el GPS",
	Toast.LENGTH_LONG).

          // registramos la recepción de datos del GPS
		this.locationManager.requestLocationUpdates(
                    LocationManager.GPS_PROVIDER, 30000, 20,(LocationListener) this);
```
El método requestLocationUpdates registra la actividad para que sea informada de las novedades de posicionamiento del proveedor, en este caso GPS_PROVIDER, del tiempo mínimo para que se informe de los cambios en milisegundos, de la distancia mínima entre un cambio de posición en metros. Cuando se produce cualquier cambio, se informa mediante el método onLocationChanged que recibe un objeto Location con todos los datos de la nueva posición. La implementación de este método es como sigue:
```
@Override
     public void onLocationChanged(Location location) {          
          // guardamos los valores de latitud y longitud
          this.lat = location.
          this.lon = location.getLongitude();
          // mostramos la posición en pantalla
          this.latitud.setText("Latitud: " + String.valueOf(lat));
          this.longitud.setText("Longitud: " + String.valueOf(lon)); 
     }
```
No nos olvidemos de añadir el permiso adecuado en el manifiesto para tener acceso al GPS.
```
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
```
Podrías probar la aplicación en este momento, pero es necesario informar al emulador de los cambios de posición manualmente. Recuerda que en el emulador lo puedes hacer desde la ventana del Monidor de Android



También podrías hacerlo a través de ficheros GPX y KML (Google Earth). Ejecuta la aplicación MiUbicacion en el emulador y envía valores de posición a través de esta ventana. La aplicación debería mostrar estos cambios automáticamente.


Recuerda que nos falta implementar el método dondeEstoy() , que se ejecuta cuando el usuario pulsa sobre el botón. Este método debe crear un Intent para iniciar la actividad de mapas, mostrando la posición actual, dada por la latitud y la longitud en la misma. El código de este método es el siguiente:
```
public void onClickDondeEstoy(View view) {
          // Creamos el Intent para abrir la aplicación de mapas
          Intent i = new Intent();
          i.setAction(Intent.ACTION_VIEW);
          Uri uri = Uri.parse("geo:" + this.lat + "," + this.lon);
          i.setData(uri);
          startActivity(i);
     }
```
Y el permiso para acceder a Internet en el manifiesto de la aplicación:
```
<uses-permission android:name="android.permission.INTERNET" />
```

### 1.5.-Ejemplo de posicionamiento. Llévame allí.

La aplicación LlévameAllí recibe información de una dirección en un cuadro de texto. Esta dirección puede ser tanto una dirección postal como una posición latitud-longitud. A través de un objeto Geocoder se obtendrá toda la información de esta dirección. 

- Los valores de latitud y longitud deben estar comprendidos entre [-90, 90] y [-180, 180] respectivamente.
- El elemento CheckBox se utiliza para informar de que el valor introducido en el cuadro de texto es una dirección postal o una posición física.
- El botón Geocode toma la dirección introducida en el cuadro de texto y obtiene una lista de objetos Address, además, muestra la información en un elemento TextView. El estiquetado como Resultado:
- El botón Llévame Allí hace la conversión de la dirección introducida para obtener el objeto Address y posteriormente abre la aplicación de mapas informándole de la latitud y la longitud de esta dirección.

Para mostrar un ejemplo de conversión de direcciones, si se introduce por ejemplo la dirección postal “Calle Santos Zárate 10, Almería” y se pulsa sobre el botón Geocode.

La conversión de la dirección se realiza por medio de un objeto Geocoder.

Este objeto dispone de dos métodos:

- uno para convertir direcciones postales, getFromLocationName, y
- otro para convertir posiciones físicas, getFromLocation.

Ambos métodos devuelven una lista de objetos Address. Este objeto contiene información como el código postal, la provincia, el país, la latitud y longitud, etc.

Implementamos el siguiente método para hacer obtener un objeto Address a partir de una dirección:
```
public  Address convertirGeocode(String direccion, boolean esDireccion){
 //lista de direcciones obtenidas por Geocoder
 List<Address> direcciones=null;
 //Construimos el objeto Geocoder
 Geocoder geocoder = new Geocoder(this);
 //Es una dirección postal
 if (esDireccion){
 try {
direcciones = geocoder.getFromLocationName(direccion, 1);
} catch (IOException e) {
e.printStackTrace();
}
 //Es una posición física
 } else{
 //La latitud y longitud separada por comas ",".
 String [] coordenadas = direccion.split(",");
 if (coordenadas!=null && coordenadas. length==2){
 try {
direcciones = geocoder.getFromLocation(Double. parseDouble(coordenadas[0]),
Double. parseDouble(coordenadas[1]), 1);
} catch (NumberFormatException e) {
e.printStackTrace();
} catch (IOException e) {
e.printStackTrace();
}
 }
 }
 //Devolvemos solo el primer elemento de la lista
 if (direcciones!=null  && direcciones.size()>0)
 return direcciones.get(0) ;
 else
 return null ;
}
```
El método convertirGeocode recibe dos parámetros, un objeto String con la dirección a convertir y un valor boolean informando si la dirección es una dirección postal (true) o una posición física (false). Con este método debemos de ser capaces de concluir con éxito la aplicación LlévameAllí.

Si una vez incluida la dirección postal o bien las coordenadas físicas pulsamos sobre el botón Lllevame Allí, se abrirá la aplicación de mapas para indicar la localización o posición indicada.

## 2.- Los mapas de Google.

Google Maps nos proporciona un servicio de cartografía online que podremos utilizar en nuestras aplicaciones Android.

Además de simplemente mostrar mapas en tus aplicaciones (como hemos hecho hasta ahora a través de Intents), con ella también podremos incorporar estos mapas a nuestras propias aplicaciones, e interaccionar con ellos para que hagan cosas interesantes.

Entre otras cosas, la primera versión de esta API (v1) permitía:

- Cambiar las vistas de los mapas.
- Obtener la latitud y longitud de ubicaciones que aparezcan en el mapa.
- Realizar geocodificación y geocodificación inversa sobre puntos del mapa (traduciendo una dirección en latitud y longitud y viceversa).
- Añadir marcadores a los mapas.


Pero esta API fue declarada obsoleta el 2 de diciembre de 2012, y fue sustituida por una nueva versión (v2), que entre sus principales novedades permite:

- Integración con los Servicios de Google Play (Google Play Services) y la Consola de API.
- Utilización a través de un nuevo tipo específico de Fragment (MapFragment), una mejora muy esperada por muchos programadores.
- Utilización de mapas vectoriales, lo que repercute en una mayor velocidad de carga y una mayor eficiencia en cuanto a uso de ancho de banda.
- Mejoras en el sistema de caché, lo que reducirá en gran medida las famosas áreas en blanco que tardan en cargar.
- Los mapas son ahora 3D, es decir, podremos mover nuestro punto de vista de forma que lo veamos en perspectiva.

Al margen de las novedades generales, como desarrolladores lo que más nos interesa es el cambio del componente utilizado para la inclusión de los mapas en nuestra aplicación.

Con la versión v1 de esta API para incluir un mapa en la aplicación había que utilizar un control llamado MapView, que además requería que la actividad contenedora fuera de otro tipo especial llamado MapActivity.

**Con la nueva API v2 nos olvidamos de estos dos componentes, y pasamos a tener sólo uno; en concreto, un nuevo tipo específico de objeto Fragment llamado MapFragment (SupportMapFragment, si quieres que tu programa se ejecute en dispositivos con una API anterior a la 3.0).**

Entre otras cosas, esto nos permitirá añadir uno o varios mapas (esto también es una novedad) a cualquier actividad, y disfrutar además de todas las ventajas del uso de los objetos Fragment [para los dispositivos con versiones anteriores a la 3.0, donde estamos obligados a utilizar un tipo especial de Activity llamado FragmentActivity (compatible con Fragment).].

### 2.1.-Requisitos para trabajar con Google Maps.

**1.- Paquete Google Play Services**


Puesto que la API v2 de Google Maps se proporciona como parte del SDK de Google Play Services, lo primero que tenemos que hacer es incorporar previamente a nuestro entorno de desarrollo dicho paquete. Para ello:

- Accede desde Android Studio al Android SDK Manager, y comprueba desde la pestaña SDK Tools si tienes el paquete descargado, en otro caso descarga el paquete llamado “Google Play Services”.



**2.- Habilitar API de Google Maps en la Consola de Google. (Necesaria una cuenta de correo gmail)**

Es necesario que tengas una cuenta de correo válida de Gmail, para a través de ella acceder a la **API Google Consola**, desde dónde Google hará la generación de la **API KEY**.

El enlace de acceso es el siguiente: https://code.google.com/apis/console

**NOTA**. Durante el propio proceso de creación de un proyecto en Android Studio para una App con plantilla de Google maps se facilita el enlace de acceso a la API Google Console, habilitando la API Google Maps v2 para la obtención de la APY KEY.

Básicamente, una vez que accedas y te valides con una cuenta de correo Gmail en la API Google Console, habrá dos opciones:

1. Si es la primera vez que utilizamos la API de Google Console, antes, posiblemente, te pedirá que crees un proyecto que Google utiliza para realizar un seguimiento del uso de la API. Hacemos clic en Create Project. La consola creará un nuevo proyecto llamado API Project. En la página siguiente, este nombre aparece en la esquina superior izquierda.
2. Si ya estás usando la API de Google Console, inmediatamente se ve una lista de los proyectos existentes y los servicios disponibles.

Debes habiltar el servicio Google Maps Android API v2.

**3.- Obtener una API Key para Google Maps v2**

Toda aplicación Android debe ir firmada para poder ejecutarse en un dispositivo, tanto físico como emulado. Este proceso de firma será uno de los pasos que tendremos que hacer siempre antes de distribuir públicamente una aplicación.

Adicionalmente, durante el desarrollo de la misma, para realizar pruebas y la depuración del código, y aunque no hayamos sido conscientes de ello hasta ahora, también estamos firmando la aplicación con un **“certificado de pruebas”**.

En el caso de un sistema Windows, el certificado de pruebas está en la ruta “**C:\Users\\.android\debug.keystore**”.

Android Studio nos va a dar de forma automática la huella o firma de prueba que necesitamos para generar la API KEY y poder utilizar los Google Maps, en el momento en que creemos una App con la plantilla de Google Maps

que encontrarás en el **fichero res\values\google_maps_api.xml**

y es un tipo de huella SHA1 similar a la siguiente: 8A:87:D9:5A:52:AD:A5:91:E3:3F:72:9B:9A:35:9D:7B:D1:61:D4:4C


A partir de esta firma, Google nos proporciona una API KEY que debemos copiar en el fichero anterior y que quedará registrada en el manifiesto de nuestra aplicación.

Esta API KEY va asociada a:

- un nombre concreto de paquete de proyecto, y
- a un equipo de desarrollo,

por lo que la aplicación que desarrolles sólo la podrás ejecutar en tu equipo con esa API KEY.

Además, todos los ejemplos que hagas, los vas a ir renombrando para utilizar el mismo paquete, ya que la API KEY generada va asociada también a un paquete concreto y así no tendrás que generar más API KEY.


### 2.2.- Crear una aplicación con Google Maps.

Sigue los siguientes pasos para crear tu primera aplicación con la API de Google Maps, que sólo consistirá en incluir un mapa de Google:


1.- Crea un nuevo proyecto Android con nombre de paquete com.pms.mapasgoogle y nombre de Activity principal CrearMapaActivity y con la plantilla de los mapas de Google


2.- Una vez creada la App, la primera pantalla que te mostrará Android Studio es la del fichero res\values\google_maps_api.xml(debug)

- La dirección web de la API Google Consola a la que debes acceder con una cuenta de gmail para habilitar la API Google Maps v2 y poder generar la API KEY para tu App de mapas.
- Te proporciona la huella SHA1 junto al nombre del paquete de tu aplicación (**huella;paquete**) que es la información necesaria que debes proporcionar en la Google Consola para generar la API KEY.
- Te indica el lugar, dentro de ese fichero, en el que debes copiar la API KEY generada. Una vez copiada, se sincroniza esta información con el menifiesto de tu aplicación.

#### 2.2.1.- Obtener la API KEY.

3.- Copia y pega la dirección web o URL de acceso a la API Google Consola en tu navegador y accede con tu cuenta de gmail. Te aparecerá la siguiente pantalla, como la imagen de la izquierda, en la que debes acceptar la creación de un nuevo proyecto.

Tras ello se mostrará una pantalla, como la imagen de la derecha, que te indicará que la API se ha habilitado y debes pulsar sobre credenciales.

4.- Observa que en la siguiente pantalla, aparece tu huella SHA1 y el paquete de tu proyecto, valores con los que se creará tu Clave de API de Android o API KEY. Pulsa en crear.

Tras ello, la siguiente pantalla, te muestra el valor de la API KEY generada, valor que debes copiar en el lugar apropiado de tu fichero res\values\google_maps_api.xml(debug).

5.- Copia el valor de API KEY, tal como te indica la imagen de la izquierda y pega en el lugar a propiado de tu fichero res\values\google_maps_api.xml(debug).

A continuación, si ejecutas tu aplicación en un emulador obtendrás un resultado similar al siguiente. (En este caso se ha centrado el mapa en la localización de Almería-España)

Y ¿que contendio tiene los ficheros de Layout, el Manifiesto y la Activity principal de la aplicación?

#### 2.2.2.- Ficheros de la aplicación de mapas.

A continuación vas a ver los fichros que se han generado en tu aplicación de mapas.

**1.- Fichero res\values\google_maps_api.xml(debug).**

De este fichero ya sabes su contenido, pues es justo en el que has puesto la API KEY generada para tu aplicación de mapas.


**2.- Fichero AndroidManifest.xml.**

En este fichero se ha incluido de forma automática los permisos necesarios:
```
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
```
y la referencia a la API KEY generada:
```
<!--
             The API key for Google Maps-based APIs is defined as a string resource.
             (See the file "res/values/google_maps_api.xml").
             Note that the API key is linked to the encryption key used to sign the APK.
             You need a different API key for each encryption key, including the release key that is used to
             sign the APK for publishing.
             You can define the keys for the debug and release targets in src/debug/ and src/release/. 
        -->
        <meta-data
            android:name="com.google.android.geo.API_KEY"
            android:value="@string/google_maps_key" />
```
Donde "@string/google_maps_key" es justo la API KEY obtenida y que has copiado al fchero de recursos:
```
<string name="google_maps_key" templateMergeStrategy="preserve"
   translatable="false">AIzaSyCHs4CMYsRAN_3YaJ2rXpOVUhgdr6AwlAk</string>
</resources>
```
**3.- Fichero XML del Layout (res\layout\....xml)**
```
<fragment xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:map="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/map"
    android:name="com.google.android.gms.maps.SupportMapFragment"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".CrearMapaActivity" />
```
**4.- Fichero .java con Activity principal.**

Por defecto las coordenas de Latitud, Longitud señalan a Sydney. Las puedes cambiar para que señalen a Almería, tal y como se ha hecho en el código que te mostramos a continuación:
```
public class CrearMapaActivity extends FragmentActivity implements OnMapReadyCallback {
    private GoogleMap mMap;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_maps);
        // Obtain the SupportMapFragment and get notified when the map is ready to be used.
        SupportMapFragment mapFragment = (SupportMapFragment) getSupportFragmentManager()
                .findFragmentById(R.id.map);
        mapFragment.getMapAsync(this);
    }

@Override
    public void onMapReady(GoogleMap googleMap) {
        mMap = googleMap;
        // Add a marker in Sydney and move the camera
        //LatLng sydney = new LatLng(-34, 151);
        LatLng sydney = new LatLng(36.8681428,-2.5134105);
        mMap.addMarker(new MarkerOptions().position(sydney).title("Marcador en Almería"));
        mMap.moveCamera(CameraUpdateFactory.newLatLng(sydney));
    }
} 
```


### 2.3.-Interaccionar con el objeto GoogleMap.

En esta segunda aplicación vamos a hacer un repaso de las opciones básicas de los nuevos mapas: captura emulador con mapa de google

-  Elegir el tipo de mapa a mostrar,
- Movernos por él mediante código, y
- Obtener los datos de la posición actual.

En la Google Maps v2 todas las operaciones se realizan directamente sobre un objeto GoogleMap.

Este objeto lo recibe como parámetro el método onMapReady() cuando el mapa está listo para mostrarse en pantalla.

Aprovecharemos este hecho para asignarlo a una variable de la aplicación y así poder utilizarlo y gestionarlo en otros métodos de la App:
```
@Override
public void onMapReady(GoogleMap googleMap) {
    mMap = googleMap;
```
Una vez obtenida esta referencia a nuestro objeto GoogleMap podremos realizar sobre él la mayoría de las acciones básicas del mapa.

Así por ejemplo, para **modificar el tipo de mapa mostrado** podremos utilizar una llamada a su método setMapType(), pasando como parámetro el tipo de mapa:

MAP_TYPE_NONE: vista en blanco del mapa.
MAP_TYPE_SATELLITE: vista por satélite.
MAP_TYPE_NORMAL: vista por defecto, mapa básico con carreteras.
MAP_TYPE_HYBRID: vista por satélite y normal.
MAP_TYPE_TERRAIN: vista de campo sin carreteras.

Para nuestro ejemplo vamos a utilizar una variable que almacene el tipo de mapa actual (en una variable entera, vista, que toma los valores de 0 a 4, declarada inicialmente como private int vista = 0), y habilitaremos varias opciones de menú para ir alternando entre las distintas opciones. El método que cambia de vista quedará de la siguiente forma:
```
private void alternarVista() {
        String vista=null;
        // establece la siguiente a la actual
        vistaId =++vistaId %5;
        switch (vistaId) {
            case 0:
                mMap.setMapType(GoogleMap.MAP_TYPE_HYBRID);
                vista="MAP_TYPE_HYBRID";
                break;
            case 1:
                mMap.setMapType(GoogleMap.MAP_TYPE_NONE);
                vista="MAP_TYPE_NONE";
                break;
            case 2:
                mMap.setMapType(GoogleMap.MAP_TYPE_NORMAL);
                vista="MAP_TYPE_NORMAL";
                break;
            case 3:
                mMap.setMapType(GoogleMap.MAP_TYPE_SATELLITE);
                vista="MAP_TYPE_SATELLITE";
                break;
            case 4:
                mMap.setMapType(GoogleMap.MAP_TYPE_TERRAIN);
                vista="MAP_TYPE_TERRAIN";
                break;
        }
        //muestra su nombre
        Toast.makeText(ControlarMapa.this, "Vista: "+ vista, Toast.LENGTH_SHORT).show();
    }
```

#### 2.3.1.- Movimiento sobre el mapa.

En cuanto al movimiento sobre el mapa, podremos movernos libremente por un espacio 3D. De esta forma, podremos hablar de:captura emulador Android con mapa

- latitud-longitud (target),
- zoom,
- orientación (bearing) y
- ángulo de visión (tilt).

La manipulación de estos dos últimos parámetros unida a la posibilidad actual de ver edificios en 3D de muchas ciudades, nos abren un mundo de posibilidades.

El movimiento de la cámara se va a realizar siempre mediante la construcción de un objeto CameraUpdate con los parámetros necesarios. Para los movimientos más básicos, como la actualización de la latitud y longitud o el nivel de zoom podremos utilizar la clase CameraUpdateFactory, y sus métodos estáticos que nos facilitarán un poco el trabajo.

Así por ejemplo, **para cambiar sólo el nivel de zoom**, podremos utilizar los siguientes métodos para crear nuestro objeto CameraUpdate:

- CameraUpdateFactory.zoomIn() que aumenta en 1 el nivel de zoom.
- CameraUpdateFactory.zoomOut() que disminuye en 1 el nivel de zoom.
- CameraUpdateFactory.zoomTo(nivel_de_zoom) que establece el nivel de zoom.


Por su parte, para **actualizar sólo la latitud-longitud** de la cámara podremos utilizar:

- CameraUpdateFactory.newLatLng(lat,long) que establece la LatLng expresadas en grados.


Si queremos modificar los dos parámetros anteriores de forma conjunta, también tendremos disponible el método CameraUpdateFactory.newLatLngZoom(lat,long,zoom) que establece la LatLng y el zoom.

Para **movernos lateralmente por el mapa** (panning) podríamos utilizar los métodos de scroll:

    - CameraUpdateFactory.scrollBy(scrollHorizontal,scrollVertical)


donde los scroll vendrán expresados en pixeles.

Tras construir el objeto CameraUpdate con los parámetros de posición tendremos que llamar a los métodos moveCamera() o animateCamera() de nuestro objeto GoogleMap, dependiendo de si queremos que la actualización de la vista se muestre directamente o de forma animada.

- Por ejemplo, si queremos centrar la vista en España en vista satélite escribimos:
```
// centra España en vista satélite
camUpd = CameraUpdateFactory.newLatLng(new LatLng(40.41, -3.69));
mapa.moveCamera(camUpd);
mapa.setMapType(GoogleMap.MAP_TYPE_SATELLITE);
``` 
    mientras que para verla en vista normal animada, con un zoom x5 ponemos:
```
// centra España con zoom x5 en vista normal animada
camUpd = CameraUpdateFactory.newLatLngZoom(
new LatLng(40.41, -3.69), 5f);
mapa.animateCamera(camUpd);
mapa.setMapType(GoogleMap.MAP_TYPE_NORMAL);
``` 

Además de los movimientos básicos que te hemos comentado, si quieres modificar los demás parámetros de la cámara o varios de ellos simultáneamente tendrás disponible el método más general CameraUpdateFactory.newCameraPosition(), que recibe como parámetro un objeto de tipo CameraPosition. Este objeto los construiremos indicando todos los parámetros de la posición de la cámara a través de su método Builder() de la siguiente forma:
```
// centra la Alcazaba de Almería en vista híbrida
LatLng alcazaba = new LatLng(36.840835, -2.471172);
camPos = new CameraPosition.Builder().target(alcazaba)
// con zoom x19
.zoom(19)
// orientación noreste (o giro de 45 grados sexagesimales 
// este -ver la brújula arriba a la izquierda)
.bearing(45)
// punto de vista bajo para ver más suelo (70 grados
// sexagesimales con respecto a la vertical)
.tilt(80).build();
camUpd = CameraUpdateFactory.newCameraPosition(camPos);
mapa.animateCamera(camUpd);
mapa.setMapType(GoogleMap.MAP_TYPE_HYBRID);
```
 

Como has podido comprobar, mediante este mecanismo podemos modificar todos los parámetros de posición de la cámara (o sólo algunos de ellos) al mismo tiempo. En nuestro caso de ejemplo hemos centrado la vista híbrida del mapa sobre la Alcazaba de Almería, con un nivel de zoom de 19, una orientación de 45 grados para que el noreste esté hacia arriba, y un ángulo de visión de 80 grados para que tengamos algo de perspectiva en 3D.

Como puedes ver, en esta nueva versión de la API se facilita bastante el posicionamiento dentro del mapa, y el uso de las clases CameraUpdate y CameraPosition resulta bastante intuitivo.

Acabas de ver cómo modificar nuestro punto de vista sobre el mapa. Pero si ahora el usuario se mueve de forma manual por él, **¿cómo podemos conocer la nueva posición de la cámara?**

Pues igual de fácil, mediante el método getCameraPosition() que nos devuelve un objeto CameraPosition como el que ya conocíamos. Accediendo a los distintos métodos y propiedades de este objeto podemos conocer con exactitud la posición de la cámara (propiedad target), la orientación, y el nivel de zoom:
```
// muestra las coordenadas de la posición actual de la cámara
camPos = mapa.getCameraPosition();
LatLng pos = camPos.target;
Toast.makeText(this,
"(Lat: " + pos.latitude + ", Lng: " + pos.longitude + ")",
Toast.LENGTH_LONG).show();
```
Podemos integrar de manera sencilla todas estas operaciones en el layout del menú:
```
<menu xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto">
    <item
        android:id="@+id/menu_alcazaba"
        app:showAsAction="ifRoom|withText"
        android:title="@string/menu_alcazaba" />
    <item
        android:id="@+id/menu_posicion"
        app:showAsAction="ifRoom|withText"
        android:title="@string/menu_posicion" />
    <item
        android:id="@+id/menu_spain"
        app:showAsAction="ifRoom|withText"
        android:title="@string/menu_spain" />
    <item
        android:id="@+id/menu_spain_zoom"
        app:showAsAction="ifRoom|withText"
        android:title="@string/menu_spain_zoom" />
    <item
        android:id="@+id/menu_vista"
        app:showAsAction="ifRoom|withText"
        android:title="@string/menu_vista" />
</menu>
```


### 2.4.- Capturar eventos.

El objeto GoogleMap soporta directamente los eventos de clic (onMapClick), clic largo (onMapLongClick), y un evento de movimiento de cámara (onCameraChange), de manera que podemos implementarlos de la forma habitual mediante su método set correspondiente.

**Capturar el evento de pulsación corta y larga** (Click y LongClick)


Podemos implementar el evento onMapClick llamando al método setOnMapClickListener() con un nuevo Listener, y luego sobrescribir el método onMapClick(). Este método recibe como parámetro, en forma de objeto LatLng, las coordenadas de latitud y longitud sobre las que ha pulsado el usuario.

Si quisiéramos traducir estas coordenadas físicas en coordenadas en pantalla podríamos utilizar un objeto Projection, obteniéndolo a partir del mapa a través del método getProjection(), y posteriormente llamando a toScreenLocation() para obtener las coordenadas (x,y) de pantalla donde el usuario pulsó.

Así, por ejemplo, si quisiéramos mostrar un Toast con todos estos datos cada vez que se pulse sobre el mapa podríamos hacer lo siguiente:
```
 mMap.setOnMapClickListener(new GoogleMap.OnMapClickListener() {
            public void onMapClick(LatLng point) {
                Projection proj = mMap.getProjection();
                Point coord = proj.toScreenLocation(point);
 

                Toast.makeText(
                        EventosMapa.this,
                        "Click
" + "Lat: " + point.latitude + "
" + "Lng: "
                                + point.longitude + "
" + "X: " + coord.x
                                + " - Y: " + coord.y, Toast.LENGTH_SHORT)
                        .show();
            }
        });
```
 


De forma similar puedes implementar el evento de pulsación larga, con la única diferencia de que lo debes asignar mediante setOnMapLongClickListener(), y sobrescribir el método onMapLongClick():
```
/**
* gestiona el evento onMapLongClick
*/
        mMap.setOnMapLongClickListener(new GoogleMap.OnMapLongClickListener() {
            public void onMapLongClick(LatLng point) {
                Projection proj = mMap.getProjection();
                Point coord = proj.toScreenLocation(point);
 

                Toast.makeText(
                        EventosMapa.this,
                        "Click Largo
" + "Lat: " + point.latitude + "
"
                                + "Lng: " + point.longitude + "
" + "X: "
                                + coord.x + " - Y: " + coord.y,
                        Toast.LENGTH_SHORT).show();
            }
        });
```
**Capturar el evento de movimiento de cámara.**

También puedes capturar el evento de cambio de cámara, de forma que puedes realizar determinadas acciones cada vez que el usuario se mueve manualmente por el mapa, desplazándolo, haciendo zoom, o modificando la orientación o el ángulo de visión. Este evento lo asignaremos al mapa mediante su método setOnCameraChangeListener() y sobrescribiendo el método onCameraChange(). Este método recibe como parámetro un objeto CameraPosition del que podemos recuperar la información deseada.

De esta forma, para mostrar un Toast con esta información debes hacer lo siguiente:
```
/**
* gestiona el evento onCameraChange
*/
        mMap.setOnCameraChangeListener(new GoogleMap.OnCameraChangeListener() {
            public void onCameraChange(CameraPosition position) {
                Toast.makeText(
                        EventosMapa.this,
                        "Cambio Cámara
" + "Lat: " + position.target.latitude
                                + "
" + "Lng: " + position.target.longitude
                                + "
" + "Zoom: " + position.zoom + "
"
                                + "Orientación: " + position.bearing + "
"
                                + "Ángulo: " + position.tilt,
                        Toast.LENGTH_SHORT).show();
            }
        });
```

### 2.5.- Marcar puntos en el mapa.

Marcar puntos en el mapa.

Rara es la aplicación Android que hace uso de mapas sin utilizar marcas para resaltar determinados puntos en el mapa. Esta funcionalidad está integrada en la propia vista del mapa, y agregar un marcador resulta tan sencillo como llamar al método addMarker(), pasándole la posición (en forma de objeto LatLng) y el texto a mostrar en la ventana de información del marcador.

En nuestra aplicación de ejemplo añadiremos un menú de forma que cuando lo pulsemos se añada automáticamente un marcador sobre España, con el texto “País: España”.

Veamos cómo escribir un método auxiliar que nos ayuda a hacer esto pasándole las coordenadas de latitud y longitud:
```
/**
* coloca un marcador sobre España
*/
    private void marcaSpain() {
        mMap.addMarker(new MarkerOptions().position(new LatLng(40.5, -3.5))
                .title("País: España"));
    }
```
Así de sencillo, basta con llamar al método addMarker() pasando como parámetro un nuevo objeto MarkerOptions sobre el que establecemos la posición del marcador y el texto.

Ya que estamos con los marcadores podemos escribir código para el evento onMarkerClick, que como su propio nombre indica se produce al hacer clic en el marcador que acabamos de agregar:
```
/**
* gestiona el evento onMarkerClick
*/
        mMap.setOnMarkerClickListener(new GoogleMap.OnMarkerClickListener() {
            public boolean onMarkerClick(Marker marker) {
                Toast.makeText(EventosMapa.this,
                        "Marcador pulsado:
" + marker.getTitle(),
                        Toast.LENGTH_SHORT).show();
                return false;
            }
        });
```


### 2.6.- Dibujar líneas en el mapa.

También podemos dibujar líneas sobre el mapa, tanto para trazar rutas como para delimitar o resaltar zonas de interés para nuestra aplicación.

Para dibujar una linea lo primero que tendremos que hacer será crear un nuevo objeto PolylineOptions, sobre el que añadiremos utilizando su método add(), las coordenadas (latitud, longitud) de todos los puntos que conformen la linea.

Tras esto, estableceremos el grosor y color de la linea llamando a los métodos width() y color() respectivamente; y por último, añadiremos la linea al mapa mediante su método addPolyline(), pasándole el objeto PolylineOptions recién creado. En resumen:
```
// Dibujo con Lineas
PolylineOptions lineas = new PolylineOptions()
.add(new LatLng(45.0, -12.0)).add(new LatLng(45.0, 5.0))
.add(new LatLng(34.5, 5.0)).add(new LatLng(34.5, -12.0))
.add(new LatLng(45.0, -12.0));
lineas.width(8);
lineas.color(Color.RED);
mapa.addPolyline(lineas); 
```
Este mismo cuadrado (por ser una línea cerrada) podemos dibujarlo también mediante el objeto PolygonOptions. Para ello crearíamos un nuevo objeto PolygonOptions y añadiremos las coordenadas de sus puntos en el sentido de las agujas del reloj. En este caso no es necesario cerrar el circuito (es decir, que la primera coordenada y la última fueran iguales) ya que se hace de forma automática.

Ahora, el ancho y color de la linea los estableceríamos mediante los métodos strokeWidth() y strokeColor(). Y el dibujo final del polígono sobre el mapa lo haríamos mediante addPolygon(). El código es:
```
// Dibujo con polígonos
PolygonOptions rectangulo = new PolygonOptions().add(new LatLng(45.0,
-12.0), new LatLng(45.0, 5.0), new LatLng(34.5, 5.0),
new LatLng(34.5, -12.0), new LatLng(45.0, -12.0));
 
rectangulo.strokeWidth(8);
rectangulo.strokeColor(Color.RED);

mapa.addPolygon(rectangulo);
```

## 3.- Sensores.

Bajo la denominación de sensores se engloba un conjunto de dispositivos con los que podremos obtener información del mundo exterior (en este conjunto no se incluye la cámara, el micrófono o el GPS). Como se verá en este apartado todos los sensores se manipulan de forma homogénea. Son los dispositivos de entrada más novedosos que incorpora Android y con ellos podremos implementar formas atractivas de interacción con el usuario

Para el manejo de los diferentes sensores disponibles es necesario hacer uso de estas clases:

- Sensor, que representa al sensor en concreto que vasmos a utilizar.
- SensorManager, que nos permite acceder a los sensores del dispositivo y la Interfaz.
- SensorEventListener, que registra los cambios hechos en el sensor indicado. Con eso podemos empezar a registrar los cambios hechos en los sensores


### 3.1.- Principales sensores.

Algunos de los principales sensores de un dispositivo móvil podemos decir que son:

- Acelerómetro.
- Sensor de movimiento.
- Orientación.
- Giroscopio.
- Proximidad.
- Temperatura.

De algunos de ellos verás ejemplos en los siguientes apartados.

Con la clase Sensor se pueden manipular los sensores. Algunos de los métodos públicos de la clase Sensor son:

- public float getMaximumRange() => Rango máximo en las unidades del sensor.
- public String getName() => Nombre del sensor.
- public float getPower() => Potencia (mA) usada por el sensor mientras está en uso.
- public float getResolution() =>Resolución en las unidades del sensor.
- public int getType() =>Tipo genérico del sensor.
- public String getVendor() =>Fabricante del sensor.
- public int getVersion() =>Versión del sensor.

La clase SensorManager tiene además tres métodos (getInclination, getOrientation y getRotationMatrix), usados para calcular transformaciones de coordenadas.

Seguro que te estarás preguntando, ¿qué sensores soporta mi dispositivo Android?

Para ello puedes crear una simple aplicación que al ejecutarla en tu dispositivo te dirá el resultado. 
```
**archivo XML del Layout**
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
  tools:context="com.pms.listarsensores.listarsensores.ListarSensores">


    <TextView
        android:id="@+id/listado"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="" />
</RelativeLayout>
```
**archivo .java de la Activity principal**

Recuerda incluir los import de la aplicación mediante la combinación de teclas Alt+Intro
```
public class ListarSensores extends AppCompatActivity {
    private TextView etiqueta;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_listar_sensores);
        etiqueta = (TextView) findViewById(R.id.listado);
        /* Usar getSystemService() con la constante SENSOR_SERVICE y obtener
        el objeto sensorManager  que accederá a la lista de servicios del sistema.*/
        SensorManager sensorManager = (SensorManager)
                getSystemService(SENSOR_SERVICE);
        // obtener la lista de todos los sensores   (TYPE_ALL)
        List<Sensor> listaSensores = sensorManager.getSensorList(Sensor.TYPE_ALL);
        // recorrer todos los sensores
        for(Sensor sensor: listaSensores)
            // añadir el sensor al label o etiqueta
            etiqueta.append("
-" + sensor.getName() + ", fabricante: " +sensor.getVendor());
    }
}
```

### 3.2.- Acelerómetro. Ejemplo.

Se denomina **acelerómetro** a cualquier instrumento destinado a medir aceleraciones, es decir mide las fuerzas de aceleración a las que se ve sometida una masa. Esta fuerza se alterada por los cambios de velocidad de la masa.

El acelerómetro es un sensor presente en la mayoría de los móviles actuales. También es posible determinar la posición del teléfono teniendo en cuenta como eje de coordenadas el punto medio del móvil.

**Usos del acelerómetro**:

- Detectar y medir alteraciones de velocidad de un objeto. Por ejemplo cuando nos movemos con el móvil.
- Medir la inclinación del dispositivo móvil cuando está en reposo, respecto al centro de la masa de la tierra.

**Funcionamiento**:

- Ojo, el acelerómetro no mide cambios de velocidad, sino fuerzas de aceleración.
- Por ejemplo, un objeto en reposo en la superficie de la tierra se ve sometido a una fuerza (g), pero en caída libre esta fuerza sería cero.
- Se construye en base a tres ejes, para poder medir en los ejes X, Y, Z.

**Inconveniente**: si se gira el dispositivo móvil a velocidad constante sobre el eje Z, no se detectará cambios en el acelerómetro.

### 3.3.- Sensor de movimiento.

La plataforma Android ofrece varios sensores que permiten controlar el movimiento de un dispositivo.

- Dos de estos sensores están basados en hardware (el acelerómetro y el giroscopio), y
- Tres de estos sensores pueden ser basados en hardware o en software (basado en la gravedad, la aceleración lineal, y los sensores de rotación del vector).

Por ejemplo, en algunos dispositivos los sensores basados en software obtienen sus datos del acelerómetro y magnetómetro, pero en otros dispositivos también pueden usar el giroscopio para derivar sus datos. La mayoría de los dispositivos con Android tienen un acelerómetro, y muchos ahora incluyen un giroscopio. La disponibilidad de los sensores basados en software es más variable ya que a menudo se basan en uno o más sensores de hardware para derivar sus datos.

Los **sensores de movimiento** son útiles para captar ciertos movimientos del dispositivo, tales como la inclinación, el temblor, la rotación, u oscilación (swing).

Los sensores de movimiento, por sí mismos, no se utilizan normalmente para controlar la posición del dispositivo, pero se pueden utilizar con otros sensores, como el sensor de campo magnético, para determinar la posición de un dispositivo.

Todos los sensores de movimiento devuelven matrices multidimensionales de valores para cada SensorEvent. Por ejemplo, durante un evento único, el sensor del acelerómetro devuelve datos de la fuerza de aceleración para los tres ejes de coordenadas, y el giróscopo de velocidad devuelve datos de rotación para los tres ejes de coordenadas. Estos valores se devuelven en un float array.


### 3.4.- Otros sensores. Ejemplos.

En este apartado vas a ver otros ejemplos de sensores. 

**Campo Magnético.**

Permite medir la dirección y fuerza de un campo magnético. Se puede usar como brújula, detector de metales, etc...

- Se construye en los 3 ejes X, Y, Z.
- El sensor se realiza con materiales magnetoresistivos, y su resistencia eléctrica cambia según el ángulo de incidencia de un campo magnético.

Su principal inconveniente es que si el dispositivo gira tomando como eje una línea de campo magnético, el sensor no detectará ningún cambio. El sensor de orientación puede solucionar este problema.


**Giroscopio.**

Es parecido al acelerómetro, aunque más preciso y menos lineal, pues también mide la dirección y el movimiento angular, siendo capaz de calcular la rotación total. Es capaz de detectar las vibraciones de nuestra voz.
El giroscopio mide la velocidad de rotación en radianes alrededor de X, Y, y eje Z de un dispositivo.

El siguiente código muestra cómo obtener una instancia del giroscopio defecto:
```
private SensorManager mSensorManager;
private Sensor mSensor;
...
mSensorManager = (SensorManager) getSystemService(Context.SENSOR_SERVICE);
mSensor = mSensorManager.getDefaultSensor(Sensor.TYPE_GYROSCOPE);
```
 

**Sensor de proximidad.**

El sensor de proximidad  permite determinar cuán lejos está un objeto desde un dispositivo. El siguiente código muestra cómo obtener una instancia del sensor de proximidad por defecto:
```
private SensorManager mSensorManager;
private Sensor mSensor;
...
mSensorManager = (SensorManager) getSystemService(Context.SENSOR_SERVICE);
mSensor = mSensorManager.getDefaultSensor(Sensor.TYPE_PROXIMITY);
```
 

El sensor de proximidad se utiliza generalmente para determinar a qué distancia está la cabeza de una persona de la pantalla de un dispositivo de teléfono (por ejemplo, cuando un usuario está haciendo o recibiendo una llamada telefónica).

La mayoría de los sensores de proximidad devuelven la distancia absoluta, en cm.

Debes **tener en cuenta** que:

- Algunos sensores de proximidad devuelven valores binarios que representan "cerca" o "lejos". En este caso, el sensor normalmente informa de su valor máximo en el estado "lejos" y un valor menor en el estado "cerca". Típicamente, el valor de la medida es un valor> 5 cm, pero esto puede variar de sensor a sensor.
- Puedes determinar el alcance máximo de un sensor utilizando el método getMaximumRange().

**Sensor de orientación.**

El sensor de orientación permite controlar la posición de un dispositivo en relación con el marco de la tierra de referencia (en concreto, el norte magnético). El siguiente código muestra cómo obtener una instancia del sensor de orientación por defecto:
```
private SensorManager mSensorManager;
private Sensor mSensor;
...
mSensorManager = (SensorManager) getSystemService(Context.SENSOR_SERVICE);
mSensor = mSensorManager.getDefaultSensor(Sensor.TYPE_ORIENTATION);
```
 

**Sensor de luz, presión y temperatura.**

Los sensores de luz, presión y temperatura obtienen los datos en bruto y por lo general no requiere calibración, filtrado, o modificación, lo que hace que sean algunos de los sensores más fáciles de usar.

Para adquirir los datos de estos sensores lo primero es crear una instancia de la clase SensorManager, que se puede utilizar para obtener una instancia de un sensor físico. Luego hay que registrar un sensor en el método onResume(), y empezar a manipular los datos del sensor de entrada en el método onSensorChanged().

 
