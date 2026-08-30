# Universidad Peruana Cayetano Heredia

## Facultad de Ciencias e Ingeniería

### Departamento Académico de Ingeniería

### Ingeniería Informática e Ingeniería Industrial

**Semestre Académico:** 2026 II – VI Ciclo  
**Semana N.° 1**  
**Tema:** Lista de exigencias  
**Curso:** Proyecto Integrador – Práctica N.° 1  
**Año:** 2026  
**Lugar:** Lima – Perú

---

## Docentes

- Ing. Umbert Lewis De La Cruz Rodriguez
- Ing. Vanessa Stefanny Stefanny Arevalo

---

## Integrantes del equipo

| Integrante | Aporte/s en específico | % de aporte |
|---|---|---:|
| Cesar Rodrigo Milla Gómez | Definió la función general del sistema, las señales de entrada y salida, y los aspectos relacionados con la seguridad del prototipo y el manejo de alertas. | 25% |
| Anderson Josue Delerna Infantes | Diseñó el tamaño y la forma del prototipo, la alimentación de energía, el sistema de control, el software, la fabricación y la planificación de las etapas del proyecto. | 25% |
| Kevin Esty Carvallo Neciosup | Trabajó en la integración de los sensores, sensor de movimiento, GPS, microcontrolador, control de las mediciones, software y funcionamiento general del sistema. | 25% |
| Shedira Lumeris Sihuincha Palacin | Revisó la resistencia de la estructura, la parte electrónica, las comunicaciones, ergonomía, control de calidad, transporte y costos del prototipo. | 25% |

**Equipo:** Informe final – 100%

---

# 1. Lista de Exigencias

**Páginas:** 5  
**Edición:** Rev. 1  
**Proyecto:** **DriveSafe AI – Sistema inteligente de monitoreo y detección de somnolencia del conductor**  
**Cliente:** Universidad Peruana Cayetano Heredia (UPCH)  
**Fecha:** 30/08/2026  
**Elaborado:** K.C, A.D, C.M, L.S

---

## 1.1 Función general

**Tipo:** Exigencia (E)

El sistema deberá permitir monitorear al conductor durante la conducción mediante una cámara y sensores, con el objetivo de identificar posibles signos de somnolencia, pérdida de atención y cambios de postura asociados.

El sistema deberá analizar indicadores visuales como apertura de los ojos, posición del rostro y postura del conductor, así como información relacionada con los movimientos y la ubicación del vehículo.

La información será procesada mediante algoritmos de inteligencia artificial para identificar patrones de riesgo y generar una alerta cuando corresponda.

Los datos obtenidos podrán registrarse para evaluar posteriormente el comportamiento del sistema.

La detección de somnolencia se justifica debido a que la fatiga puede afectar la atención, el tiempo de reacción y la capacidad para conducir de manera segura.

**Responsables:** C.M, K.C, A.D, L.S

---

## 1.2 Geometría

**Tipo:** Exigencia (E)

El prototipo no requerirá mecanismos automatizados de movimiento durante el monitoreo. La cámara, el sensor de movimiento y los demás componentes permanecerán instalados en posiciones definidas para mantener una captura estable del conductor.

La estructura deberá permitir realizar ajustes manuales de orientación durante la instalación para conseguir un encuadre adecuado del rostro y la postura.

El sensor de movimiento deberá instalarse en una posición estable que permita registrar adecuadamente los movimientos e inclinaciones del dispositivo o vehículo.

El módulo GPS deberá ubicarse de manera que permita una adecuada recepción de las señales de posicionamiento.

**Responsable:** A.D

---

## 1.3 Cinemática

**Tipo:** Exigencia (E)

El prototipo no requerirá mecanismos de movimiento continuo durante la operación. La cámara permanecerá estática durante el monitoreo para evitar variaciones en la captura de imágenes.

El sensor de movimiento permitirá detectar cambios de orientación, inclinaciones y movimientos del dispositivo o vehículo.

Los movimientos detectados deberán utilizarse como información complementaria para el análisis del comportamiento del conductor.

**Responsable:** K.C

---

## 1.4 Fuerzas

**Tipo:** Exigencia (E)

La estructura deberá soportar el peso de la cámara, sensores, sensor de movimiento, GPS, microcontrolador y demás componentes instalados, manteniendo su posición durante el funcionamiento.

Los elementos de fijación deberán resistir vibraciones y movimientos propios del vehículo para evitar que la cámara pierda el encuadre del conductor.

La estructura deberá permanecer estable y evitar desplazamientos que puedan afectar la captura de imágenes, el funcionamiento del sensor de movimiento o la recepción de los datos del GPS.

**Responsable:** L.S

---

## 1.5 Energía

**Tipo:** Exigencia (E)

El sistema deberá funcionar mediante una fuente de alimentación de bajo voltaje compatible con el microcontrolador, cámara, sensores, sensor de movimiento, módulo GPS y dispositivos de alerta.

Se deberá priorizar una fuente estable que permita mantener el funcionamiento durante todo el periodo de monitoreo.

El sistema deberá permitir verificar la disponibilidad de alimentación para evitar interrupciones durante la adquisición y procesamiento de datos.

Los sensores y módulos deberán alimentarse respetando los niveles de tensión especificados por sus fabricantes.

**Responsable:** A.D

---

## 1.6 Materia

**Tipo:** Exigencia (E)

El sistema deberá utilizar materiales adecuados para fabricar la carcasa y los soportes de los componentes electrónicos.

La estructura deberá proteger la cámara, sensores, sensor de movimiento, GPS, microcontrolador y conexiones frente a golpes, vibraciones y manipulación durante el uso.

Los materiales deberán permitir una fabricación sencilla y facilitar el acceso a los componentes para realizar mantenimiento, pruebas y reemplazos.

**Responsable:** L.S

---

## 1.7 Señales (Información)

**Tipo:** Exigencia (E)

El sistema deberá contar con señales de entrada y salida asociadas al proceso de monitoreo y detección del estado del conductor.

### Señales de entrada

- Imagen y video capturados mediante la cámara.
- Apertura y cierre de los ojos.
- Frecuencia y duración del parpadeo.
- Orientación y posición del rostro.
- Movimientos de la cabeza.
- Postura corporal del conductor.
- Bostezos u otros indicadores visuales asociados a la somnolencia.
- Información proveniente de los sensores utilizados.
- Datos del sensor de movimiento para identificar movimientos, inclinaciones y cambios de orientación del conductor o del dispositivo.
- Datos de ubicación y desplazamiento obtenidos mediante el GPS.
- Estado inicial del sistema y parámetros configurados para el monitoreo.

### Señales de salida

- Estado estimado de atención del conductor.
- Indicadores detectados de somnolencia.
- Cambios de postura identificados.
- Nivel o condición de riesgo.
- Alerta visual, sonora o vibratoria ante la detección de un patrón de riesgo.
- Estado de funcionamiento de los sensores y componentes.
- Registro de eventos detectados durante el monitoreo.
- Historial de las detecciones y alertas generadas.
- Datos de ubicación asociados a los eventos de riesgo.
- Datos procesados para la evaluación posterior del comportamiento del sistema.

Las señales obtenidas mediante la cámara, el sensor de movimiento, el GPS y los demás sensores permitirán analizar diferentes indicadores relacionados con el estado del conductor y las condiciones de conducción.

La información será procesada para identificar patrones asociados con somnolencia, pérdida de atención y cambios de postura, considerando indicadores como el cierre de los ojos, parpadeo, orientación de la cabeza, movimientos y postura corporal.

Los datos del sensor de movimiento permitirán complementar el análisis de los movimientos y orientación, mientras que el GPS permitirá asociar los eventos detectados con su ubicación durante el monitoreo.

A partir de esta información, el sistema podrá determinar el nivel de riesgo y generar una alerta cuando corresponda.

**Responsables:** K.C, C.M

---

## 1.8 Control

**Tipo:** Exigencia (E)

El sistema de control deberá coordinar la adquisición de información proveniente de la cámara, los sensores, el sensor de movimiento y el GPS, realizar el procesamiento de los datos y ejecutar el análisis correspondiente.

La secuencia deberá contemplar:

1. Captura de información.
2. Procesamiento de datos.
3. Extracción de características.
4. Análisis mediante inteligencia artificial.
5. Clasificación del estado del conductor.
6. Análisis de movimiento.
7. Análisis de ubicación.
8. Generación de alerta.
9. Registro de información.

El sistema deberá evitar generar alertas únicamente a partir de una observación aislada, considerando conjuntamente los indicadores visuales, los movimientos detectados y la información de ubicación para disminuir posibles falsas detecciones.

**Responsables:** A.D, K.C

---

## 1.9 Electrónico (Hardware)

**Tipo:** Exigencia (E)

El sistema utilizará un microcontrolador o controlador electrónico con capacidad suficiente para adquirir información de la cámara, sensores, sensor de movimiento y módulo GPS, además de comunicarse con los demás componentes.

Se podrá considerar un ESP32 como plataforma de referencia debido a sus interfaces GPIO, I2C, SPI y UART, además de sus capacidades de procesamiento y comunicación.

El hardware deberá permitir la integración del sensor de movimiento para detectar movimientos e inclinaciones del dispositivo y del módulo GPS para obtener información de ubicación y desplazamiento.

Los componentes deberán encontrarse correctamente conectados y protegidos para garantizar el funcionamiento del prototipo.

**Responsables:** K.C, L.S

---

## 1.10 Software

**Tipo:** Exigencia (E)

El software deberá permitir adquirir, procesar, almacenar y visualizar la información obtenida durante el monitoreo.

Deberá incorporar técnicas de visión artificial para identificar características del rostro y postura del conductor.

También deberá incorporar algoritmos de procesamiento para analizar los datos provenientes del sensor de movimiento y del GPS.

El procesamiento deberá permitir relacionar los indicadores visuales con los movimientos, cambios de orientación y datos de ubicación del vehículo para determinar el estado del conductor y generar alertas cuando corresponda.

El sistema deberá permitir registrar los eventos detectados y almacenar información relevante para su evaluación posterior.

**Responsables:** A.D, K.C

---

## 1.11 Comunicaciones

**Tipo:** Exigencia (E)

El sistema deberá permitir la comunicación entre el microcontrolador, la cámara, los sensores, el sensor de movimiento, el GPS y los demás componentes utilizados.

Cuando sea necesario transmitir información hacia una aplicación o interfaz de usuario, podrá utilizarse Wi-Fi, Bluetooth u otra comunicación disponible en la arquitectura seleccionada.

La comunicación deberá permitir transmitir los resultados del monitoreo y las alertas sin afectar el funcionamiento básico del sistema.

**Responsable:** L.S

---

## 1.12 Seguridad

**Tipo:** Exigencia (E)

Los componentes electrónicos deberán encontrarse protegidos frente a golpes, polvo, humedad y manipulación accidental.

La alimentación eléctrica deberá trabajar con niveles seguros para el usuario y deberá evitar el contacto directo con partes energizadas.

El sistema deberá incorporar protección frente a cortocircuitos, conexiones incorrectas y condiciones eléctricas que puedan comprometer los componentes.

La carcasa no deberá presentar bordes o superficies que generen riesgos durante la manipulación.

Las alertas deberán ser claras y no deberán generar una distracción adicional para el conductor.

Debido a que el sistema interviene en una función relacionada con la seguridad vial, se deberán realizar pruebas y validaciones antes de considerar confiables las detecciones.

**Responsable:** C.M

---

## 1.13 Ergonomía

**Tipo:** Exigencia (E)

El equipo deberá instalarse de manera que no interfiera con el campo visual del conductor ni con los controles normales del vehículo.

La cámara deberá ubicarse de manera que pueda obtener información suficiente del rostro y postura sin requerir movimientos adicionales por parte del conductor.

El sistema deberá ser sencillo de utilizar y requerir una intervención mínima durante la conducción.

Las alertas deberán ser fáciles de interpretar y no deberán generar una carga de interacción innecesaria.

**Responsable:** L.S

---

## 1.14 Fabricación

**Tipo:** Exigencia (E)

El prototipo deberá poder fabricarse utilizando materiales y componentes disponibles comercialmente.

La carcasa y los soportes podrán fabricarse mediante impresión 3D, mecanizado u otros procedimientos accesibles para el equipo.

Se deberán priorizar componentes de fácil adquisición y reemplazo, procurando que la estructura pueda modificarse durante las etapas de prueba y validación sin requerir una fabricación compleja.

**Responsables:** K.C, A.D

---

## 1.15 Control de calidad

**Tipo:** Exigencia (E)

Antes de realizar las pruebas de funcionamiento, la cámara, sensores, sensor de movimiento, GPS y componentes electrónicos deberán ser revisados para comprobar su correcto funcionamiento.

Se deberán realizar pruebas de:

- Captura de imágenes.
- Detección facial.
- Reconocimiento de patrones de somnolencia.
- Detección de movimientos.
- Adquisición de datos de ubicación.
- Comunicación entre componentes.
- Generación de alertas.
- Registro de eventos.

También se deberá comprobar el funcionamiento conjunto del sistema y registrar los resultados obtenidos para identificar errores y realizar mejoras.

**Responsable:** L.S

---

## 1.16 Montaje

**Tipo:** Exigencia (E)

El diseño deberá ser modular para permitir el montaje y desmontaje de la cámara, sensores, sensor de movimiento, GPS, microcontrolador, alimentación y demás componentes.

Las conexiones deberán estar identificadas y protegidas para evitar conexiones incorrectas durante la instalación.

El sensor de movimiento deberá instalarse en una posición estable para obtener correctamente los movimientos y cambios de orientación.

El GPS deberá ubicarse de manera que permita una adecuada recepción de las señales de posicionamiento.

La estructura deberá permitir reemplazar componentes sin necesidad de reconstruir completamente el prototipo y deberá facilitar las actividades de mantenimiento y pruebas.

**Responsables:** L.S, C.M

---

## 1.17 Transporte

**Tipo:** Exigencia (E)

El dispositivo deberá ser transportable manualmente entre diferentes espacios de trabajo, laboratorios o vehículos de prueba.

La carcasa deberá proteger la cámara, sensores, microcontrolador, sensor de movimiento, GPS y conexiones durante el traslado.

Los componentes deberán mantenerse asegurados para reducir el riesgo de golpes, desconexiones o daños que puedan afectar posteriormente el funcionamiento del sistema.

**Responsable:** L.S

---

## 1.18 Uso

**Tipo:** Deseo (D)

Se desea que el sistema pueda utilizarse de manera sencilla durante una sesión de conducción.

La secuencia de utilización deberá ser:

**Instalar el dispositivo → orientar la cámara hacia el conductor → encender el sistema → iniciar el monitoreo → analizar los indicadores visuales, movimientos y ubicación → identificar un patrón de riesgo → generar una alerta → registrar el evento.**

El funcionamiento deberá requerir una intervención mínima por parte del conductor para evitar generar distracciones adicionales durante la conducción.

**Responsable:** K.C

---

## 1.19 Mantenimiento

**Tipo:** Exigencia (E)

La cámara y los sensores deberán poder limpiarse periódicamente para mantener la calidad de las mediciones y detecciones.

El sensor de movimiento y el GPS deberán poder revisarse y reemplazarse en caso de falla.

Las conexiones deberán revisarse periódicamente para detectar cables sueltos, daños o desconexiones.

Los componentes electrónicos deberán poder reemplazarse individualmente sin desmontar completamente el prototipo.

El software y los modelos utilizados podrán actualizarse cuando sea necesario.

**Responsables:** A.D

---

## 1.20 Costos

**Tipo:** Exigencia (E)

Se buscará que el prototipo utilice componentes comerciales de costo accesible.

El costo deberá considerar principalmente:

- Microcontrolador.
- Cámara.
- Sensor de movimiento.
- Módulo GPS.
- Sensores adicionales.
- Dispositivos de alerta.
- Fuente de alimentación.
- Carcasa.
- Materiales de fabricación.
- Cables y conectores.

Se priorizarán componentes disponibles comercialmente, de fácil adquisición y reemplazo, manteniendo como prioridad el funcionamiento y confiabilidad del sistema.

**Responsable:** L.S

---

## 1.21 Plazos

**Tipo:** Exigencia (E)

El proyecto comprenderá las etapas de:

1. Definición del problema.
2. Revisión del estado de la tecnología.
3. Selección de sensores.
4. Diseño del prototipo.
5. Diseño electrónico.
6. Desarrollo del software.
7. Integración de cámara y sensores.
8. Integración del sensor de movimiento.
9. Integración del GPS.
10. Desarrollo del algoritmo de inteligencia artificial.
11. Fabricación del prototipo.
12. Integración general del sistema.
13. Calibración y configuración.
14. Pruebas experimentales.
15. Validación del sistema.
16. Registro y análisis de resultados.
17. Mejoras finales del prototipo.

Las fechas específicas deberán establecerse mediante el plan de trabajo del proyecto.

**Responsables:** A.D, K.C

---

# 2. Bibliografía

[1] National Highway Traffic Safety Administration (NHTSA). *Drowsy Driving*, 2026.

[2] Centers for Disease Control and Prevention / National Institute for Occupational Safety and Health (CDC/NIOSH). *Driver Fatigue on the Job*, 2024.

[3] National Highway Traffic Safety Administration (NHTSA). *Advanced Impaired Driving Prevention Technology*, 2024.

[4] World Health Organization (WHO). *Global Status Report on Road Safety*, 2023.

[5] Espressif Systems. *ESP32-WROOM-32D & ESP32-WROOM-32U Datasheet*, 2025.

[6] Google AI for Developers. *MediaPipe Face Landmarker*, 2026.

[7] OpenCV. *OpenCV Documentation*, 2025.

[8] International Organization for Standardization (ISO). *ISO 21448:2022 — Road vehicles — Safety of the intended functionality*, 2022.

[9] International Organization for Standardization (ISO). *ISO 12100:2010 — Safety of machinery — General principles for design — Risk assessment and risk reduction*, 2010.

[10] International Organization for Standardization (ISO). *ISO 9241-210:2019 — Ergonomics of human-system interaction — Human-centred design for interactive systems*, 2019.

[11] International Organization for Standardization (ISO). *ISO 9241-115:2024 — Ergonomics of human-system interaction — Guidance on conceptual design, user-system interaction design, user interface design and navigation design*, 2024.

[12] International Organization for Standardization (ISO). *ISO 9001:2015 — Quality management systems — Requirements*, 2015.

[13] Dahiya, A., et al. *Technologies for detecting and monitoring drivers' states: A systematic review*, Heliyon, 2024.

[14] TDK InvenSense. *Motion Sensor / IMU Documentation*, 2013.

[15] u-blox. *GPS/GNSS Module Documentation*, 2016.