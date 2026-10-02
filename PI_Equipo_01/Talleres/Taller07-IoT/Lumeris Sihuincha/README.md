# TALLER 07 — Internet de las Cosas (IoT)

| | |
|---|---|
| **Facultad** | Ciencias e Ingeniería |
| **Curso** | Proyecto Integrador |
| **Docentes** | Ing. Umbert Lewis · Ing. Vanessa Stefanny · Ing. Renzo Chan · Ing. Maria Rejas |
| **Integrante** | Shedira Lumeris Sihuincha Palacin |
| **Año** | 2026 |

---

# Contenido

1. [Introducción](#introducción)
2. [Ejercicio 01 — Lectura de un potenciómetro](#ejercicio-01--lectura-de-un-potenciómetro)
3. [Ejercicio 02 — Conexión WiFi y página web desde el ESP32](#ejercicio-02--conexión-wifi-y-página-web-desde-el-esp32)
4. [Ejercicio 03 — Envío de datos a internet con ThingSpeak](#ejercicio-03--envío-de-datos-a-internet-con-thingspeak)
5. [Ejercicio 04 — Sensor de gas MQ-2 enviando datos a ThingSpeak](#ejercicio-04--sensor-de-gas-mq-2-enviando-datos-a-thingspeak)
6. [Ejercicio 05 — Control de un LED desde internet con Firebase](#ejercicio-05--control-de-un-led-desde-internet-con-firebase)
7. [Conclusiones generales](#conclusiones-generales)

---

# Introducción

Este taller tiene como finalidad practicar cómo funciona el Internet de las Cosas (IoT), es decir, cómo objetos cotidianos y pequeños aparatos electrónicos pueden conectarse a internet para enviar y recibir información.

Para ello se trabajó con una placa llamada **ESP32**, que funciona como un pequeño cerebro con WiFi. Con ella se midieron valores de sensores, se mostraron en una página web, se enviaron a plataformas en internet y, por último, se controló un LED a distancia.

Los cinco ejercicios siguen un camino que se va complicando poco a poco:

| Paso | Qué ocurre | Dónde se ve en el taller |
|---|---|---|
| 1 | Un sensor mide algo del entorno | Ejercicios 1, 3 y 4 |
| 2 | La placa ordena y mejora esa información | Ejercicios 1 y 3 |
| 3 | La placa se conecta a internet por WiFi | Ejercicios 2 al 5 |
| 4 | Los datos se guardan y se muestran en la nube | Ejercicios 3 y 4 |
| 5 | Desde internet se da una orden que la placa cumple | Ejercicio 5 |

En conjunto, los ejercicios muestran cómo un aparato puede vigilarse y manejarse desde cualquier lugar con conexión a internet.

---

# Ejercicio 01 — Lectura de un potenciómetro

## ¿De qué trata?

Un potenciómetro es una perilla que se puede girar para cambiar cuánta electricidad deja pasar. En este ejercicio, Conecte uno a la placa ESP32 para que esta leyera su posición.

Una sola lectura puede variar un poco por pequeñas interferencias eléctricas. Por eso, el programa toma 10 lecturas seguidas y calcula su promedio, lo que da un resultado más estable. Luego convierte ese número en voltios, una unidad más fácil de entender.

## Objetivo

Leer un sensor con la ESP32, promediar varias lecturas para obtener un valor más estable y mostrar el resultado en voltios en el Monitor Serial (la pantalla de texto del programa Arduino IDE).

## Código utilizado

```cpp
int potPin = 34;

void setup() {
  Serial.begin(115200);
}

void loop() {

  long suma = 0;

  // Tomar 10 lecturas
  for (int i = 0; i < 10; i++) {

    int valor = analogRead(potPin);

    suma += valor;

    delay(50);
  }

  // Calcular promedio de las 10 lecturas
  float promedioADC = suma / 10.0;

  // Convertir el promedio a voltaje
  float voltaje = (promedioADC * 3.3) / 4095.0;

  Serial.print("Promedio ADC: ");
  Serial.print(promedioADC);

  Serial.print(" | Voltaje promedio: ");
  Serial.print(voltaje, 3);

  Serial.println(" V");

  delay(500);
}
```

## Cómo funciona el código

| Parte del código | Qué hace, en palabras simples |
|---|---|
| `int potPin = 34;` | Indica en qué terminal de la placa está conectado el potenciómetro (el terminal 34). |
| `Serial.begin(115200);` | Abre la comunicación entre la placa y la computadora para poder ver los resultados en pantalla. |
| `long suma = 0;` | Crea un contador donde se irán sumando las lecturas. |
| `for (int i = 0; i < 10; i++)` | Repite la lectura 10 veces seguidas. |
| `analogRead(potPin);` | Lee el potenciómetro. La placa entrega un número entre 0 (mínimo) y 4095 (máximo). |
| `float promedioADC = suma / 10.0;` | Suma las 10 lecturas y las divide entre 10 para obtener el promedio. |
| `(promedioADC * 3.3) / 4095.0` | Convierte ese número en voltios. La placa trabaja con un máximo de 3.3 V, y ese valor se reparte entre los 4095 niveles posibles. |
| `Serial.print(...)` | Muestra en pantalla el promedio y el voltaje. |

## Por qué es importante

- **Medir el entorno:** leer un sensor es el primer paso de cualquier sistema IoT, porque convierte algo físico en un número que se puede usar.
- **Promediar:** al usar varias lecturas, se reducen los saltos causados por interferencias y el dato resulta más confiable.
- **Convertir a voltios:** un número como 2697 no dice mucho, mientras que 2.174 V se interpreta con facilidad.
- **Ver los datos en pantalla:** permite comprobar en el momento que todo funciona bien.

## Evidencia de ejecución

Al ejecutar el programa, el Monitor Serial muestra el promedio de las lecturas y su equivalente en voltios.

Ejemplo de salida:

```yaml
Promedio ADC: 2697.40 | Voltaje promedio: 2.174 V

Promedio ADC: 2678.80 | Voltaje promedio: 2.159 V
```

**Evidencia:**

<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/6792c3c8-4e54-48fb-a1b5-0c6a1ffdb9df" />
<img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/13e60d1f-ea30-47bf-b2e4-cfa43e09b0c4" />

## Resultado

| Aspecto | Resultado |
|---|---|
| Lectura del potenciómetro | Correcta |
| Promedio de 10 lecturas | Valores más estables |
| Conversión a voltios | Correcta |

## Conclusión del ejercicio

Logre armar un sistema sencillo para medir un sensor con la ESP32. El ejercicio permitió entender la primera etapa de un sistema IoT: captar información del entorno y ordenarla bien antes de usarla. Si los datos que se miden no son confiables, todo lo que venga después tampoco lo será.

---

# Ejercicio 02 — Conexión WiFi y página web desde el ESP32

## ¿De qué trata?

En este ejercicio, Conecte la ESP32 a una red WiFi creada desde un celular (usando la opción de compartir internet, llamada también "hotspot"). Una vez conectada, la red le asigna una dirección IP, que es como el número de casa del aparato dentro de esa red.

Con esa conexión, la placa funciona como un pequeño servidor web: al escribir su dirección IP en un navegador, se abre una página que muestra un mensaje de bienvenida, el estado del servidor y la propia dirección IP.

## Objetivo

Conectar la ESP32 a una red WiFi y crear una página web sencilla, que se pueda ver desde cualquier navegador conectado a la misma red.

## Código utilizado

> Nota: en este informe, el nombre y la clave de la red WiFi se reemplazaron por texto de ejemplo, para no dejar datos personales a la vista.

```cpp
#include <WiFi.h>
#include <WebServer.h>

const char* ssid = "NOMBRE_DE_LA_RED";
const char* password = "CLAVE_DE_LA_RED";

WebServer server(80);

void handleRoot() {

  String html = R"rawliteral(

  <!DOCTYPE html>
  <html>

  <body>

  <h1>Hola Lumeris, bienvenida</h1>

  <p>Servidor funcionando</p>

  </body>

  </html>

  )rawliteral";

  html += WiFi.localIP().toString();

  server.send(200, "text/html", html);

}

void setup() {

  Serial.begin(115200);

  WiFi.begin(ssid, password);

  while (WiFi.status() != WL_CONNECTED) {

    delay(500);
    Serial.print(".");

  }

  Serial.println("WiFi conectado");

  Serial.print("Direccion IP: ");
  Serial.println(WiFi.localIP());

  server.on("/", handleRoot);

  server.begin();

}

void loop() {

  server.handleClient();

}
```

## Cómo funciona el código

| Parte del código | Qué hace, en palabras simples |
|---|---|
| `#include <WiFi.h>` | Agrega las herramientas para conectarse a una red WiFi. |
| `#include <WebServer.h>` | Agrega las herramientas para crear una página web desde la placa. |
| `ssid` y `password` | Guardan el nombre y la clave de la red a la que se conectará la placa. |
| `WebServer server(80);` | Crea el servidor web en el puerto 80, que es el que usan normalmente las páginas de internet. |
| `handleRoot()` | Arma la página que verá la persona que entre: un saludo, el estado del servidor y la dirección IP. |
| `WiFi.localIP()` | Obtiene la dirección IP que la red le dio a la placa, para mostrarla en la página. |
| `WiFi.begin(ssid, password);` | Le ordena a la placa conectarse a la red. |
| `while (WiFi.status() != WL_CONNECTED)` | Hace que la placa espere, mostrando puntos en pantalla, hasta que la conexión se logre. |
| `server.on("/", handleRoot);` | Indica que, al entrar a la página principal, se muestre el contenido de `handleRoot()`. |
| `server.begin();` | Enciende el servidor. |
| `server.handleClient();` | Dentro del `loop()`, revisa todo el tiempo si alguien pidió la página y, de ser así, se la entrega. |

## Por qué es importante

- **Sin cables:** el WiFi permite que el aparato envíe información sin estar conectado físicamente a nada.
- **Un servidor propio:** la placa entrega la página por sí sola, sin necesitar una computadora que la ayude.
- **La dirección IP:** es la forma de encontrar al aparato dentro de la red y abrir su página desde un navegador.

## Evidencia de ejecución

Durante la prueba se comprobó lo siguiente:

- La ESP32 se conectó correctamente al hotspot del celular.
- La red le asignó una dirección IP.
- El navegador pudo abrir la página creada por la placa.

Resultado mostrado:

```yaml
✓ Servidor funcionando

La conexión WiFi se estableció correctamente.

Dirección IP del ESP32:

10.175.204.80
```

**Evidencia:**

<img width="900" height="500" alt="WhatsApp Image 2026-09-29 at 3 34 42 PM" src="https://github.com/user-attachments/assets/6946f3ab-33ad-433b-9276-f5bb536e3bbc" />
<img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/0d46cab6-be7b-42e5-bd20-b71b6776f278" />

## Resultado

| Aspecto | Resultado |
|---|---|
| Conexión al WiFi | Correcta |
| Dirección IP asignada | 10.175.204.80 |
| Página web desde el navegador | Se abrió sin problemas |

## Conclusión del ejercicio

Logre que la ESP32 se conectara a una red inalámbrica y mostrara una página web propia. Este ejercicio ayudó a entender que un aparato IoT puede dar información a distancia con solo estar conectado a la red, y que este mismo principio puede servir luego para vigilarlo o manejarlo desde otros dispositivos.

---

# Ejercicio 03 — Envío de datos a internet con ThingSpeak

## ¿De qué trata?

Hasta ahora, los datos solo se veían en la computadora. En este ejercicio, Di un paso más: la ESP32 lee el potenciómetro, calcula el voltaje (igual que en el ejercicio 1) y lo envía a **ThingSpeak**, una página en internet que guarda los datos y los muestra en gráficos.

De esta manera, el voltaje del potenciómetro puede verse desde cualquier lugar, casi en tiempo real.

## Objetivo

Conectar la ESP32 con ThingSpeak para guardar y ver en internet los datos de un sensor.

## Código utilizado

> Nota: la clave de la red WiFi y la clave de escritura de ThingSpeak se reemplazaron por texto de ejemplo, ya que son datos privados que no deben quedar a la vista.

```cpp
#include <WiFi.h>
#include <ThingSpeak.h>

const char* ssid = "NOMBRE_DE_LA_RED";
const char* password = "CLAVE_DE_LA_RED";

// ThingSpeak
unsigned long channelID = 3515248;
const char* writeAPIKey = "CLAVE_DE_ESCRITURA_THINGSPEAK";

WiFiClient client;

int potPin = 34;

void setup() {

  Serial.begin(115200);

  WiFi.begin(ssid, password);

  Serial.print("Conectando a WiFi");

  while (WiFi.status() != WL_CONNECTED) {

    delay(500);
    Serial.print(".");

  }

  Serial.println();

  Serial.println("WiFi conectado");

  Serial.print("IP del ESP32: ");

  Serial.println(WiFi.localIP());

  ThingSpeak.begin(client);

}

void loop() {

  long suma = 0;

  // Tomar 10 lecturas
  for (int i = 0; i < 10; i++) {

    int valor = analogRead(potPin);

    suma += valor;

    delay(50);

  }

  // Promedio de ADC
  float promedioADC = suma / 10.0;

  // Conversión a voltaje
  float voltaje = (promedioADC * 3.3) / 4095.0;

  Serial.print("ADC promedio: ");

  Serial.print(promedioADC);

  Serial.print(" | Voltaje: ");

  Serial.print(voltaje, 3);

  Serial.println(" V");

  // Enviar a ThingSpeak
  ThingSpeak.setField(1, voltaje);

  int respuesta = ThingSpeak.writeFields(channelID, writeAPIKey);

  if (respuesta == 200) {

    Serial.println("Dato enviado correctamente a ThingSpeak");

  } else {

    Serial.print("Error al enviar. Codigo HTTP: ");

    Serial.println(respuesta);

  }

  delay(15000);

}
```

## Cómo funciona el código

| Parte del código | Qué hace, en palabras simples |
|---|---|
| `#include <WiFi.h>` | Permite que la placa se conecte a internet por WiFi. |
| `#include <ThingSpeak.h>` | Permite que la placa se comunique con la página ThingSpeak. |
| `ssid` y `password` | Nombre y clave de la red WiFi. |
| `channelID` | Es el número del "canal", que funciona como una carpeta en ThingSpeak donde se guardan los datos. |
| `writeAPIKey` | Es una clave que autoriza a la placa a guardar datos en ese canal. Sin ella, cualquiera podría escribir en él. |
| `for (int i = 0; i < 10; i++)` | Toma 10 lecturas del potenciómetro. |
| `promedioADC = suma / 10.0` | Calcula el promedio de esas lecturas para que el dato sea más estable. |
| `voltaje = (promedioADC * 3.3) / 4095.0` | Convierte el promedio en voltios. |
| `ThingSpeak.setField(1, voltaje);` | Coloca el voltaje en el "campo 1" del canal, que es el espacio donde se guardará. |
| `ThingSpeak.writeFields(...)` | Envía el dato a internet. |
| `if (respuesta == 200)` | Si ThingSpeak responde con el código 200, significa que el dato llegó bien. Si no, se muestra un mensaje de error. |
| `delay(15000);` | Espera 15 segundos antes de repetir, porque ThingSpeak, en su versión gratuita, no admite envíos más seguidos. |

## Por qué es importante

- **Datos en la nube:** los datos dejan de estar solo en la computadora y pueden revisarse desde cualquier lugar con internet.
- **Datos ordenados antes de enviar:** el promedio evita mandar valores con saltos causados por interferencias.
- **Gráficos automáticos:** ThingSpeak dibuja la gráfica sin que la estudiante tenga que hacer nada más.
- **Un sistema IoT completo:** este ejercicio reúne todas las etapas:

| Etapa | Qué pasa |
|---|---|
| 1 | El sensor mide. |
| 2 | La ESP32 ordena el dato. |
| 3 | La placa se conecta al WiFi. |
| 4 | El dato viaja a internet. |
| 5 | ThingSpeak lo muestra en un gráfico. |

## Evidencia de ejecución

Durante la prueba se comprobó lo siguiente:

- La ESP32 se conectó a la red WiFi.
- Se leyó el potenciómetro y se calculó el voltaje.
- El dato se envió correctamente a ThingSpeak.

Ejemplo del Monitor Serial:

```yaml
ADC promedio: 4095.00 | Voltaje: 3.300 V

Dato enviado correctamente a ThingSpeak
```

**Evidencia:**

<img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/38a84896-d985-4dcd-ac88-a84106aa5de5" />
<img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/654e60f2-cafd-4858-9d34-4f50603fde5b" />

En ThingSpeak se ve la gráfica con los cambios de voltaje enviados desde la ESP32.

## Resultado

| Aspecto | Resultado |
|---|---|
| Conexión a internet | Correcta |
| Envío de datos a ThingSpeak | Correcto (código 200) |
| Gráfica en ThingSpeak | Se visualizó la variación del voltaje |

## Conclusión del ejercicio

Logre que la ESP32 midiera un dato, lo enviara a internet y se pudiera ver en una gráfica. Con este ejercicio se entendió cómo un aparato físico puede mandar información a un servicio en la nube para guardarla y revisarla después, que es una de las ideas principales del Internet de las Cosas.

---

# Ejercicio 04 — Sensor de gas MQ-2 enviando datos a ThingSpeak

## ¿De qué trata?

El MQ-2 es un sensor que reacciona a la presencia de gases en el aire, como el humo o el gas de cocina. Conecte a la ESP32 y envió sus lecturas a ThingSpeak para poder ver cómo cambian con el tiempo.

A diferencia del ejercicio anterior, aquí el dato se envía usando una dirección web (una URL) que la placa visita cada cierto tiempo, de forma parecida a cuando una persona escribe una dirección en el navegador.

## Objetivo

Leer un sensor de gas con la ESP32 y enviar sus datos a ThingSpeak por WiFi, para guardarlos y verlos en una gráfica.

## Código utilizado

> Nota: la clave de la red WiFi y la clave de ThingSpeak se reemplazaron por texto de ejemplo, ya que son datos privados.

```cpp
#include <WiFi.h>
#include <HTTPClient.h>

const char* ssid = "NOMBRE_DE_LA_RED";
const char* password = "CLAVE_DE_LA_RED";

String apiKey = "CLAVE_DE_ESCRITURA_THINGSPEAK";

const int MQ2_PIN = 34;

void setup() {

  Serial.begin(115200);

  pinMode(MQ2_PIN, INPUT);

  WiFi.begin(ssid, password);

  while (WiFi.status() != WL_CONNECTED) {

    delay(500);

    Serial.print(".");

  }

  Serial.println("\nWiFi conectado");

}

void loop() {

  int valorMQ2 = analogRead(MQ2_PIN);

  Serial.print("Valor MQ-2: ");

  Serial.println(valorMQ2);

  if (WiFi.status() == WL_CONNECTED) {

    HTTPClient http;

    String url = "https://api.thingspeak.com/update?api_key="
                 + apiKey + "&field1=" + String(valorMQ2);

    http.begin(url);

    int respuesta = http.GET();

    Serial.print("Respuesta ThingSpeak: ");

    Serial.println(respuesta);

    http.end();

  }

  delay(15000);

}
```

## Cómo funciona el código

| Parte del código | Qué hace, en palabras simples |
|---|---|
| `#include <WiFi.h>` | Permite conectar la placa a internet. |
| `#include <HTTPClient.h>` | Permite que la placa "visite" direcciones web para enviar información. |
| `apiKey` | Es la clave que autoriza a la placa a guardar datos en el canal de ThingSpeak. |
| `MQ2_PIN = 34` | Indica el terminal de la placa donde está conectado el sensor. |
| `analogRead(MQ2_PIN);` | Lee el sensor. Entrega un número entre 0 y 4095: mientras más alto, más fuerte es la señal del sensor. |
| `if (WiFi.status() == WL_CONNECTED)` | Antes de enviar, revisa que haya conexión a internet. |
| `String url = ...` | Arma la dirección web que lleva la clave y el valor medido. |
| `http.GET();` | Visita esa dirección, y con eso el dato queda guardado en ThingSpeak. |
| `http.end();` | Cierra la conexión una vez terminado el envío, para no gastar recursos de la placa. |
| `delay(15000);` | Espera 15 segundos antes de repetir el proceso. |

## Por qué es importante

- **Vigilar el ambiente:** un sensor de gas permite saber cómo está el aire de un lugar, aunque la persona no esté ahí.
- **Revisión a distancia:** el dato llega a internet y puede verse desde cualquier sitio.
- **Otra forma de enviar datos:** en el ejercicio 3 se usó una herramienta lista para ThingSpeak; aquí se envía con una dirección web común, que es un método válido para muchos otros servicios.
- **Revisar la conexión antes de enviar:** así la placa no intenta mandar datos cuando no tiene internet.

## Evidencia de ejecución

Durante la prueba se comprobó lo siguiente:

- La ESP32 se conectó a la red WiFi.
- El sensor MQ-2 entregó valores.
- Los valores se enviaron a ThingSpeak y la plataforma los recibió.

En el Monitor Serial se observa:

```yaml
WiFi conectado

Valor MQ-2: 2329

Respuesta ThingSpeak: 200


Valor MQ-2: 2308

Respuesta ThingSpeak: 200
```

El código `200` indica que el servidor recibió los datos sin problemas.

**Evidencia:**

<img width="900" height="500" alt="WhatsApp Image 2026-09-29 at 4 57 48 PM" src="https://github.com/user-attachments/assets/c105407e-59af-416b-8bf5-5a96677eba02" />
<img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/0f562560-814e-4d1a-bec3-ccbdd343b0a4" />
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/9d1bfe6b-ed59-4316-8e83-307d9d1f0276" />
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/0f8a21d6-8791-4be9-b5c0-19712599f84b" />

En ThingSpeak se ve la gráfica con los valores recibidos del sensor MQ-2.

## Resultado

| Aspecto | Resultado |
|---|---|
| Lectura del sensor MQ-2 | Correcta |
| Envío a ThingSpeak | Correcto (código 200) |
| Gráfica en ThingSpeak | Se visualizaron los valores recibidos |

## Conclusión del ejercicio

Logre conectar un sensor de gas a la ESP32 y ver sus lecturas en internet. El ejercicio permitió repasar todo el recorrido de un dato: se mide, viaja por WiFi y se guarda en la nube. Este tipo de sistema sirve de base para vigilar a distancia variables del ambiente, como la calidad del aire.

---

# Ejercicio 05 — Control de un LED desde internet con Firebase

## ¿De qué trata?

En este último ejercicio, la comunicación va en las dos direcciones. Use **Firebase Realtime Database**, una base de datos en internet donde se guarda un valor que puede cambiarse en cualquier momento.

La ESP32 se conecta al WiFi, inicia sesión en Firebase con un usuario registrado y revisa cada segundo el valor guardado en la base de datos:

| Valor guardado | Qué hace la ESP32 |
|---|---|
| `true` (verdadero) | Enciende el LED. |
| `false` (falso) | Apaga el LED. |

Después de cumplir la orden, la placa escribe de vuelta en Firebase el estado que aplicó, para confirmar que lo recibió y lo ejecutó.

## Objetivo

Lograr que la ESP32 y Firebase se comuniquen en ambos sentidos, de modo que un LED pueda encenderse y apagarse a distancia con un valor guardado en internet.

## Código utilizado

> Nota: la red WiFi, la clave del proyecto de Firebase y el usuario con su contraseña se reemplazaron por texto de ejemplo, ya que son datos privados que no deben quedar a la vista.

```cpp
#define ENABLE_USER_AUTH
#define ENABLE_DATABASE

#include <WiFi.h>
#include <WiFiClientSecure.h>
#include <FirebaseClient.h>

#define WIFI_SSID "NOMBRE_DE_LA_RED"
#define WIFI_PASSWORD "CLAVE_DE_LA_RED"

#define API_KEY "CLAVE_API_DE_FIREBASE"

#define DATABASE_URL "https://talleriot-c670f-default-rtdb.firebaseio.com/"

#define USER_EMAIL "CORREO_DEL_USUARIO"
#define USER_PASSWORD "CONTRASENA_DEL_USUARIO"

#define LED_PIN 2

UserAuth user_auth(
  API_KEY,
  USER_EMAIL,
  USER_PASSWORD
);

FirebaseApp app;

WiFiClientSecure ssl_client;

using AsyncClient = AsyncClientClass;

AsyncClient async_client(ssl_client);

RealtimeDatabase Database;

unsigned long ultimoTiempo = 0;

const unsigned long intervalo = 1000;

void processData(AsyncResult &aResult)
{
  if (!aResult.isResult())
    return;

  if (aResult.isError())
  {
    Serial.print("Firebase error: ");
    Serial.println(aResult.error().message());
  }
}

void setup()
{

  Serial.begin(115200);

  pinMode(
    LED_PIN,
    OUTPUT
  );

  digitalWrite(
    LED_PIN,
    LOW
  );

  WiFi.begin(
    WIFI_SSID,
    WIFI_PASSWORD
  );

  while (
    WiFi.status() != WL_CONNECTED
  )
  {
    delay(500);
    Serial.print(".");
  }

  ssl_client.setInsecure();

  initializeApp(
    async_client,
    app,
    getAuth(user_auth),
    processData,
    "authTask"
  );

  app.getApp<RealtimeDatabase>(
    Database
  );

  Database.url(
    DATABASE_URL
  );

}

void loop()
{

  app.loop();

  if (
    millis() - ultimoTiempo >= intervalo
  )
  {

    ultimoTiempo = millis();

    if (
      app.ready()
    )
    {

      bool estado =
        Database.get<bool>(
          async_client,
          "/estado"
        );

      Serial.print(
        "Estado recibido: "
      );

      Serial.println(
        estado ? "true" : "false"
      );

      if (estado)
      {

        digitalWrite(
          LED_PIN,
          HIGH
        );

        Serial.println(
          "LED ENCENDIDO"
        );

      }

      else
      {

        digitalWrite(
          LED_PIN,
          LOW
        );

        Serial.println(
          "LED APAGADO"
        );

      }

      Database.set<bool>(
        async_client,
        "/estado_esp32",
        estado
      );

    }

  }

}
```

## Cómo funciona el código

| Parte del código | Qué hace, en palabras simples |
|---|---|
| `#include <FirebaseClient.h>` | Agrega las herramientas para comunicarse con Firebase. |
| `WiFiClientSecure` | Crea una conexión protegida (segura) con internet. |
| `API_KEY` y `DATABASE_URL` | Identifican el proyecto y la base de datos de Firebase a la que se conectará la placa. |
| `UserAuth user_auth(...)` | Guarda el correo y la contraseña con los que la placa inicia sesión. Así, solo un usuario autorizado puede entrar a la base de datos. |
| `LED_PIN 2` y `pinMode(...)` | Indican que el LED está en el terminal 2 y que la placa lo usará para dar órdenes (encender o apagar). |
| `WiFi.begin(...)` | Conecta la placa a la red WiFi. |
| `app.loop();` | Mantiene activa la sesión con Firebase mientras la placa funciona. |
| `intervalo = 1000` | Hace que la placa revise la base de datos cada segundo. |
| `Database.get<bool>(..., "/estado")` | Lee el valor `estado` guardado en Firebase (verdadero o falso). |
| `digitalWrite(LED_PIN, HIGH / LOW)` | Enciende el LED si el valor es verdadero y lo apaga si es falso. |
| `Database.set<bool>(..., "/estado_esp32", estado)` | Guarda en Firebase el estado que la placa aplicó, para confirmar que cumplió la orden. |

## Por qué es importante

- **Comunicación en las dos direcciones:** la placa no solo manda datos, también recibe órdenes y avisa que las cumplió.

```text
Firebase  →  ESP32  →  LED  →  Firebase
(orden)     (recibe)  (actúa)  (confirma)
```

- **Control a distancia:** un valor guardado en internet se convierte en una acción real, como encender un LED. Con el mismo principio podría manejarse una luz, un motor o una cerradura.
- **Datos en tiempo real:** como la placa revisa Firebase cada segundo, responde rápido a los cambios.
- **Acceso protegido:** la placa inicia sesión con un usuario, así que no cualquier persona puede cambiar la orden.

## Evidencia de ejecución

Durante la prueba se comprobó lo siguiente:

- La ESP32 se conectó correctamente al WiFi.
- La placa se comunicó con Firebase.
- Al cambiar el valor en la nube, el LED cambió de estado.
- La placa actualizó su propio estado en la base de datos.

La base de datos muestra los valores:

```yaml
estado: false

estado_esp32: false
```

Cuando el valor cambia a verdadero desde la interfaz:

```yaml
estado: true
```

la ESP32 recibe el cambio y enciende el LED.

**Evidencia:**

<img width="900" height="400" alt="WhatsApp Image 2026-10-01 at 7 16 15 PM" src="https://github.com/user-attachments/assets/7b00a184-e893-4b84-a0f5-b5bea02015b9" />
<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/a8fd2795-459e-4ad4-9da3-64ef5449a410" />

## Resultado

| Aspecto | Resultado |
|---|---|
| Conexión con Firebase | Correcta |
| Control del LED desde la nube | El LED se encendió y apagó según el valor guardado |
| Confirmación de estado (`estado_esp32`) | La placa devolvió el estado aplicado |

## Conclusión del ejercicio

Logre controlar un LED a distancia usando una base de datos en internet. El ejercicio mostró cómo un aparato físico puede recibir órdenes desde la nube y confirmar que las cumplió. Esta forma de trabajo se usa en la domótica (casas inteligentes), la automatización y muchas aplicaciones de la industria.

---

# Conclusiones generales

| Ejercicio | Qué se logró | Idea principal que dejó |
|---|---|---|
| 1. Potenciómetro | Leer un sensor y mostrar el voltaje promediado | Los datos deben medirse bien desde el comienzo. |
| 2. WiFi y página web | Conectar la placa a una red y crear una página propia | Un aparato IoT puede dar información sin cables. |
| 3. ThingSpeak | Enviar el voltaje a internet y verlo en gráficos | Los datos pueden guardarse y revisarse desde cualquier lugar. |
| 4. Sensor MQ-2 | Enviar lecturas de gas a la nube | Se puede vigilar el ambiente a distancia. |
| 5. Firebase y LED | Encender y apagar un LED desde internet | Un aparato puede recibir órdenes y confirmar que las cumplió. |

En conjunto, el taller permitió a la estudiante recorrer todo el camino de un sistema IoT: medir, conectar, enviar, guardar, mostrar y controlar a distancia. Estas prácticas son una base útil para proyectos que necesiten vigilar o manejar equipos de forma remota, como el monitoreo de cultivos, la seguridad en espacios de trabajo o la automatización de procesos.
