# GREENPLANT — TRL 2

## Formulación conceptual de la propuesta tecnológica

La propuesta define la integración de sensores de bajo costo para el monitoreo experimental de gases y variables ambientales durante ensayos con plantas de papa. Este informe presenta el sustento científico, el análisis preliminar de protección y el perfil del proyecto correspondiente al TRL 2.

## Datos del informe

| Campo | Información |
|:---|:---|
| **Curso** | Proyecto Integrador |
| **Integrantes** | Cesar Rodrigo Milla Gómez; Anderson Josue Delerna Infantes; Kevin Esty Carvallo Neciosup; Shedira Lumeris Sihuincha Palacin |
| **Ingenieros** | Umbert Lewis De La Cruz, Maria Rejas, Harry Rivera y Renzo Chan |
| **Fecha** | 27/10/2026 |
| **Institución** | Universidad Peruana Cayetano Heredia |
| **Tema** | TRL 2 de GREENPLANT — Formulación conceptual de la propuesta tecnológica |

**Definición del TRL 2**

Este nivel se caracteriza por el desarrollo de investigación aplicada, explorando las aplicaciones prácticas de la propuesta tecnológica, siendo las posibles aplicaciones aún especulativas. Se sustentan en el análisis del estado del arte acotado al concepto de aplicación tecnológico. En este nivel los aspectos de propiedad intelectual adquieren importancia y continúan en adelante. Se desarrolla en un entorno de laboratorio.

GREENPLANT propone un sistema de monitoreo experimental de amoníaco (NH₃), dióxido de carbono (CO₂), condiciones ambientales y humedad del sustrato durante ensayos con plantas de papa (Solanum tuberosum) fertilizadas con urea. A partir de los principios científicos revisados en el TRL 1, esta etapa define la aplicación prevista, los componentes del sistema y su integración conceptual en un entorno de laboratorio.

La propuesta contempla sensores de bajo costo conectados a un microcontrolador ESP32, encargado de adquirir, procesar y transmitir los registros. En concordancia con el TRL 2, se explora su aplicación práctica en laboratorio y se establece el fundamento de la arquitectura, sus necesidades de calibración y las alternativas de protección intelectual. Las posibles aplicaciones de apoyo a la decisión agronómica siguen siendo especulativas: no se considera demostrada la exactitud del conjunto ni su capacidad para generar recomendaciones de fertilización.

## 1 Artículos científicos que respalden o tengan relación directa con la propuesta tecnológica

### 1.1 Medición de amoníaco mediante el sensor MQ 137

Petric et al. \[1\] desarrollaron un dispositivo de monitoreo de amoníaco basado en un sensor MQ-137 conectado a una plataforma compatible con Arduino. Los autores compararon sus mediciones con las de un analizador profesional y evaluaron la calibración y repetibilidad del dispositivo en condiciones controladas. Este antecedente respalda la posibilidad de utilizar el MQ-137 en sistemas experimentales, siempre que su respuesta eléctrica se contraste con una referencia.

En GREENPLANT se propone adquirir la señal del circuito de lectura del MQ-137 y estudiar su relación con la concentración de NH₃. Las curvas de la hoja técnica servirán como orientación inicial; la conversión a partes por millón requerirá una calibración apropiada para los sensores y las condiciones del ensayo. El procesamiento en el ESP32 permitirá aplicar las relaciones obtenidas, pero no sustituirá la validación de las mediciones \[1\].

### 1.2 Monitoreo de dióxido de carbono mediante sensores NDIR

Dubey et al. \[2\] evaluaron sensores de CO₂ de bajo costo basados en absorción infrarroja no dispersiva —NDIR, por sus siglas en inglés— mediante comparación con un instrumento de referencia. Su trabajo destaca la importancia de caracterizar el desempeño de cada sensor y evaluar métodos de calibración antes de interpretar sus registros.

Este estudio sustenta el enfoque de evaluación previsto para GREENPLANT, aunque no constituye una validación específica del MH-Z19B. Para este modelo, el fabricante documenta el principio NDIR, la comunicación UART y las condiciones de funcionamiento sin condensación \[3\]. Su selección se plantea como una alternativa para registrar variaciones de CO₂ dentro de la cámara experimental, cuyo desempeño deberá verificarse en las condiciones reales de uso \[2\], \[3\].

### 1.3 Calibración de sensores capacitivos de humedad del suelo

Placidi et al. \[4\] estudiaron sensores de bajo costo para el monitoreo del suelo y del ambiente en una arquitectura de agricultura de precisión. El trabajo muestra que la sensibilidad de la sonda de contenido de agua no es constante, por lo que resulta necesario caracterizar la relación entre la señal de salida y la humedad del medio.

Para GREENPLANT se propone calibrar la sonda capacitiva v1.2 utilizando el sustrato seleccionado para los ensayos. Se contrastará su señal con una referencia gravimétrica obtenida a partir de las masas húmeda y seca de muestras representativas. Si se requiere expresar el contenido volumétrico de agua, también deberá determinarse la densidad aparente del sustrato. De este modo, se evitará interpretar la tensión de salida como un porcentaje universal de humedad \[4\].

### 1.4 Influencia de la temperatura y la humedad en las mediciones de gases

Huerta et al. \[5\] estudiaron un método para reducir la influencia de las variaciones de temperatura y humedad sobre señales de sensores químicos de óxido metálico. Su investigación respalda el registro simultáneo de variables ambientales como información necesaria para desarrollar y evaluar modelos de corrección.

En GREENPLANT, el BME280 se utilizará para registrar temperatura, humedad relativa y presión del aire \[6\]. Estas variables permitirán contextualizar las lecturas de gases y explorar posibles relaciones entre el ambiente y la respuesta de los sensores. Sin embargo, incorporar el BME280 no garantiza corregir automáticamente la deriva del MQ-137 ni eliminar interferencias de otros gases. Cualquier compensación deberá obtenerse y validarse mediante ensayos específicos \[5\], \[6\].

## 2 Análisis de patentabilidad y protección

### 2.1 Revisión del estado de la técnica

Los antecedentes revisados muestran que la medición de amoníaco mediante sensores de bajo costo, la integración de sensores ambientales y el procesamiento de señales son soluciones conocidas \[1\], \[4\], \[5\]. Por ello, su incorporación en GREENPLANT no permite afirmar, por sí sola, que la propuesta sea nueva o patentable.

Como antecedente documental se identificó la patente estadounidense US7341694B2, titulada “Ammonia sensor” \[7\], que describe una solución para detectar amoníaco y abordar la influencia de la temperatura sobre la medición. Su principio y aplicación difieren de la integración propuesta para GREENPLANT; aun así, evidencia que la mejora de la selectividad y la respuesta térmica forman parte del estado de la técnica. Este antecedente no demuestra una interferencia específica del CO₂ sobre el MQ-137 ni determina la patentabilidad de la cámara propuesta.

El posible aporte de GREENPLANT se explorará en la configuración de la cámara, la distribución del aire y la ubicación de los sensores. Se plantea estudiar si una disposición determinada reduce la influencia del calentador del MQ-137 sobre los demás componentes y mejora la representatividad de los registros. Estas ventajas constituyen hipótesis de diseño pendientes de comprobación.

En consecuencia, la revisión realizada es preliminar. Antes de solicitar protección, será necesario ampliar la búsqueda de antecedentes y comparar las características del diseño con las reivindicaciones de documentos pertinentes. En el TRL 2 no se declara demostrada la novedad ni el nivel inventivo de GREENPLANT.

### 2.2 Mecanismos de protección considerados

#### Modelo de utilidad

Se evaluará la posibilidad de proteger una configuración física de la cámara o de sus componentes si presenta una nueva disposición que aporte una ventaja técnica. Esta alternativa podría comprender la ubicación de sensores, los soportes o los elementos de distribución del aire, siempre que sus características cumplan los requisitos aplicables. INDECOPI señala que los modelos de utilidad protegen nuevas formas o configuraciones de elementos de un producto que le otorguen una ventaja técnica \[8\]. Por tanto, la solicitud dependerá del diseño finalmente desarrollado y del análisis de antecedentes.

#### Derecho de autor sobre el software

Se considerará el registro del programa desarrollado para el ESP32, correspondiente a las rutinas originales de adquisición, organización y transmisión de datos. INDECOPI dispone de un procedimiento de registro para programas de ordenador \[9\]. La documentación del proyecto deberá identificar a sus autores y distinguir el código propio de las bibliotecas de terceros utilizadas.

#### Secreto empresarial

Se evaluará esta alternativa para información técnica no divulgada que pueda obtenerse durante el desarrollo, como parámetros de calibración o procedimientos específicos. Su protección como secreto empresarial dependerá de que la información sea secreta, tenga valor comercial por esa condición y esté sujeta a medidas razonables de confidencialidad \[10\]. En esta etapa no se afirma que GREENPLANT disponga de coeficientes o curvas experimentales propios ya obtenidos.

## 3 Perfil o propuesta de proyecto

### 3.1 Título del proyecto

GREENPLANT: sistema experimental de monitoreo de NH₃(g), CO₂(g) y variables ambientales para estudiar el manejo de la urea en el cultivo de papa.

### 3.2 Problema y justificación

GREENPLANT parte de la necesidad de estudiar el comportamiento de los gases y las condiciones del sistema suelo-planta durante la fertilización con urea. El documento base del proyecto identifica como problema el riesgo de aplicar fertilizantes nitrogenados sin suficiente correspondencia con las necesidades del cultivo y las condiciones del suelo, lo que puede favorecer aplicaciones excesivas y pérdidas de nitrógeno \[11\].

La propuesta busca disponer de registros experimentales comparables de NH₃(g) y CO₂(g), acompañados de temperatura y humedad del aire y humedad del sustrato. Esta información permitirá explorar cómo varían las concentraciones bajo distintas dosis y formas de aplicación de urea. Su interpretación deberá considerar las condiciones de la cámara, la calibración de los sensores y el tiempo transcurrido desde la fertilización.

El propósito agronómico es aportar evidencia para una orientación preliminar sobre el uso de la urea, integrada con análisis de suelo, requerimientos de la papa y evaluación del cultivo. La contribución tecnológica consiste en formular una plataforma que reúna la adquisición, transmisión, almacenamiento y visualización de esas variables. En el TRL 2 se plantea esta aplicación y se fundamenta su diseño; su utilidad agronómica y su desempeño instrumental permanecen pendientes de comprobación.

### 3.3 Pregunta de investigación e hipótesis

Pregunta de investigación: ¿Cómo se relacionan las dosis y las formas de aplicación de urea, junto con las condiciones ambientales y del sustrato, con las concentraciones de NH₃(g) y CO₂(g) registradas en ensayos controlados con plantas de papa, y cómo podrían contribuir esos resultados, junto con información agronómica, a orientar un uso más eficiente del fertilizante? \[11\].

Hipótesis de trabajo: las dosis y las formas de aplicación de urea, junto con las condiciones ambientales y del sustrato, se relacionan con variaciones en las concentraciones de NH₃(g) y CO₂(g) registradas durante los ensayos con plantas de papa. Esta hipótesis deberá contrastarse experimentalmente; no implica que una lectura de gas permita determinar por sí sola la dosis adecuada de fertilizante.

### 3.4 Objetivos del proyecto y alcance del TRL 2

Objetivo general del proyecto: desarrollar un prototipo experimental que permita monitorear y registrar NH₃(g), CO₂(g) y variables ambientales y del sustrato, para analizar su comportamiento en ensayos controlados con plantas de papa bajo distintas condiciones de fertilización y aportar evidencia para orientar un uso más eficiente de la urea \[11\].

Objetivos específicos del proyecto:

- Recopilar antecedentes sobre el cultivo de papa en el Perú y sobre dosis y prácticas de fertilización con urea, considerando su contexto agronómico.

- Describir las transformaciones de la urea relacionadas con el NH₃(g) y los procesos que intervienen en las variaciones de CO₂(g) del sistema suelo-planta.

- Diseñar e implementar, en etapas posteriores, un prototipo con ESP32 y sensores para registrar gases, condiciones del aire y humedad del sustrato.

- Organizar, graficar y analizar los registros para comparar las condiciones experimentales evaluadas.

- Elaborar una orientación preliminar de manejo de la urea sustentada en los ensayos y en referencias agronómicas, sin proponer dosis universales ni sustituir el análisis de suelo y la validación en campo.

Objetivo específico de esta etapa TRL 2: formular el concepto de aplicación tecnológica, definir la arquitectura y las funciones de sus componentes, establecer un plan preliminar de evaluación e identificar posibles mecanismos de protección. El objetivo de desarrollar el prototipo corresponde al proyecto completo; su implementación y validación no se presentan como resultados ya alcanzados en esta etapa.

### 3.5 Solución y arquitectura tecnológica propuesta

Se propone una plataforma de laboratorio compuesta por una cámara experimental para ensayos con plantas de papa, sensores de gases y variables ambientales, un ESP32 y una aplicación de almacenamiento y visualización. La cámara deberá permitir documentar su volumen, la ubicación de los sensores y las condiciones de circulación o renovación de aire. Su configuración final se definirá de acuerdo con el propósito de medición; no se considerará caracterizada como cámara dinámica únicamente por incorporar un ventilador.

La arquitectura contempla los siguientes componentes:

- MQ-137: sensor para estudiar la respuesta al NH₃(g). Su circuito de lectura entregará una señal analógica que deberá calibrarse antes de interpretarse como concentración \[1\].

- MH-Z19B: sensor NDIR para registrar CO₂(g), con comunicación UART y funcionamiento dentro de las condiciones establecidas por el fabricante \[3\].

- BME280: sensor digital para registrar temperatura, humedad relativa y presión del aire mediante I²C \[6\].

- Sonda capacitiva v1.2: sensor analógico para estimar la humedad del sustrato mediante una calibración específica \[4\].

- ESP32: microcontrolador encargado de adquirir las señales, organizar los registros y transmitirlos mediante su conectividad Wi-Fi \[12\].

Se verificarán las tensiones de alimentación y los niveles de señal de todos los componentes. Las salidas analógicas del MQ-137 y de la sonda capacitiva deberán acondicionarse cuando sea necesario para respetar los límites de entrada del ESP32. El BME280 medirá condiciones del aire; no se le atribuirá medición de temperatura del suelo. Si el ensayo requiere esta última variable, deberá incorporarse una sonda específica.

El firmware organizará las lecturas con fecha, hora e identificación del ensayo. Se propone transmitirlas como mensajes JSON mediante MQTT, utilizando el modelo de publicación y suscripción: el ESP32 publicará los datos en un bróker y una aplicación suscriptora los recibirá para almacenarlos y visualizarlos \[13\]. Se conservarán las señales originales y se distinguirán de los valores convertidos o filtrados. Cualquier compensación ambiental deberá sustentarse en una evaluación experimental propia.

### 3.6 Plan preliminar de ensayos y análisis

Se plantea comparar tratamientos con distintas dosis y, cuando el diseño lo permita, distintas formas de aplicación de urea, incluyendo un control sin aplicación de urea. Las dosis concretas, el número de repeticiones y la duración de los ensayos se definirán antes de la implementación, con base en el análisis del sustrato, la variedad y etapa de desarrollo de la papa, las referencias agronómicas y los recursos disponibles. No se trasladarán directamente dosis por hectárea a macetas sin justificar su equivalencia.

El plan considerará las siguientes actividades:

- Caracterización del sistema de medición: verificar alimentación, comunicación, estabilidad, repetibilidad y respuesta de los sensores; comparar los registros de gases con concentraciones conocidas o instrumentos de referencia y calibrar la humedad del sustrato mediante un método gravimétrico.

- Preparación y trazabilidad de los ensayos: registrar tratamiento, cantidad de urea aplicada, forma y momento de aplicación, características del sustrato, estado inicial de las plantas, riego y condiciones de iluminación y ventilación.

- Adquisición de datos: obtener una línea de base antes de la aplicación y registrar las variables durante un periodo definido, manteniendo criterios de medición comparables entre tratamientos.

- Evaluación del cultivo: incorporar, si se analizará la respuesta de las plantas, indicadores directos como altura, número o área de hojas y biomasa. El rendimiento se evaluará únicamente si el alcance y la duración del ensayo lo permiten.

- Análisis comparativo: elaborar series temporales y comparar los tratamientos, documentando variabilidad, datos faltantes, posibles interferencias y limitaciones de los sensores. Las asociaciones entre variables se interpretarán sin asumir causalidad por correlación.

La temperatura y humedad del aire se registrarán con el BME280 y la humedad del sustrato con la sonda capacitiva. El pH y las propiedades químicas del suelo, cuando sean necesarios para interpretar los resultados, se obtendrán mediante análisis o instrumentos adicionales; los sensores propuestos no proporcionan esas mediciones.

### 3.7 Aplicación prevista y resultados esperados

La aplicación inicial será el monitoreo y la comparación de condiciones de fertilización en un entorno académico de laboratorio. Los registros se utilizarán para estudiar patrones de concentración y formular preguntas o recomendaciones preliminares de manejo que posteriormente deban contrastarse con evidencia agronómica. La posible utilidad para productores de papa se considera una proyección del proyecto y requerirá validación adicional.

Como resultados del proyecto completo se esperan un prototipo documentado, un procedimiento de calibración y operación, una base de registros experimentales, gráficas comparativas y un informe de interpretación. La orientación sobre urea deberá integrar los resultados de gases con los análisis de suelo, los requerimientos del cultivo y los indicadores de crecimiento disponibles \[11\].

El resultado específico del TRL 2 será el perfil tecnológico, acompañado de la arquitectura conceptual, la selección justificada de componentes, el plan preliminar de ensayos y el análisis de protección intelectual. No se reportan en esta etapa curvas de calibración propias, porcentajes de reducción de pérdidas ni mejoras de rendimiento ya demostradas.

### 3.8 Alcance y limitaciones de interpretación

El alcance inicial se limita a ensayos controlados con plantas de papa. Las concentraciones de NH₃(g) y CO₂(g) en ppm no equivalen directamente a flujos de emisión por unidad de superficie ni permiten calcular, por sí solas, el porcentaje de nitrógeno aplicado que se volatilizó. Para estimar esas magnitudes se requerirá un método de cuantificación que considere la configuración y el volumen de la cámara, la renovación de aire, el tiempo de medición y la cantidad de nitrógeno aplicada \[11\].

El NH₃(g) se abordará como una forma de nitrógeno reactivo asociada al problema de volatilización; no se presentará como un gas de efecto invernadero directo equivalente al CO₂(g). Tampoco se atribuirán automáticamente las variaciones de CO₂(g) a la urea, pues su interpretación debe considerar la respiración del sistema suelo-planta, la fotosíntesis y el intercambio de aire \[11\].

Una menor concentración registrada no demostrará por sí sola una reducción de pérdidas de nitrógeno ni un crecimiento óptimo. La ventilación, las propiedades del sustrato y el desempeño del instrumento pueden influir en el registro. Por ello, cualquier orientación de fertilización se limitará a las condiciones estudiadas y requerirá revisión agronómica antes de su aplicación fuera del laboratorio.

## Referencias bibliográficas

\[1\] M. Petric, F. Dodigović, I. Grčić, P. Markužić, L. Radetić y M. Topić, “Ammonia concentration monitoring using Arduino platform,” Environmental Engineering – Inženjerstvo okoliša, vol. 6, n.º 1, pp. 21–26, 2019, doi: 10.37023/ee.6.1.4. Disponible: https://doi.org/10.37023/ee.6.1.4

\[2\] R. Dubey et al., “Low-cost CO₂ NDIR sensors: Performance evaluation and calibration using machine learning techniques,” Sensors, vol. 24, n.º 17, art. 5675, 2024, doi: 10.3390/s24175675. Disponible: https://doi.org/10.3390/s24175675

\[3\] Zhengzhou Winsen Electronics Technology Co., Ltd., “Infrared CO₂ sensor module (model: MH-Z19B): User’s manual,” ver. 1.7, oct. 2020. \[En línea\]. Disponible: https://www.winsen-sensor.com/d/files/manual/mh-z19b.pdf. \[Consulta: 27-oct-2026\].

\[4\] P. Placidi, R. Morbidelli, D. Fortunati, N. Papini, F. Gobbi y A. Scorzoni, “Monitoring soil and ambient parameters in the IoT precision agriculture scenario: An original modeling approach dedicated to low-cost soil water content sensors,” Sensors, vol. 21, n.º 15, art. 5110, 2021, doi: 10.3390/s21155110. Disponible: https://doi.org/10.3390/s21155110

\[5\] R. Huerta, T. S. Mosqueiro, J. Fonollosa, N. F. Rulkov e I. Rodriguez-Lujan, “Online decorrelation of humidity and temperature in chemical sensors for continuous monitoring,” Chemometrics and Intelligent Laboratory Systems, vol. 157, pp. 169–176, 2016, doi: 10.1016/j.chemolab.2016.07.004. Disponible: https://doi.org/10.1016/j.chemolab.2016.07.004

\[6\] Bosch Sensortec, “BME280: Data sheet,” rev. 1.24, feb. 2024. \[En línea\]. Disponible: https://www.bosch-sensortec.com/media/boschsensortec/downloads/datasheets/bst-bme280-ds002.pdf. \[Consulta: 27-oct-2026\].

\[7\] H. Nishiyama et al., “Ammonia sensor,” patente estadounidense US7341694B2, 11-mar-2008. \[En línea\]. Disponible: https://patents.google.com/patent/US7341694B2/en.

\[8\] INDECOPI, “Formulario de solicitud de registro de modelo de utilidad.” \[En línea\]. Disponible: https://www.gob.pe/institucion/indecopi/informes-publicaciones/1272433-formulario-de-solicitud-de-registro-de-modelo-de-utilidad. \[Consulta: 27-oct-2026\].

\[9\] INDECOPI, “El Indecopi habilita servicio para que creadores de software registren sus programas a través de la plataforma de Registro Virtual de Obras,” 2024. \[En línea\]. Disponible: https://www.gob.pe/institucion/indecopi/noticias/906591-el-indecopi-habilita-servicio-para-que-creadores-de-software-registren-sus-programas-a-traves-de-la-plataforma-de-registro-virtual-de-obras. \[Consulta: 27-oct-2026\].

\[10\] INDECOPI, Módulo instruccional: Derecho de la propiedad intelectual, 2019. \[En línea\]. Disponible: https://escuela.indecopi.gob.pe/images/publicaciones/pdf/2019/Mdulo_Instruccional_Derecho_de_la_Propiedad_Intelectual_PUBLICADO.pdf. \[Consulta: 27-oct-2026\].

\[11\] Equipo GREENPLANT, “GREENPLANT — Proyecto integrador: monitoreo experimental de NH₃(g) y CO₂(g) en cultivo de papa,” documento de trabajo del proyecto, s. f., pp. 1–10. Archivo proporcionado: greenplant el real.pdf.

\[12\] Espressif Systems, “ESP32 series datasheet,” ver. 5.3. \[En línea\]. Disponible: https://documentation.espressif.com/esp32_datasheet_en.html. \[Consulta: 27-oct-2026\].

\[13\] OASIS, MQTT Version 5.0, OASIS Standard, 7-mar-2019. \[En línea\]. Disponible: https://docs.oasis-open.org/mqtt/mqtt/v5.0/os/mqtt-v5.0-os.html. \[Consulta: 27-oct-2026\].
