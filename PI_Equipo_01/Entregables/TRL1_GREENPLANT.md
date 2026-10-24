<div align="center">

# 🌱 GREENPLANT

### Principios científicos de los sensores · TRL 1

**Proyecto Integrador | Universidad Peruana Cayetano Heredia**

📅 **23 de octubre de 2026**

</div>

---

## 📋 Ficha del proyecto

| Campo | Información |
|:---|:---|
| **Curso** | Proyecto Integrador |
| **Institución** | Universidad Peruana Cayetano Heredia |
| **Tema** | TRL1GREENPLANT |
| **Fecha** | 23/10/2026 |

**Integrantes:**

- Cesar Rodrigo Milla Gómez
- Anderson Josue Delerna Infantes
- Kevin Esty Carvallo Neciosup
- Shedira Lumeris Sihuincha Palacin

**Ingenieros:** Umbert Lewis De La Cruz, Maria Rejas, Harry Rivera y Renzo Chan

---

## 🧭 Contenido

1. [Artículos científicos y principios tecnológicos](#1-artículos-científicos-sobre-los-principios-de-la-tecnología-propuesta)
2. [Estado del arte](#2-estado-del-arte)
3. [Bases de datos](#3-bases-de-datos)
4. [Libros](#4-libros)
5. [Tesis](#5-tesis)
6. [Referencias bibliográficas](#referencias-bibliográficas)

---

## Presentación del proyecto

La tecnología que proponemos estudiar en GREENPLANT es un sistema de monitoreo de amoníaco, dióxido de carbono y condiciones ambientales y del suelo durante ensayos con plantas de papa. En el TRL 1 buscamos comprender los principios que permiten a los sensores detectar estas variables. La fertilización con urea constituye el contexto de aplicación; el fundamento tecnológico se centra en cómo se producen y se interpretan las señales de medición.

**Pregunta de investigación:**
Nuestro planteamiento inicial es el siguiente: ¿qué principios científicos permiten que los sensores MQ-137, MH-Z19B, BME280 y de humedad de tierra v1.2 detecten las variables de interés, y cómo sustentan su posible utilización en un sistema de monitoreo experimental para GREENPLANT?

---

## 1 Artículos científicos sobre los principios de la tecnología propuesta

### Sensor MQ-137 para amoníaco

El principio que identificamos en el MQ-137 es la variación de la resistencia eléctrica de un material semiconductor al interactuar con gases. En la versión documentada por Hanwei, el material sensible es dióxido de estaño, SnO₂. Las interacciones del gas con la superficie modifican la disponibilidad de electrones y, por tanto, la conductividad. Frente al amoníaco, la respuesta típica es un aumento de la conductividad y una disminución de la resistencia. Un circuito de lectura convierte ese cambio en una tensión que puede relacionarse con la concentración mediante calibración [[1]](#ref-1), [[2]](#ref-2).

Petric y colaboradores utilizaron un MQ-137 conectado a una plataforma compatible con Arduino y compararon sus mediciones con un analizador profesional. Este antecedente nos permite comprender que una lectura eléctrica necesita una relación de calibración antes de expresarse como concentración. En GREENPLANT, el principio servirá para estudiar variaciones de NH₃ en el aire de la cámara. La temperatura, la humedad, el calentamiento del sensor y la respuesta a otros gases deberán considerarse al interpretar sus lecturas [[1]](#ref-1), [[2]](#ref-2).

### Sensor MH-Z19B para dióxido de carbono

El MH-Z19B utiliza el principio de absorción infrarroja no dispersiva, conocido como NDIR. El CO₂ absorbe radiación infrarroja en bandas características; al atravesar el gas, la intensidad detectada disminuye. La relación entre absorción, recorrido óptico y cantidad de gas permite estimar su concentración a partir de una calibración. Consideramos este principio útil para GREENPLANT porque proporciona una vía óptica de medición distinta de la respuesta resistiva del MQ-137 [[3]](#ref-3), [[4]](#ref-4).

Dubey y colaboradores evaluaron sensores NDIR de otros modelos y mostraron la importancia de compararlos con un instrumento de referencia. Su estudio sustenta el análisis de esta tecnología, pero no valida específicamente nuestro MH-Z19B. Para este modelo recurrimos al manual de Winsen, que establece condiciones de funcionamiento, compensación de temperatura y uso sin condensación. Por ello, no asumimos una precisión absoluta ni independencia total de las condiciones ambientales [[3]](#ref-3), [[4]](#ref-4).

### Sensor BME280 para las condiciones del aire

El BME280 integra mediciones de humedad relativa, presión y temperatura. La documentación de soporte de Bosch identifica un principio capacitivo para la humedad, resistivo para la presión y basado en la tensión de un diodo para la temperatura. En términos físicos, el vapor de agua modifica la respuesta dieléctrica del elemento de humedad; la presión produce cambios en un elemento sensible resistivo; y la temperatura modifica la respuesta eléctrica de la unión semiconductora. El circuito integrado procesa estas variaciones y entrega datos digitales [[5]](#ref-5), [[6]](#ref-6).

En GREENPLANT lo utilizaríamos para registrar las condiciones del aire de la cámara y contextualizar las lecturas de gases. Su temperatura interna puede verse afectada por el calor de la placa y por su propio funcionamiento, de modo que la ubicación debe cuidarse. Grochala y colaboradores incorporaron el BME280 en una plataforma de monitoreo de contaminación atmosférica, lo que constituye un antecedente de su uso junto con sensores de gases, sin demostrar todavía su desempeño en nuestra cámara [[5]](#ref-5), [[7]](#ref-7).

### Sensor capacitivo de humedad de tierra v1.2

El sensor de humedad de tierra v1.2 que consideramos para el proyecto corresponde al tipo capacitivo. Su principio consiste en detectar cambios en las propiedades dieléctricas del medio que rodea la sonda. Como el contenido de agua modifica esas propiedades, también cambia la respuesta del circuito y su tensión de salida. Esta señal permite estimar la humedad mediante una calibración para el suelo o sustrato utilizado; no representa por sí sola un porcentaje universal de agua [[8]](#ref-8).

Placidi y colaboradores estudiaron sensores capacitivos v1.2 dentro de una red de monitoreo agrícola y analizaron la relación entre la salida analógica y el contenido volumétrico de agua. Para GREENPLANT, este antecedente orienta la comparación de la señal con una referencia y la evaluación de la variabilidad entre sensores. La sonda se destinará a humedad del sustrato. No se le atribuye medición de temperatura del suelo; el BME280 registra condiciones del aire y no reemplaza una sonda térmica enterrada [[8]](#ref-8).

### ESP32 y comunicación mediante Wi-Fi y MQTT

El ESP32 no es un sensor de gases: es el microcontrolador que permitiría adquirir y organizar sus señales. La conversión analógica a digital transforma una tensión en un valor numérico; las interfaces digitales permiten recibir datos de los sensores que ya realizan esa conversión internamente. Así, el MQ-137 y la sonda de humedad pueden aportar señales analógicas, mientras que el MH-Z19B y el BME280 ofrecen interfaces digitales. La compatibilidad eléctrica debe comprobarse antes de conectar cada módulo [[9]](#ref-9).

Para comunicar los registros proponemos Wi-Fi y MQTT. Wi-Fi proporciona la conexión inalámbrica, mientras MQTT organiza mensajes mediante publicación y suscripción: un dispositivo publica datos en un tema y un servidor intermediario, llamado bróker, los distribuye a los clientes suscritos. Este fundamento permitiría vincular las lecturas con una aplicación y un registro en la nube. La transmisión no mejora por sí misma la exactitud de los sensores; transporta los datos obtenidos [[10]](#ref-10).

---

## 2 Estado del arte

Los antecedentes revisados muestran que los sensores de bajo costo pueden integrarse en sistemas de monitoreo, pero su utilidad depende de caracterizar sus respuestas. El trabajo de Petric y colaboradores aporta una referencia de medición de amoníaco con MQ-137 y comparación instrumental. El estudio de Dubey y colaboradores aborda la evaluación y calibración de sensores NDIR de CO₂. En conjunto, estos trabajos orientan dos necesidades de GREENPLANT: relacionar la señal con la concentración y comprobar la calidad de esa relación en las condiciones del ensayo [[1]](#ref-1), [[3]](#ref-3).

La plataforma HAPADS de Grochala y colaboradores combina sensores de NO₂ con un BME280 para registrar condiciones ambientales durante recorridos en vehículos. Su aporte para nuestro proyecto es mostrar cómo las variables del aire acompañan e informan la interpretación de las mediciones de gases. La aplicación estudia contaminación atmosférica en movilidad, por lo que no se trasladan sus resultados directamente al monitoreo de NH₃ y CO₂ en una cámara con papa [[7]](#ref-7).

Sawant y colaboradores presentan un sistema agrícola que integra sensores, transmisión inalámbrica y un ESP32 que envía información a Blynk por Wi-Fi. Este antecedente se relaciona con la adquisición y visualización remota previstas para GREENPLANT. Sin embargo, su arquitectura utiliza también módulos nRF24L01 y no constituye una validación específica de nuestra comunicación MQTT. Para sustentar este protocolo utilizamos el estándar de OASIS [[10]](#ref-10), [[11]](#ref-11).

A partir de estos antecedentes, planteamos estudiar la integración de los cuatro sensores seleccionados y un ESP32 para observar gases, humedad del sustrato y condiciones del aire. La necesidad pendiente es conocer cómo se comportará ese conjunto dentro de nuestra cámara ventilada: el movimiento del aire, la ubicación de las sondas y el calentamiento de los componentes pueden modificar lo que se registra. En el TRL 1 establecemos esta base científica; la implementación y las pruebas de desempeño corresponden a etapas posteriores.

---

## 3 Bases de datos

Para localizar y ampliar el sustento bibliográfico consideramos Google Académico, ScienceDirect e IEEE Xplore. Google Académico funciona como buscador de literatura académica; ScienceDirect permite localizar publicaciones y libros científicos; e IEEE Xplore reúne literatura técnica relacionada con electrónica, instrumentación y comunicaciones. Las búsquedas pertinentes para GREENPLANT incluyen “MQ-137 calibration”, “NDIR CO₂ sensor accuracy”, “BME280 environmental monitoring”, “capacitive soil moisture sensor v1.2 calibration” y “ESP32 MQTT sensor monitoring”.

Para esta revisión se identificaron artículos en Hrčak, Sensors y Springer, y antecedentes de titulación en repositorios universitarios. Estas plataformas permiten comprobar autores, títulos, fechas y enlaces a los documentos. También utilizamos documentación de Hanwei, Winsen, Bosch, Espressif y OASIS para distinguir características del modelo y fundamentos de comunicación. Las fichas técnicas complementan los artículos, pero no se presentan como publicaciones científicas arbitradas. En este apartado, “bases de datos” se refiere a fuentes bibliográficas, no a mediciones experimentales ya obtenidas por GREENPLANT.

---

## 4 Libros

Como fundamento de instrumentación identificamos Sensores y acondicionadores de señal, de Ramón Pallás Areny, en la edición registrada por Marcombo de 2004. El libro organiza los sensores según la magnitud eléctrica que cambia o se genera y aborda circuitos de acondicionamiento e interfaces con microcontroladores. Para GREENPLANT nos permite estudiar por qué una variación de resistencia o capacitancia necesita un circuito de lectura y cómo se relacionan sensibilidad, calibración y señal de salida [[12]](#ref-12).

Su aporte se vincula especialmente con la lectura del MQ-137 y del sensor de humedad del suelo. El libro proporciona fundamentos generales de instrumentación; la elección concreta de divisores de tensión, alimentación o reguladores deberá apoyarse también en la documentación de cada componente. No se atribuye al texto una validación particular del módulo LM2596 ni del circuito final del proyecto [[12]](#ref-12).

También consideramos Internet of Things Projects with ESP32, de Agus Kurniawan, publicado por Packt. Esta referencia aborda el desarrollo de proyectos con ESP32 y su conexión con servicios de red. Su utilidad para GREENPLANT es orientar la organización del sistema de adquisición y comunicación que acompañará a los sensores. El fundamento de MQTT se respalda de manera específica con el estándar de OASIS, evitando confundir la comunicación de datos con el principio físico de medición [[10]](#ref-10), [[13]](#ref-13).

---

## 5 Tesis

Como antecedente de titulación, Adrià Jurado Morros desarrolló el trabajo Diseño e implementación de un sistema para la monitorización de la calidad del aire en interiores, en la Universitat Politècnica de Catalunya. El sistema integra un ESP32 con sensores BME680, PMSA003 y MH-Z19B y presenta los datos en una pantalla. Para GREENPLANT, su aporte es documentar una integración del sensor de CO₂ seleccionado con el microcontrolador y la visualización de registros. El BME680 utilizado en ese trabajo es un modelo diferente del BME280 de nuestro proyecto [[14]](#ref-14).

Otro antecedente es Desarrollo de un medidor de bajo coste del nivel de CO₂ en el aire, de Jaime Huarte Rubio, de la Universidad de Zaragoza. Este trabajo de fin de grado se enfoca en un dispositivo de medición de CO₂ e incluye el estudio de la comunicación del MH-Z19B y de los modos Wi-Fi del ESP32. Consideramos que orienta el análisis de la conexión entre sensor, procesamiento y comunicación, aunque su aplicación no corresponde a una cámara agrícola con amoníaco [[15]](#ref-15).

Ambos trabajos se incorporan como antecedentes de grado dentro del apartado de tesis, respetando su denominación institucional. Su función es mostrar experiencias documentadas con componentes relacionados. Sus resultados no prueban la exactitud del sistema GREENPLANT ni sustituyen la caracterización de nuestros propios sensores.

Con esta revisión, el TRL 1 de GREENPLANT queda centrado en los principios resistivos, ópticos, capacitivos y electrónicos que sustentan las mediciones propuestas. A futuro, ese conocimiento podrá apoyar el diseño de una herramienta de monitoreo para ensayos con papa, cuyo funcionamiento y alcance deberán comprobarse experimentalmente.

## Referencias bibliográficas

<a id="ref-1"></a>

[1] M. Petric, F. Dodigović, I. Grčić, P. Markužić, L. Radetić, and M. Topić, “Ammonia concentration monitoring using Arduino platform,” Environmental Engineering – Inženjerstvo okoliša, vol. 6, no. 1, pp. 21–26, 2019, doi: 10.37023/ee.6.1.4.

<a id="ref-2"></a>

[2] Hanwei Electronics, “Technical data MQ-137 gas sensor,” datasheet. Accessed: Oct. 23, 2026. [Online]. Available: <https://www.mysensors.org/dl/57c3ebeb071cb0e34c90057a/design/NH3.pdf>

<a id="ref-3"></a>

[3] R. Dubey et al., “Low-cost CO₂ NDIR sensors: Performance evaluation and calibration using machine learning techniques,” Sensors, vol. 24, no. 17, Art. no. 5675, 2024, doi: 10.3390/s24175675.

<a id="ref-4"></a>

[4] Zhengzhou Winsen Electronics Technology, “Infrared CO₂ sensor module MH-Z19B user’s manual,” ver. 1.7, 2020. Accessed: Oct. 23, 2026. [Online]. Available: <https://www.winsen-sensor.com/d/files/manual/mh-z19b.pdf>

<a id="ref-5"></a>

[5] Bosch Sensortec, “BME280 data sheet,” rev. 1.23, 2022. Accessed: Oct. 23, 2026. [Online]. Available: <https://www.bosch-sensortec.com/media/boschsensortec/downloads/datasheets/bst-bme280-ds002.pdf>

<a id="ref-6"></a>

[6] Bosch Sensortec Community, “BME280 measuring principle,” technical support response. Accessed: Oct. 23, 2026. [Online]. Available: <https://community.bosch-sensortec.com/mems-sensors-forum-jrmujtaw/post/bme280-measuring-principle-Z1EkEDoeOd9APwT>

<a id="ref-7"></a>

[7] D. Grochala et al., “Highly accurate and autonomous programmable platform for providing air pollution data services to drivers and the public – Polish case study,” Sensors and Actuators B: Chemical, vol. 447, Art. no. 138859, 2026, doi: 10.1016/j.snb.2025.138859.

<a id="ref-8"></a>

[8] P. Placidi, R. Morbidelli, D. Fortunati, N. Papini, F. Gobbi, and A. Scorzoni, “Monitoring soil and ambient parameters in the IoT precision agriculture scenario: An original modeling approach dedicated to low-cost soil water content sensors,” Sensors, vol. 21, no. 15, Art. no. 5110, 2021, doi: 10.3390/s21155110.

<a id="ref-9"></a>

[9] Espressif Systems, “ESP32 series datasheet,” ver. 5.3, 2026. Accessed: Oct. 23, 2026. [Online]. Available: <https://documentation.espressif.com/esp32_datasheet_en.html>

<a id="ref-10"></a>

[10] OASIS, MQTT Version 5.0, OASIS Standard, Mar. 2019. Accessed: Oct. 23, 2026. [Online]. Available: <https://docs.oasis-open.org/mqtt/mqtt/v5.0/os/mqtt-v5.0-os.html>

<a id="ref-11"></a>

[11] N. R. Sawant, A. Kumar, S. Pant, and K. Kotecha, “An IoT-driven machine learning system for real-time smart crop recommendation and optimization in precision agriculture,” Discover Artificial Intelligence, vol. 6, Art. no. 194, 2026, doi: 10.1007/s44163-026-00896-y.

<a id="ref-12"></a>

[12] R. Pallás Areny, Sensores y acondicionadores de señal. Marcombo, 2004.

<a id="ref-13"></a>

[13] A. Kurniawan, Internet of Things Projects with ESP32: Build Exciting and Powerful IoT Projects Using the All-New Espressif ESP32. Packt Publishing, 2019.

<a id="ref-14"></a>

[14] A. Jurado Morros, “Diseño e implementación de un sistema para la monitorización de la calidad del aire en interiores,” Trabajo de fin de grado, Universitat Politècnica de Catalunya, España, 2024. [Online]. Available: <https://hdl.handle.net/2117/417562>

<a id="ref-15"></a>

[15] J. Huarte Rubio, “Desarrollo de un medidor de bajo coste del nivel de CO₂ en el aire,” Trabajo de fin de grado, Universidad de Zaragoza, España, 2021. [Online]. Available: <https://zaguan.unizar.es/record/112323>

---

<div align="center">

*GREENPLANT · TRL 1 · Proyecto Integrador · 2026*

</div>
