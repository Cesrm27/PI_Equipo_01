# TALLER 07 — IoT

> **Facultad:** Ciencias e Ingeniería  
> **Curso:** Proyecto Integrador  
> **Docentes:** Ing. Umbert Lewis · Ing. Vanessa Stefanny · Ing. Renzo Chan · Ing. Maria Rejas  
>
> **Integrante:** Shedira Lumeris Sihuincha Palacin  
> **Año:** 2026

---

# FACULTAD DE CIENCIAS E INGENIERÍA

## CURSO:

# PROYECTO INTEGRADOR

## TALLER 07 — Internet de las Cosas (IoT)

---

## DOCENTES:

- Ing. Umbert Lewis
- Ing. Vanessa Stefanny
- Ing. Renzo Chan
- Ing. Maria Rejas

---

## Integrante:

**Shedira Lumeris Sihuincha Palacin**

---

## Año:

**2026**

---

# Contenido

1. [Introducción](#introducción)
2. [Ejercicio 01 — Lectura de un Potenciómetro con ESP32](#ejercicio-01)
3. [Ejercicio 02 — Conexión WiFi y Servidor Web con ESP32](#ejercicio-02)
4. [Ejercicio 03 — Envío de datos a la nube mediante ThingSpeak](#ejercicio-03)
5. [Ejercicio 04 — Sensor MQ-2 enviando datos a ThingSpeak](#ejercicio-04)
6. [Ejercicio 05](#ejercicio-05)
7. [Conclusiones](#conclusiones)

---

# Introducción

El presente taller tiene como finalidad desarrollar aplicaciones basadas en el Internet de las Cosas (IoT) utilizando una placa ESP32 como dispositivo principal de adquisición y comunicación de datos.

Durante el desarrollo de las actividades se aplican conceptos fundamentales de IoT como la lectura de sensores analógicos, comunicación mediante redes inalámbricas WiFi, implementación de servidores web embebidos y transmisión de información hacia plataformas Cloud.

Los ejercicios permiten comprender el flujo completo de un sistema IoT:

- Captura de información mediante sensores.
- Procesamiento de datos en el dispositivo.
- Comunicación inalámbrica mediante Internet.
- Almacenamiento y visualización de información en la nube.

Estas prácticas permiten conocer cómo los dispositivos inteligentes pueden interactuar con servicios externos para realizar tareas de monitoreo remoto y gestión de información.

---

# Ejercicio 01 — Lectura de un Potenciómetro con ESP32

## Descripción del problema

En este ejercicio se desarrolla la lectura de un potenciómetro conectado a una placa ESP32.

La actividad consiste en mejorar una lectura analógica básica mediante la implementación de un promedio de datos y posteriormente convertir los valores obtenidos por el ADC (Convertidor Analógico Digital) en valores de voltaje.

El uso del promedio permite disminuir pequeñas variaciones producidas por ruido eléctrico, logrando obtener mediciones más estables y confiables.

---

## Objetivo

Realizar la lectura de un sensor analógico utilizando el ESP32, procesar los datos obtenidos mediante un promedio de mediciones y convertir los valores ADC en valores de voltaje para visualizar la información mediante el Monitor Serial.

---

# Código utilizado

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
# Interpretacion del codigo

El programa comienza declarando el pin donde se encuentra conectado el potenciómetro:

```cpp
int potPin = 34;
```

El GPIO 34 del ESP32 funciona como una entrada analógica, permitiendo leer las variaciones de voltaje producidas por el movimiento del potenciómetro.

---

En la función `setup()` se inicia la comunicación serial:

```cpp
Serial.begin(115200);
```

Esta instrucción permite establecer comunicación entre el ESP32 y el Monitor Serial del Arduino IDE para visualizar los valores obtenidos durante la ejecución.

---

Dentro de la función `loop()` se crea una variable acumuladora:

```cpp
long suma = 0;
```

Esta variable almacena la suma de todas las lecturas obtenidas del sensor.

---

El programa realiza 10 lecturas consecutivas mediante un ciclo:

```cpp
for (int i = 0; i < 10; i++)
```

En cada repetición se obtiene un valor analógico mediante:

```cpp
int valor = analogRead(potPin);
```

La función `analogRead()` permite capturar el valor entregado por el sensor.

El ESP32 utiliza un ADC de 12 bits, por lo que los valores obtenidos pueden encontrarse dentro del rango:

- **0:** valor mínimo.
- **4095:** valor máximo.

---

Luego de realizar las mediciones, el programa calcula el promedio:

```cpp
float promedioADC = suma / 10.0;
```

Este proceso permite disminuir variaciones en la lectura y obtener un valor más estable.

---

Finalmente, el valor promedio del ADC es convertido a voltaje:

```cpp
float voltaje = (promedioADC * 3.3) / 4095.0;
```

La fórmula utiliza el voltaje de referencia del ESP32 (**3.3 V**) y la resolución del ADC (**4095 niveles**) para obtener un valor aproximado en voltios.

---

# Aspectos importantes del código

## 1. Lectura analógica del ESP32

```cpp
analogRead(potPin);
```

Esta función permite capturar señales provenientes de sensores analógicos.

Es una parte fundamental en sistemas IoT porque permite transformar variables físicas del entorno en datos digitales que pueden ser procesados.

---

## 2. Promedio de múltiples lecturas

```cpp
for (int i = 0; i < 10; i++)
```

El programa realiza varias mediciones antes de obtener el resultado final.

Esto permite disminuir errores generados por ruido eléctrico y mejora la estabilidad de la información obtenida.

---

## 3. Conversión ADC a voltaje

```cpp
float voltaje = (promedioADC * 3.3) / 4095.0;
```

Permite convertir el valor digital generado por el ADC en una magnitud física interpretable.

Esta conversión facilita analizar el comportamiento del sensor en valores reales.

---

## 4. Comunicación serial

```cpp
Serial.print()
```

Permite observar los datos obtenidos en tiempo real y comprobar el correcto funcionamiento del sistema.

---

# Evidencia de ejecución

Durante la ejecución del programa se observa la lectura del potenciómetro mediante el Monitor Serial del Arduino IDE.

Los valores mostrados corresponden al promedio de las lecturas realizadas y su conversión equivalente a voltaje.

Ejemplo de salida:

```yaml
Promedio ADC: 2697.40 | Voltaje promedio: 2.174 V

Promedio ADC: 2678.80 | Voltaje promedio: 2.159 V
```
# Evidencia:

<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/6792c3c8-4e54-48fb-a1b5-0c6a1ffdb9df" />
<img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/13e60d1f-ea30-47bf-b2e4-cfa43e09b0c4" />

# Resultado obtenido

El ESP32 logró realizar correctamente la lectura del potenciómetro, procesar los valores obtenidos y convertirlos en una medida de voltaje.

El promedio aplicado permitió obtener datos más estables, reduciendo las variaciones y mejorando la confiabilidad de las mediciones.

---

# Conclusión del ejercicio

Se logró implementar un sistema básico de adquisición de datos utilizando ESP32 y un sensor analógico.

Este ejercicio permitió comprender la primera etapa de un sistema IoT: la captura y procesamiento de información proveniente del entorno.

La correcta lectura y tratamiento de los datos obtenidos es fundamental para desarrollar sistemas IoT confiables y capaces de transmitir información útil para posteriores análisis.

# Ejercicio 02 — Conexión WiFi y Servidor Web con ESP32

## Descripción del problema

En este ejercicio se implementa una conexión inalámbrica utilizando una placa ESP32 conectada a una red WiFi creada mediante un Smartphone como punto de acceso (Hotspot).

El objetivo es lograr que el ESP32 pueda conectarse a una red disponible, obtener una dirección IP asignada y utilizar dicha conexión para ejecutar un servidor web local.

El sistema genera una página web personalizada donde se muestra el estado de conexión y la dirección IP del dispositivo.

---

## Objetivo

Configurar la comunicación WiFi del ESP32 y desarrollar un servidor web básico que permita visualizar información del dispositivo mediante un navegador conectado a la misma red.

---

## Código utilizado

```cpp
#include <WiFi.h>
#include <WebServer.h>

const char* ssid = "GalaxyA04s";
const char* password = "12345678";

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
# Interpretación del código

El programa comienza incluyendo las librerías necesarias para habilitar la conexión inalámbrica y la creación de un servidor web:

```cpp
#include <WiFi.h>
#include <WebServer.h>
```

La librería `WiFi.h` permite conectar el ESP32 a una red inalámbrica, mientras que `WebServer.h` proporciona las funciones necesarias para crear un servidor HTTP.

---

# Configuración de la red WiFi

```cpp
const char* ssid = "GalaxyA04s";
const char* password = "12345678";
```

Estas variables almacenan el nombre de la red WiFi y la contraseña utilizada para establecer la conexión.

El ESP32 utiliza estos datos para autenticarse dentro de la red creada mediante el Smartphone.

---

# Creación del servidor web

```cpp
WebServer server(80);
```

Esta instrucción crea un servidor web utilizando el puerto 80, que es el puerto estándar empleado para la comunicación HTTP.

Gracias a esto, otros dispositivos conectados a la misma red pueden acceder al ESP32 mediante su dirección IP.

---

# Generación de la página web

La función:

```cpp
void handleRoot()
```

se encarga de crear el contenido HTML que será enviado al navegador.

La página contiene:

- Mensaje de bienvenida.
- Estado del servidor.
- Confirmación de conexión.
- Dirección IP del ESP32.

La dirección IP se obtiene mediante:

```cpp
WiFi.localIP()
```

permitiendo mostrar dinámicamente la ubicación del dispositivo dentro de la red.

---

# Conexión WiFi del ESP32

Dentro de la función `setup()` se inicia la comunicación serial:

```cpp
Serial.begin(115200);
```

Luego comienza la conexión inalámbrica:

```cpp
WiFi.begin(ssid, password);
```

El programa espera hasta que la conexión sea exitosa mediante:

```cpp
while (WiFi.status() != WL_CONNECTED)
```

Una vez conectado, muestra la dirección IP asignada al dispositivo.

---

# Configuración de rutas del servidor

```cpp
server.on("/", handleRoot);
```

Esta instrucción indica que cuando un usuario ingrese a la dirección principal del servidor se ejecutará la función `handleRoot()`.

Después se inicia el servidor:

```cpp
server.begin();
```

---

# Atención de solicitudes

En la función principal:

```cpp
void loop()
{
  server.handleClient();
}
```

El ESP32 revisa constantemente si existe una solicitud enviada desde un navegador y responde enviando la página web correspondiente.

---

# Aspectos importantes del código

## 1. Comunicación WiFi

```cpp
WiFi.begin(ssid, password);
```

Permite que el ESP32 pueda comunicarse con otros dispositivos mediante una red inalámbrica.

Esta capacidad es fundamental dentro de sistemas IoT, ya que permite transmitir información sin necesidad de conexiones físicas.

---

## 2. Servidor web embebido

```cpp
WebServer server(80);
```

Permite que el ESP32 funcione como un servidor independiente sin necesidad de una computadora externa.

El dispositivo puede generar y entregar páginas web directamente a otros equipos conectados a la misma red.

---

## 3. Dirección IP dinámica

```cpp
WiFi.localIP()
```

Permite identificar el dispositivo dentro de la red para acceder al servidor web mediante un navegador.

---

# Evidencia de ejecución

Durante la prueba se observa:

- El ESP32 logró conectarse correctamente al Hotspot.
- Se obtuvo una dirección IP asignada.
- El navegador permitió acceder al servidor web creado.

Resultado mostrado:

```yaml
✓ Servidor funcionando

La conexión WiFi se estableció correctamente.

Dirección IP del ESP32:

10.175.204.80
```

# Evidencia:
<img width="900" height="500" alt="WhatsApp Image 2026-09-29 at 3 34 42 PM" src="https://github.com/user-attachments/assets/6946f3ab-33ad-433b-9276-f5bb536e3bbc" />
<img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/0d46cab6-be7b-42e5-bd20-b71b6776f278" />


---

# Resultado obtenido

El ESP32 funcionó correctamente como un servidor web conectado mediante WiFi.

La interfaz creada permitió comprobar la comunicación entre el dispositivo IoT y un navegador web dentro de la misma red.

---

# Conclusión del ejercicio

Se logró implementar una conexión inalámbrica mediante ESP32 y desarrollar un servidor web local.

Este ejercicio permitió comprender cómo los dispositivos IoT pueden conectarse a redes y proporcionar información remotamente mediante interfaces web.

La implementación de servidores embebidos permite que los dispositivos IoT puedan ser monitoreados y controlados mediante diferentes plataformas de acceso remoto.
---

# Ejercicio 03 — Envío de datos a la nube mediante ThingSpeak

## Descripción del problema

En este ejercicio se implementa un sistema IoT donde el ESP32 captura datos provenientes de un potenciómetro y los envía hacia una plataforma Cloud para su almacenamiento y visualización.

El objetivo es mostrar en tiempo real la variación del voltaje generado por el potenciómetro conectado al ESP32 utilizando ThingSpeak como plataforma de monitoreo.

Para lograrlo, el dispositivo realiza la lectura analógica del sensor, procesa los valores obtenidos mediante un promedio de mediciones, convierte los datos ADC a voltaje y finalmente envía la información hacia un canal en la nube.

---

## Objetivo

Implementar una comunicación entre un dispositivo IoT (ESP32) y una plataforma Cloud IoT (ThingSpeak), permitiendo almacenar y visualizar datos obtenidos desde un sensor analógico.

---

## Código utilizado

```cpp
#include <WiFi.h>
#include <ThingSpeak.h>

const char* ssid = "UPCH_CENTRAL";
const char* password = "CAYETANO2022";

// ThingSpeak
unsigned long channelID = 3515248;
const char* writeAPIKey = "BNU5ZQ3GHU1X1O49";

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
# Interpretación del código

El programa inicia incluyendo las librerías necesarias para la conexión WiFi y comunicación con la plataforma ThingSpeak:

```cpp
#include <WiFi.h>
#include <ThingSpeak.h>
```

La librería `WiFi.h` permite que el ESP32 tenga acceso a Internet mediante una red inalámbrica.

La librería `ThingSpeak.h` permite enviar información hacia la plataforma Cloud para su almacenamiento y visualización.

---

# Configuración de la conexión WiFi

```cpp
const char* ssid = "UPCH_CENTRAL";
const char* password = "CAYETANO2022";
```

Estas variables almacenan las credenciales de la red WiFi utilizada por el ESP32.

La conexión a Internet es necesaria para poder transmitir los datos obtenidos hacia la nube.

---

# Configuración del canal ThingSpeak

```cpp
unsigned long channelID = 3515248;

const char* writeAPIKey = "BNU5ZQ3GHU1X1O49";
```

Estos valores identifican el canal donde se almacenarán los datos enviados desde el ESP32.

- `channelID`: identifica el canal de almacenamiento en ThingSpeak.
- `writeAPIKey`: permite autorizar el envío de información hacia dicho canal.

---

# Lectura del potenciómetro

El sensor se conecta al pin analógico:

```cpp
int potPin = 34;
```

El ESP32 utiliza su conversor analógico-digital (**ADC**) para transformar el voltaje recibido en un valor digital.

La lectura se realiza mediante:

```cpp
analogRead(potPin);
```

El ADC del ESP32 posee una resolución de 12 bits, por lo que los valores obtenidos se encuentran dentro del rango:

- **0:** valor mínimo.
- **4095:** valor máximo.

---

# Promedio de lecturas

El programa realiza 10 mediciones consecutivas:

```cpp
for (int i = 0; i < 10; i++)
```

Cada valor obtenido es acumulado mediante:

```cpp
suma += valor;
```

Luego se calcula el promedio:

```cpp
float promedioADC = suma / 10.0;
```

Este procedimiento permite reducir el ruido generado por pequeñas variaciones eléctricas y obtener datos más estables.

---

# Conversión de ADC a voltaje

El valor digital obtenido del ADC se convierte a voltios mediante:

```cpp
float voltaje = (promedioADC * 3.3) / 4095.0;
```

La fórmula utiliza:

- Voltaje de referencia del ESP32: **3.3 V**.
- Resolución del ADC: **4095 niveles**.

Esta conversión permite obtener una medida física interpretable que puede ser enviada hacia la plataforma Cloud.

---

# Envío de información a ThingSpeak

El valor calculado del voltaje se almacena en el campo 1:

```cpp
ThingSpeak.setField(1, voltaje);
```

Posteriormente se realiza el envío hacia el canal configurado:

```cpp
ThingSpeak.writeFields(channelID, writeAPIKey);
```

Si la respuesta obtenida es igual a `200`, significa que la información fue enviada correctamente a ThingSpeak.

---

# Aspectos importantes del código

## 1. Integración con una plataforma Cloud

El ESP32 deja de trabajar únicamente de forma local y comienza a enviar datos hacia Internet.

Esto permite realizar monitoreo remoto de variables físicas obtenidas mediante sensores.

---

## 2. Procesamiento de datos antes del envío

El promedio de lecturas:

```cpp
float promedioADC = suma / 10.0;
```

permite mejorar la estabilidad de los datos enviados.

Este método evita transmitir valores afectados por pequeñas fluctuaciones eléctricas.

---

## 3. Conversión de señales físicas

La conversión de ADC a voltaje permite interpretar correctamente la información obtenida del sensor.

Esto facilita el análisis de los datos almacenados en la plataforma Cloud.

---

## 4. Comunicación IoT completa

El proceso desarrollado incluye las siguientes etapas:

1. Captura del dato mediante un sensor analógico.
2. Procesamiento de información en el ESP32.
3. Conexión a una red WiFi.
4. Envío de datos hacia la nube.
5. Visualización mediante gráficos en ThingSpeak.

---

# Evidencia de ejecución

Durante la ejecución del programa se observa:

- El ESP32 establece conexión con la red WiFi.
- Se realiza la lectura del potenciómetro.
- Los datos obtenidos son convertidos a voltaje.
- La información es enviada correctamente a ThingSpeak.

Ejemplo del Monitor Serial:

```yaml
ADC promedio: 4095.00 | Voltaje: 3.300 V

Dato enviado correctamente a ThingSpeak
```

# Evidencia:
<img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/38a84896-d985-4dcd-ac88-a84106aa5de5" />
<img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/654e60f2-cafd-4858-9d34-4f50603fde5b" />


En ThingSpeak se observa la gráfica generada con las variaciones del voltaje enviado desde el ESP32.

---

# Resultado obtenido

El sistema logró enviar datos obtenidos desde un sensor analógico hacia una plataforma Cloud.

Los valores fueron almacenados correctamente y pudieron visualizarse mediante gráficos en ThingSpeak.

El ESP32 funcionó como un nodo IoT capaz de capturar información, procesarla y transmitirla hacia un servicio remoto.

---

# Conclusión del ejercicio

Se logró implementar un sistema IoT completo utilizando ESP32, WiFi y ThingSpeak.

El ejercicio permitió comprender cómo un dispositivo físico puede capturar información del entorno y enviarla hacia servicios Cloud para su almacenamiento y análisis remoto.

Esta comunicación entre dispositivos físicos y plataformas Cloud representa una característica fundamental de los sistemas IoT modernos.
---

# Ejercicio 04 — Envío de datos de un sensor MQ-2 a ThingSpeak con ESP32

## Descripción del problema

En este ejercicio se implementa un sistema IoT utilizando un sensor MQ-2 conectado a una placa ESP32 para capturar valores analógicos relacionados con la detección de gases y enviarlos hacia una plataforma Cloud.

El ESP32 realiza la lectura del sensor MQ-2 mediante una entrada analógica, procesa el valor obtenido y posteriormente transmite la información hacia ThingSpeak utilizando una solicitud HTTP.

Esto permite almacenar los datos en la nube y visualizar su comportamiento mediante gráficos, facilitando el monitoreo remoto del sensor.

---

## Objetivo

Implementar un sistema IoT capaz de adquirir datos de un sensor MQ-2 mediante ESP32 y enviarlos hacia ThingSpeak utilizando una conexión WiFi para su almacenamiento y visualización en la nube.

---

## Código utilizado

```cpp
#include <WiFi.h>
#include <HTTPClient.h>

const char* ssid = "UPCH_CENTRAL";
const char* password = "CAYETANO2022";

String apiKey = "1NNJ4UQJU2CYUT6M";

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
# Interpretación del código

El programa comienza incluyendo las librerías necesarias para establecer comunicación WiFi y realizar solicitudes HTTP hacia la plataforma ThingSpeak:

```cpp
#include <WiFi.h>
#include <HTTPClient.h>
```

La librería `WiFi.h` permite conectar el ESP32 a Internet mediante una red inalámbrica.

La librería `HTTPClient.h` permite enviar solicitudes HTTP hacia servidores externos.

---

# Configuración de la red WiFi

```cpp
const char* ssid = "UPCH_CENTRAL";
const char* password = "CAYETANO2022";
```

Estas variables contienen los datos necesarios para que el ESP32 pueda conectarse a la red WiFi.

La conexión a Internet es necesaria para enviar los valores obtenidos del sensor hacia la plataforma Cloud.

---

# Configuración de la API de ThingSpeak

```cpp
String apiKey = "1NNJ4UQJU2CYUT6M";
```

La API Key permite autenticar al dispositivo y autorizar el envío de información hacia un canal específico de ThingSpeak.

Esta clave funciona como un identificador de acceso para actualizar los datos almacenados en la plataforma.

---

# Configuración del sensor MQ-2

```cpp
const int MQ2_PIN = 34;
```

El sensor MQ-2 se conecta al pin analógico 34 del ESP32.

Este sensor entrega una señal analógica relacionada con la concentración de gases detectados en el ambiente.

El ADC interno del ESP32 convierte esta señal en valores digitales que pueden ser procesados por el programa.

---

# Lectura del sensor

Dentro de la función `loop()` se obtiene el valor entregado por el sensor:

```cpp
int valorMQ2 = analogRead(MQ2_PIN);
```

La función `analogRead()` realiza la conversión analógico-digital.

El valor obtenido representa la intensidad de la señal detectada por el sensor MQ-2.

El ESP32 utiliza un ADC de 12 bits, por lo que los valores obtenidos se encuentran dentro del rango:

- **0:** valor mínimo.
- **4095:** valor máximo.

---

# Envío de datos mediante HTTP

Cuando el ESP32 tiene conexión a Internet:

```cpp
if (WiFi.status() == WL_CONNECTED)
```

se crea un cliente HTTP:

```cpp
HTTPClient http;
```

Luego se genera la dirección URL para actualizar los datos en ThingSpeak:

```cpp
String url = "https://api.thingspeak.com/update?api_key="
             + apiKey + "&field1=" + String(valorMQ2);
```

La URL contiene:

- La API Key del canal.
- El campo donde será almacenado el dato.
- El valor obtenido del sensor MQ-2.

---

# Solicitud al servidor

El envío de información se realiza mediante:

```cpp
int respuesta = http.GET();
```

Esta instrucción ejecuta una petición HTTP hacia ThingSpeak.

La respuesta recibida indica si la comunicación con el servidor fue exitosa.

---

# Finalización de conexión HTTP

Después de enviar los datos:

```cpp
http.end();
```

se libera la conexión utilizada para realizar la solicitud HTTP.

Esto permite optimizar el uso de recursos del ESP32.

---

# Aspectos importantes del código

## 1. Captura de datos ambientales

```cpp
analogRead(MQ2_PIN);
```

Permite obtener información del entorno mediante un sensor físico conectado al ESP32.

Esta etapa corresponde a la adquisición de datos dentro de un sistema IoT.

---

## 2. Comunicación entre dispositivo y Cloud

El ESP32 utiliza Internet para transmitir los datos hacia ThingSpeak.

Este proceso permite realizar monitoreo remoto sin necesidad de una conexión física directa con el dispositivo.

---

## 3. Uso de solicitudes HTTP

```cpp
http.GET();
```

Permite enviar información hacia servidores externos utilizando el protocolo HTTP.

Este mecanismo facilita la comunicación entre dispositivos IoT y plataformas Cloud.

---

## 4. Verificación de conexión WiFi

```cpp
WiFi.status() == WL_CONNECTED
```

Antes de realizar el envío de datos, el programa verifica que exista una conexión activa.

Esto evita intentos de transmisión cuando el dispositivo no tiene acceso a Internet.

---

# Evidencia de ejecución

Durante la ejecución se observa:

- El ESP32 establece conexión con la red WiFi.
- El sensor MQ-2 genera valores analógicos.
- Los datos obtenidos son enviados hacia ThingSpeak.
- La plataforma recibe correctamente la información.

En el Monitor Serial se observa:

```yaml
WiFi conectado

Valor MQ-2: 2329

Respuesta ThingSpeak: 200


Valor MQ-2: 2308

Respuesta ThingSpeak: 200
```

El código de respuesta HTTP `200` confirma que los datos fueron enviados correctamente al servidor.

# Evidencia:
<img width="900" height="500" alt="WhatsApp Image 2026-09-29 at 4 57 48 PM" src="https://github.com/user-attachments/assets/c105407e-59af-416b-8bf5-5a96677eba02" />
<img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/0f562560-814e-4d1a-bec3-ccbdd343b0a4" />
<img width="700" height="500" alt="image" src="https://github.com/user-attachments/assets/9d1bfe6b-ed59-4316-8e83-307d9d1f0276" />

En ThingSpeak se visualiza la gráfica generada con los valores recibidos del sensor MQ-2.

---

# Resultado obtenido

El sistema logró integrar correctamente un sensor MQ-2 con el ESP32 y una plataforma Cloud.

Los valores obtenidos por el sensor fueron enviados mediante Internet y almacenados en ThingSpeak, permitiendo visualizar su comportamiento de forma remota.

El ESP32 funcionó como un nodo IoT capaz de capturar información ambiental y transmitirla hacia un servicio externo.

---

# Conclusión del ejercicio

Se logró desarrollar un sistema IoT utilizando un sensor ambiental, una placa ESP32 y una plataforma Cloud.

El ejercicio permitió comprender el proceso completo de adquisición de datos, comunicación inalámbrica y transmisión hacia servicios externos.

La integración de sensores con plataformas Cloud constituye una base fundamental para aplicaciones IoT orientadas al monitoreo remoto y análisis de variables ambientales.
