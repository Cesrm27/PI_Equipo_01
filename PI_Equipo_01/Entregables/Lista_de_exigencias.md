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
- Ing. Vanessa Stefany Stefany Arevalo

---

## Integrantes del equipo

| Integrante | Aporte/s en específico | % de aporte |
|---|---|---:|
| Cesar Rodrigo Milla Gómez | Definió la función general del sistema, las señales de entrada y salida, y se encargó de los aspectos relacionados con la seguridad del prototipo y el manejo de los gases durante los ensayos. | 25% |
| Anderson Josue Delerna Infantes | Diseño del tamaño y la forma de la cámara experimental, la alimentación de energía, el sistema de control, el software, la fabricación y la planificación de las etapas del proyecto. | 25% |
| Kevin Esty Carvallo Neciosup | Trabajó en la integración de los sensores, el hardware y microcontrolador, el control de las mediciones y la adquisición de datos. | 25% |
| Integrante 4 | Apoyo en la integración, pruebas, documentación y validación del prototipo. | 25% |

---

# LISTA DE EXIGENCIAS

| Fecha de cambios | Diseño o Exigencia | Descripción | Responsable |
|---|---|---|---|
| 30/08/2026 | E | **Función general:** El sistema deberá permitir monitorear al conductor durante la conducción mediante una cámara y sensores, con el objetivo de identificar posibles signos de somnolencia y cambios de postura asociados a pérdida de atención. El sistema deberá analizar indicadores visuales como apertura y cierre de los ojos, posición del rostro y postura del conductor, además de utilizar información proveniente del sensor de movimiento y GPS. La información será procesada mediante algoritmos de inteligencia artificial y permitirá generar una alerta cuando se detecte un patrón de riesgo. Los datos obtenidos podrán registrarse para su evaluación posterior. **Fuente:** NHTSA (2026); CDC/NIOSH (2024). | C.M., K.C., A.D., L.S. |
| 30/08/2026 | E | **Geometría:** El prototipo no requerirá mecanismos de movimiento durante el monitoreo. La cámara, el sensor de movimiento y los demás sensores permanecerán instalados en posiciones definidas para mantener una captura estable del conductor. La estructura deberá permitir realizar ajustes manuales de orientación durante la instalación para conseguir un encuadre adecuado del rostro y la postura, sin necesidad de incorporar mecanismos de movimiento. **Fuente:** ISO 21448:2022. | A.D. |
| 30/08/2026 | E | **Cinemática:** El prototipo no requerirá mecanismos de movimiento continuo durante la operación. La cámara y los sensores permanecerán estáticos durante cada medición para evitar variaciones en la captura de información. El sensor de movimiento permitirá detectar movimientos, inclinaciones y cambios de orientación del conductor sin necesidad de desplazar físicamente la estructura. **Fuente:** ISO 21448:2022. | K.C. |
| 30/08/2026 | E | **Fuerzas:** La estructura deberá soportar el peso de la cámara, sensores, sensor de movimiento, GPS, microcontrolador y demás componentes instalados, manteniendo su posición durante el funcionamiento. Los elementos de fijación deberán resistir vibraciones y movimientos propios del vehículo para evitar que la cámara pierda el encuadre del conductor o que los sensores presenten errores de medición. **Fuente:** ISO 12100:2010. | L.S. |
| 30/08/2026 | E | **Energía:** El sistema deberá funcionar mediante una fuente de alimentación de bajo voltaje compatible con el microcontrolador, cámara, sensor de movimiento, GPS y dispositivos de alerta utilizados. Se deberá priorizar una alimentación estable durante todo el periodo de monitoreo. Si se utiliza un ESP32, se deberán respetar las especificaciones eléctricas correspondientes al módulo seleccionado. **Fuente:** Espressif Systems (2025). | A.D. |
| 30/08/2026 | E | **Material:** El sistema deberá utilizar materiales adecuados para fabricar la carcasa y los soportes de los componentes electrónicos. La estructura deberá proteger la cámara, microcontrolador, sensor de movimiento, GPS y demás sensores frente a golpes, polvo y manipulación durante el uso. Los materiales empleados deberán permitir una fabricación sencilla, facilitar el acceso a los componentes y evitar que la estructura interfiera con el campo de visión de la cámara. | L.S. |
| 30/08/2026 | E | **Señales (Información):** El sistema deberá contar con señales de entrada y salida asociadas al proceso de monitoreo del conductor. **Señales de entrada:** imagen y video capturados mediante la cámara; apertura y cierre de los ojos; frecuencia y duración del parpadeo; orientación y posición del rostro; movimientos de la cabeza; postura corporal del conductor; bostezos u otros indicadores visuales asociados a la somnolencia; información proveniente de los sensores utilizados; datos del sensor de movimiento para identificar movimientos, inclinaciones y cambios de orientación del conductor; datos de ubicación y desplazamiento obtenidos mediante el GPS; estado inicial del sistema y parámetros configurados para el monitoreo. **Señales de salida:** estado estimado de atención del conductor; indicadores detectados de somnolencia; cambios de postura identificados; nivel o condición de riesgo; alerta visual, sonora o vibratoria ante la detección de un patrón de riesgo; estado de funcionamiento de los sensores y componentes; registro de eventos detectados durante el monitoreo; historial de detecciones y alertas generadas; datos de ubicación asociados a los eventos de riesgo; datos procesados para la evaluación posterior del comportamiento del sistema. **Fuente:** NHTSA (2024); CDC/NIOSH (2024); Dahiya et al. (2024). | K.C., C.M. |
| 30/08/2026 | E | **Procesamiento y control:** El sistema de control deberá coordinar la adquisición de información proveniente de la cámara y los sensores, realizar el procesamiento de los datos y ejecutar el análisis correspondiente. La secuencia deberá contemplar captura, procesamiento, extracción de características, análisis mediante inteligencia artificial, clasificación del estado del conductor, generación de alertas y registro de información. El sistema deberá evitar generar alertas únicamente a partir de una observación aislada, considerando un patrón de comportamiento para disminuir posibles falsas detecciones. El GPS deberá permitir asociar los eventos detectados con su ubicación y el sensor de movimiento deberá complementar el análisis de orientación y movimiento. **Fuente:** ISO 21448:2022; NHTSA (2024). | A.D., K.C. |
| 30/08/2026 | E | **Electrónico (hardware):** El sistema utilizará un microcontrolador o controlador electrónico con capacidad suficiente para adquirir información de la cámara, sensor de movimiento, GPS y demás sensores, así como comunicarse con los demás componentes. Se podrá considerar un ESP32 como plataforma de referencia debido a sus interfaces GPIO, I2C, SPI, UART, ADC, Wi-Fi y Bluetooth, además de su capacidad de procesamiento. El hardware deberá permitir la integración de la cámara, sensor de movimiento, GPS y dispositivos de alerta de acuerdo con los requerimientos del prototipo. **Fuente:** Espressif Systems (2025). | K.C., L.S. |
| 30/08/2026 | E | **Software:** El software deberá permitir adquirir, procesar, almacenar y visualizar la información obtenida durante el monitoreo. Deberá incorporar técnicas de visión artificial para identificar características del rostro y postura, además de algoritmos de Machine Learning para analizar los patrones asociados al estado del conductor. El procesamiento deberá integrar la información de la cámara, sensor de movimiento y GPS para mejorar la identificación de eventos de riesgo. El procesamiento podrá utilizar herramientas de visión artificial y modelos de detección facial capaces de obtener puntos de referencia del rostro y realizar seguimiento durante una transmisión de video. **Fuente:** Google AI for Developers (2026); OpenCV (2025); Dahiya et al. (2024). | A.D., K.C. |
| 30/08/2026 | E | **Comunicaciones:** El sistema deberá permitir la comunicación entre el microcontrolador, los sensores y los componentes utilizados. Cuando sea necesario transmitir información hacia una computadora, aplicación o interfaz de usuario, podrá utilizarse Wi-Fi, Bluetooth u otra comunicación disponible en la arquitectura seleccionada. La comunicación deberá permitir transmitir los resultados del monitoreo, ubicación de eventos y alertas sin afectar el funcionamiento básico del sistema. **Fuente:** Espressif Systems (2025). | L.S. |
| 30/08/2026 | E | **Seguridad:** Los componentes electrónicos deberán encontrarse protegidos frente a contactos accidentales, golpes y manipulación durante el funcionamiento. La alimentación eléctrica deberá utilizar niveles adecuados para los componentes y contar con conexiones correctamente aisladas. Además, el sistema deberá priorizar que las alertas generadas sean claras y no provoquen una distracción adicional al conductor. Debido a que el sistema interviene en una función relacionada con la seguridad vial, deberán considerarse procesos de identificación de riesgos, verificación y validación de su funcionamiento. **Fuente:** ISO 12100:2010; ISO 21448:2022. | C.M. |
| 30/08/2026 | E | **Ergonomía:** El equipo deberá instalarse de manera que no interfiera con el campo visual del conductor, los controles del vehículo ni la posición normal de conducción. La cámara deberá ubicarse de forma que pueda obtener información suficiente sin requerir movimientos adicionales por parte del conductor. El sensor de movimiento y el GPS deberán instalarse en posiciones que permitan obtener información confiable sin afectar la interacción del usuario. Las alertas deberán ser fáciles de interpretar y no deberán generar una carga de interacción innecesaria. **Fuente:** ISO 9241-210:2019; ISO 9241-115:2024. | L.S. |
| 30/08/2026 | E | **Fabricación:** El prototipo deberá poder fabricarse utilizando materiales y componentes disponibles comercialmente. La carcasa y soportes podrán fabricarse mediante impresión 3D, mecanizado u otros procedimientos accesibles para el equipo. Se deberán priorizar componentes de fácil adquisición y reemplazo, procurando que la estructura pueda modificarse durante las etapas de prueba y validación sin requerir una fabricación compleja. | K.C., A.D. |
| 30/08/2026 | E | **Control de calidad:** Antes de realizar las pruebas de funcionamiento, la cámara, sensor de movimiento, GPS y demás componentes electrónicos deberán ser revisados para comprobar su correcto funcionamiento. Se deberán realizar pruebas de captura de imágenes, detección facial, reconocimiento de patrones de somnolencia, comunicación, adquisición de ubicación, detección de movimiento y generación de alertas. Se deberán verificar los resultados obtenidos para identificar errores y realizar mejoras. El control sistemático de procesos, medición y evaluación contribuye a mantener la calidad del sistema. **Fuente:** ISO 9001:2015. | L.S. |
| 30/08/2026 | E | **Montaje:** El diseño deberá ser modular para permitir el montaje y desmontaje de la cámara, sensores, sensor de movimiento, GPS, microcontrolador, alimentación y demás componentes. Las conexiones deberán estar identificadas y protegidas para evitar conexiones incorrectas durante la instalación. La estructura deberá permitir reemplazar componentes sin necesidad de reconstruir completamente el prototipo y deberá facilitar las actividades de mantenimiento y pruebas. | L.S., C.M. |
| 30/08/2026 | E | **Transporte:** El dispositivo deberá ser transportable manualmente entre diferentes espacios de trabajo, laboratorios o vehículos de prueba. La carcasa deberá proteger la cámara, sensores, sensor de movimiento, GPS, microcontrolador y conexiones durante el traslado. Los componentes deberán mantenerse asegurados para reducir el riesgo de golpes, desconexiones o daños que puedan afectar posteriormente el funcionamiento del sistema. | L.S. |
| 30/08/2026 | D | **Uso:** Se desea que el sistema pueda utilizarse de manera sencilla durante una sesión de conducción o prueba. La secuencia de utilización deberá ser: instalar el dispositivo → orientar la cámara hacia el conductor → encender el sistema → iniciar el monitoreo → analizar los indicadores visuales y datos de sensores → identificar un patrón de riesgo → generar una alerta → registrar el evento y su ubicación. El funcionamiento deberá requerir una intervención mínima del conductor para evitar generar distracciones adicionales durante la conducción. **Fuente:** NHTSA (2026); CDC/NIOSH (2024). | K.C. |
| 30/08/2026 | E | **Mantenimiento:** La cámara y los sensores deberán poder limpiarse periódicamente para mantener la calidad de las mediciones y de las imágenes. Las conexiones deberán revisarse para detectar cables sueltos o componentes dañados. El software y los modelos utilizados podrán actualizarse cuando sea necesario, mientras que los componentes electrónicos deberán poder reemplazarse individualmente en caso de falla. El sensor de movimiento y el GPS deberán revisarse para comprobar que continúan proporcionando información adecuada. | A.D. |
| 30/08/2026 | E | **Costos:** Se buscará que el prototipo utilice componentes comerciales de costo accesible y disponibles en el mercado. Como criterio inicial, se deberán priorizar componentes que permitan implementar las funciones de captura, procesamiento, comunicación, ubicación, detección de movimiento y alerta sin incrementar innecesariamente el costo del prototipo. El costo final deberá determinarse considerando el microcontrolador, cámara, sensor de movimiento, GPS, demás sensores, elementos de alerta, alimentación, carcasa y materiales de fabricación. | L.S. |
| 30/08/2026 | E | **Plazos:** El proyecto comprenderá las etapas de definición del problema, revisión del estado de la tecnología, selección de componentes, diseño del prototipo, desarrollo del software y algoritmo de inteligencia artificial, fabricación de la estructura, integración de hardware y software, calibración, pruebas experimentales y validación final. Las fechas específicas deberán establecerse mediante el plan de trabajo del proyecto. La planificación y evaluación progresiva permitirán controlar el desarrollo y realizar ajustes antes de la validación final. **Fuente:** ISO 9001:2015. | A.D., K.C. |

---

# Bibliografía

## Lista de Requerimientos

[1] National Highway Traffic Safety Administration (NHTSA). “Drowsy Driving”, 2026.

[2] Centers for Disease Control and Prevention / National Institute for Occupational Safety and Health (CDC/NIOSH). “Driver Fatigue on the Job”, 2024.

[3] National Highway Traffic Safety Administration (NHTSA). “Advanced Impaired Driving Prevention Technology”, 2024.

[4] World Health Organization (WHO). “Global Status Report on Road Safety 2023”, 2023.

[5] Espressif Systems. “ESP32-WROOM-32 & ESP32-WROOM-32U Datasheet”, 2025.

[6] Google AI for Developers. “MediaPipe Face Landmarker”, 2026.

[7] OpenCV. “OpenCV Documentation”, 2025.

[8] International Organization for Standardization (ISO). “ISO 21448:2022 — Road vehicles — Safety of the intended functionality”, 2022.

[9] International Organization for Standardization (ISO). “ISO 12100:2010 — Safety of machinery — General principles for design — Risk assessment and risk reduction”, 2010.

[10] International Organization for Standardization (ISO). “ISO 9241-210:2019 — Ergonomics of human-system interaction — Human-centred design for interactive systems”, 2019.

[11] International Organization for Standardization (ISO). “ISO 9241-115:2024 — Ergonomics of human-system interaction — Guidance on conceptual design, user-system interaction design, user interface design and navigation design”, 2024.

[12] International Organization for Standardization (ISO). “ISO 9001:2015 — Quality management systems — Requirements”, 2015.

[13] Dahiya, A., et al. “Technologies for detecting and monitoring drivers' states: A systematic review”, Heliyon, 2024.