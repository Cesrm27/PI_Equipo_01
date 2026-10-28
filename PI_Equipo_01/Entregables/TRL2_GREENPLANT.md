# GREENPLANT — TRL 2

## Formulación conceptual de la propuesta tecnológica

La propuesta define la integración de sensores de bajo costo para el monitoreo experimental de gases y variables ambientales durante ensayos con plantas de papa. 

## Datos del informe

| Campo | Información |
|:---|:---|
| **Curso** | Proyecto Integrador |
| **Integrantes** | Cesar Rodrigo Milla Gómez; Anderson Josue Delerna Infantes; Kevin Esty Carvallo Neciosup; Shedira Lumeris Sihuincha Palacin |
| **Ingenieros** | Umbert Lewis De La Cruz, Maria Rejas, Harry Rivera y Renzo Chan |
| **Fecha** | 27/10/2026 |
| **Institución** | Universidad Peruana Cayetano Heredia |
| **Tema** | TRL 2 de GREENPLANT — Formulación conceptual de la propuesta tecnológica |

## Definición del TRL 2 en GREENPLANT

El TRL 2 corresponde a la formulación del concepto tecnológico y de su aplicación a partir de principios científicos conocidos, según la escala de madurez tecnológica analizada por Mankins [1]. En GREENPLANT, esta etapa consiste en definir un sistema experimental que integre sensores de NH₃, CO₂, condiciones del aire y humedad del sustrato para estudiar tratamientos de fertilización con urea en plantas de papa (Solanum tuberosum).

La aplicación agrícola se sustenta en el estudio de Wan et al. [2], que relaciona la fertilización nitrogenada con la volatilización de NH₃ en cultivos de papa, y en el de Rochette et al. [3], que examina el efecto de la profundidad de incorporación de la urea sobre las pérdidas de amoníaco. Estos antecedentes fundamentan la comparación de dosis y formas de aplicación. El CO₂ se incorpora como variable complementaria del sistema suelo-planta, considerando las distintas fuentes biológicas de CO₂ descritas por Kuzyakov [4].

La selección instrumental se apoya en antecedentes específicos: Petric et al. [5] utilizaron el MQ-137 para medir amoníaco con calibración frente a un analizador; Othman et al. [6] evaluaron el MH-Z19B en una cámara de calibración; y Placidi et al. [7] estudiaron la sonda capacitiva v1.2 para monitorear el contenido de agua del suelo. El registro ambiental se fundamenta en Huerta et al. [8], quienes analizaron la influencia de temperatura y humedad en sensores de óxido metálico. Como antecedente de integración, la tesis de Bezborodov [9] describe un equipo que combina ESP32, BME280 y MH-Z19B para monitorear aire en espacios interiores.

La arquitectura de adquisición, almacenamiento y visualización toma como antecedente el sistema agrícola con ESP32 de Berrios Gomez y Rivera Herrera [10]. GREENPLANT adapta este enfoque a ensayos de fertilización e incorpora el alojamiento de sensores ya contemplado en su diseño. Su configuración de medición se orienta por los criterios de trabajo con cámaras discutidos por Davidson et al. [11]. Así, el TRL 2 reúne una aplicación definida, componentes respaldados por investigaciones y una propuesta de integración orientada a la evaluación experimental.

## 1. Fundamento científico y antecedentes tecnológicos

### 1.1. Medición de amoníaco con el MQ-137

Petric et al. [5] desarrollaron un dispositivo con un sensor MQ-137 conectado a una placa Croduino Basic 2 y compararon sus registros con un analizador Geotech GA5000. El estudio empleó mediciones en un entorno controlado para calibrar el dispositivo y evaluar su repetibilidad.

Este antecedente sustenta la selección del MQ-137 para el monitoreo experimental de NH₃ en GREENPLANT. Se propone registrar su señal analógica y obtener una relación de calibración mediante concentraciones conocidas o un instrumento de referencia. La calibración se realizará en el intervalo de concentraciones previsto para los ensayos, siguiendo el criterio de contraste instrumental empleado en [5].

### 1.2. Medición de CO₂ mediante el MH-Z19B

Othman et al. [6] desarrollaron una cámara para evaluar sensores de calidad del aire y compararon el MH-Z19B con un monitor Onset HOBO MX1102. Su investigación incluye evaluación experimental y calibración por regresión. Este antecedente respalda directamente el uso del modelo seleccionado en un montaje de medición controlada.

Como complemento metodológico, Dubey et al. [12] evaluaron los sensores NDIR Sunrise, K30 y GMP343 frente a un instrumento de referencia. Este estudio aporta criterios de calibración para la tecnología NDIR; el antecedente específico del MH-Z19B es [6].

GREENPLANT propone utilizar el MH-Z19B para seguir la concentración de CO₂ y contrastar su respuesta con una referencia antes de comparar tratamientos [6]. Su comunicación UART y las condiciones de instalación se establecerán según el manual del fabricante [13].

### 1.3. Humedad del sustrato mediante una sonda capacitiva

Placidi et al. [7] estudiaron sensores de contenido de agua del suelo, incluida la sonda capacitiva v1.2, dentro de una arquitectura de monitoreo agrícola. Su trabajo relaciona la respuesta de sensores de bajo costo con el comportamiento hídrico del medio y con mediciones de referencia.

En GREENPLANT se propone calibrar la sonda utilizando el mismo sustrato de los ensayos. El procedimiento relacionará la señal eléctrica con el contenido de agua determinado mediante muestras húmedas y secas. La variable se expresará como contenido gravimétrico de agua; para obtener contenido volumétrico se incorporará la densidad aparente del sustrato. Esta propuesta de calibración adapta al sustrato del proyecto el enfoque de caracterización de sensores de humedad presentado en [7].

### 1.4. Registro simultáneo de temperatura y humedad del aire

Huerta et al. [8] desarrollaron un método para tratar la influencia de la temperatura y la humedad en las señales de sensores de óxido metálico, utilizando registros ambientales simultáneos. Este antecedente sustenta la incorporación de variables ambientales al análisis de los sensores de gases.

La tesis de Bezborodov [9] proporciona un antecedente de integración del BME280 con el ESP32 y el MH-Z19B. En GREENPLANT, el BME280 registrará temperatura, humedad relativa y presión del aire, conforme a las funciones documentadas por Bosch [14]. Estos datos acompañarán las lecturas de NH₃ y CO₂ y permitirán examinar su comportamiento bajo las condiciones ambientales de cada ensayo. El método de Huerta et al. [8] orienta el análisis de la influencia ambiental; sus coeficientes se ajustarían con los datos del sistema GREENPLANT.

### 1.5. Fertilización nitrogenada y volatilización de amoníaco en papa

Wan et al. [2] estudiaron el efecto de distintas dosis de nitrógeno y de un inhibidor de urea en campos de papa con riego por goteo. Encontraron picos de volatilización de NH₃ entre uno y cinco días después de la fertilización y una mayor volatilización acumulada al aumentar la dosis de nitrógeno en las condiciones evaluadas.

El estudio sustenta el seguimiento temporal del NH₃ después de fertilizar y la comparación de dosis [2]. Rochette et al. [3] observaron que la profundidad de incorporación de urea afectó la volatilización en el suelo estudiado, lo que fundamenta incluir la forma de aplicación como factor experimental. En GREENPLANT se propone establecer una línea de base previa a la aplicación y concentrar el seguimiento en los días posteriores, incluyendo un tratamiento sin urea como referencia experimental, en correspondencia con el control utilizado en [2].

### 1.6. Diseño de la cámara y condiciones de medición

Davidson et al. [11] analizaron fuentes de error en mediciones de respiración del suelo realizadas con cámaras. El trabajo muestra la importancia de controlar las condiciones de medición y las perturbaciones introducidas por la cámara.

Como criterio de diseño para GREENPLANT, se propone documentar el volumen de aire, la duración de las mediciones y el régimen de circulación o renovación utilizado. El alojamiento existente se integra a esta configuración. La exigencia de acceso del aire a los sensores se concreta con las indicaciones de instalación del MH-Z19B [13]. Como antecedente adicional de evaluación del montaje, Othman et al. [6] estudiaron la circulación del aire y la estabilidad ambiental de una cámara de calibración. Estos trabajos orientan los requisitos de GREENPLANT; la geometría del alojamiento corresponde al diseño del equipo.

### 1.7. ESP32, integración electrónica y gestión de registros

Berrios Gomez y Rivera Herrera [10] desarrollaron en Perú un sistema con ESP32 para monitorear variables ambientales y del suelo en un invernadero de lechugas. Los nodos enviaban información por ESP-NOW a un nodo central y los registros se almacenaban para su consulta. Este trabajo respalda la arquitectura general de adquisición y visualización agrícola; GREENPLANT propone MQTT para su propia comunicación.

La tesis de Bezborodov [9], presentada en 2025 en la Universidad Nacional V. N. Karazin de Járkiv, describe una integración concreta de ESP32, BME280 y MH-Z19B. Se utiliza como antecedente de compatibilidad e integración, según el resumen institucional del trabajo. Las interfaces y los límites eléctricos se especificarán con la documentación del ESP32 [15]; el esquema de publicación y suscripción se fundamenta en el estándar MQTT [16].

### 1.8. Función del CO₂ en la interpretación del sistema suelo-planta

Kuzyakov [4] distingue contribuciones al CO₂ del suelo procedentes de raíces, microorganismos y descomposición de materia orgánica. Este antecedente justifica registrar CO₂ como información complementaria y separar su interpretación del seguimiento de NH₃. En GREENPLANT se analizarán las variaciones de CO₂ junto con las condiciones de medición, manteniendo el NH₃ como variable gaseosa principal del estudio de fertilización [2], [4], [11].

## 2. Estado de la técnica y estrategia de protección

### 2.1. Antecedentes y aporte tecnológico de GREENPLANT

Los artículos [5], [6], [7], [8] y [10], junto con la tesis [9], documentan antecedentes de medición e integración pertinentes para los componentes seleccionados. GREENPLANT utiliza estos principios para formular una plataforma destinada a ensayos de fertilización con urea en plantas de papa.

La patente US7341694B2, «Ammonia sensor» [17], describe un sensor con una capa sensible basada predominantemente en ZrO₂ y que contiene tungsteno. Su objeto es el elemento de detección de amoníaco. GREENPLANT, en cambio, integra sensores comerciales y organiza su adquisición de datos para una aplicación experimental agrícola. Esta distinción delimita el objeto técnico de ambos desarrollos.

La propuesta combina el seguimiento de fertilización estudiado en [2], [3] con la adquisición electrónica descrita en [5], [6], [9], [10]. Su aporte de desarrollo es organizar las mediciones por tratamiento y tiempo de aplicación de la urea. El diseño aportado ya contempla un alojamiento destinado a los sensores. Este elemento se incorpora como parte de la arquitectura mecánica del equipo y como referencia para definir su montaje y acceso al aire de la cámara.

El criterio de integración es conservar la función de protección del alojamiento y permitir la exposición adecuada de los sensores al medio de medición. Para el MH-Z19B, el fabricante indica mantener libre el intercambio de aire en su ventana de difusión y alejar el módulo de fuentes de calor [13]. Estas indicaciones se adoptan como requisitos de montaje del alojamiento existente.

### 2.2. Mecanismos de protección considerados

#### Modelo de utilidad: configuración del alojamiento existente

El objeto de esta modalidad sería la configuración física del alojamiento ya previsto para los sensores y su integración con el equipo. El artículo [10] también describe el uso de una caja protectora para un nodo electrónico, por lo que la protección física se reconoce como una práctica de integración existente. INDECOPI señala que un modelo de utilidad protege una nueva forma o configuración de elementos que aporte una ventaja técnica [18]. Por ello, la justificación tendría que identificar una característica constructiva concreta y explicar qué mejora produce frente a otras configuraciones.

En la documentación actual, el alojamiento se presenta por su función de montaje y protección. Se mantiene como parte del diseño de GREENPLANT, sin convertir la existencia de una cubierta o un espacio para sensores en una justificación automática de modelo de utilidad. La modalidad queda vinculada a una diferencia constructiva y a una ventaja técnica identificables.

#### Derecho de autor sobre el software

La estrategia contempla documentar la autoría del código original desarrollado para adquirir, organizar, transmitir y visualizar los datos, conservando las versiones y distinguiendo las bibliotecas de terceros. INDECOPI dispone del registro de programas de ordenador mediante su plataforma de Registro Virtual de Obras [19].

#### Documentación técnica del proyecto

Los planos, esquemas eléctricos, archivos de diseño, procedimientos de calibración y versiones del programa se organizarán con identificación de autores y fechas. Esta documentación permitirá mantener la trazabilidad del desarrollo. El secreto empresarial no se prioriza como mecanismo del proyecto académico, cuya evaluación requiere presentar el diseño y sus procedimientos.

## 3. Perfil del proyecto

### 3.1. Título

GREENPLANT: sistema experimental de monitoreo de NH₃, CO₂ y variables ambientales en ensayos de fertilización con urea en plantas de papa.

### 3.2. Problema y justificación

La volatilización de amoníaco es una vía de pérdida de nitrógeno estudiada en la fertilización de papa [2]. La dosis y la colocación del fertilizante constituyen factores pertinentes para su análisis: Wan et al. evaluaron dosis en este cultivo [2], mientras que Rochette et al. investigaron la profundidad de incorporación de urea en suelo [3]. Estos resultados fundamentan el problema experimental que aborda GREENPLANT.

La necesidad instrumental es reunir mediciones de gases, ambiente y sustrato en registros comparables. Los antecedentes del MQ-137 [5], del MH-Z19B [6] y de sensores capacitivos de humedad [7] respaldan la selección de los dispositivos; la influencia ambiental sobre sensores de óxido metálico justifica acompañar el registro con temperatura y humedad del aire [8].

GREENPLANT propone organizar estas variables por tratamiento, unidad experimental y tiempo. El CO₂ se incorpora como variable complementaria por sus distintas fuentes biológicas [4]. La adquisición y consulta digital siguen un enfoque de monitoreo agrícola con antecedentes en sistemas basados en ESP32 [10].

### 3.3. Pregunta de investigación e hipótesis

Pregunta de investigación: ¿Cómo varían las concentraciones de NH₃ y CO₂ registradas en una cámara experimental con plantas de papa entre tratamientos con distintas dosis y formas de aplicación de urea, considerando las condiciones del aire y la humedad del sustrato?

Hipótesis de trabajo: los tratamientos de fertilización con urea producirán diferencias en la evolución temporal del NH₃ registrado en la cámara. Se formula a partir de los antecedentes sobre dosis y colocación del fertilizante [2], [3]. El CO₂ y las variables ambientales se analizarán como información complementaria [4], [8].

### 3.4. Objetivos

Objetivo general: desarrollar un sistema experimental para registrar NH₃, CO₂, condiciones del aire y humedad del sustrato, y comparar su comportamiento en ensayos con plantas de papa sometidas a distintos tratamientos de fertilización con urea.

Los objetivos siguientes traducen el fundamento agronómico [2], [3] y los antecedentes instrumentales [5], [6], [7], [10] en actividades propias del proyecto.

Objetivos específicos:

1. Sustentar la selección de sensores y el esquema de medición mediante antecedentes científicos y documentación técnica.
2. Integrar los sensores, el alojamiento previsto y el ESP32 en una arquitectura de adquisición y transmisión de datos.
3. Establecer procedimientos de calibración, verificación y registro para los componentes del sistema.
4. Obtener series temporales identificadas por tratamiento, repetición y momento de medición.
5. Comparar los registros e interpretarlos junto con las condiciones del sustrato y los indicadores de crecimiento del cultivo.

Objetivo del TRL 2: definir el concepto tecnológico, la arquitectura, la función de los componentes y el plan de evaluación del sistema, en correspondencia con la formulación de aplicación descrita por Mankins [1].

### 3.5. Arquitectura tecnológica

La plataforma propuesta reúne una cámara experimental, el alojamiento de sensores contemplado en el diseño, los dispositivos de medición, un ESP32 y una aplicación de registros. La arquitectura adapta antecedentes de medición en cámaras [6], [11] y de monitoreo agrícola conectado [10].

Componentes y funciones:

- MQ-137: adquisición de una señal analógica asociada a la respuesta al NH₃ y conversión mediante calibración [5].
- MH-Z19B: registro de CO₂, respaldado por su evaluación experimental en [6], con NDIR y UART según [13].
- BME280: registro ambiental; su integración con ESP32 tiene antecedente en [9], y sus funciones e interfaz I²C se documentan en [14].
- Sonda capacitiva v1.2: estimación del contenido de agua del sustrato a partir de una calibración específica [7].
- ESP32: lectura y transmisión de datos, con antecedente agrícola en [10] y especificaciones en [15].

El alojamiento representado en la imagen aportada se utilizará como base del montaje de los sensores de gases y del aire. La sonda de humedad se instalará en el sustrato. Como requisitos de integración, se propone mantener accesibles las zonas de detección [13] y organizar el cableado. La ubicación del BME280 fuera de la proximidad inmediata de fuentes de calor se adopta para reducir el riesgo de medir el calentamiento local del equipo: Bosch indica que su lectura térmica depende de la temperatura del circuito y del autocalentamiento [14]. La distribución se documentará mediante un plano rotulado, con identificación de sensores y puntos de comunicación con el aire de la cámara.

El circuito incluirá la alimentación correspondiente a cada módulo y el acondicionamiento de las señales analógicas de acuerdo con los límites de entrada del ESP32 [15]. El programa conservará la señal original y el valor calculado, junto con fecha, hora, tratamiento e identificación de la unidad experimental.

La transmisión se propone mediante mensajes JSON sobre MQTT. El ESP32 publicará los registros en un bróker y una aplicación suscriptora los almacenará y mostrará en gráficas [16]. Esta organización permitirá revisar las mediciones y relacionarlas con las operaciones de fertilización y riego.

### 3.6. Plan de evaluación y ensayos

El plan adapta la comparación de fertilización en papa de [2], el estudio de colocación de urea de [3] y los criterios instrumentales de [5], [6], [7], [11]. Se propone comparar tratamientos con un control sin urea, manteniendo una variedad de papa, una etapa de desarrollo y un sustrato comunes. La dosis se expresará por unidad experimental, indicando la cantidad de urea y de nitrógeno aplicada. El protocolo fijará las dosis, las formas de aplicación, el número de repeticiones y la duración antes de iniciar los ensayos.

La evaluación comprenderá cinco actividades:

1. Verificación instrumental. Comprobar alimentación, comunicaciones, estabilización y continuidad del registro. Contrastar los sensores de gases con referencias e identificar el intervalo útil de medición y la repetibilidad. Calibrar la sonda en el sustrato seleccionado [5], [6], [7].
2. Comprobación del montaje. Revisar el acceso del aire a los sensores, registrar la distribución de los componentes y comprobar el comportamiento de las lecturas con el equipo completo en funcionamiento. Documentar el volumen de la cámara y el régimen de circulación o renovación del aire [6], [11].
3. Preparación experimental. Identificar cada maceta como unidad experimental; registrar masa de sustrato, tratamiento, estado inicial de la planta, riego e iluminación. Distribuir aleatoriamente los tratamientos y mantener condiciones comparables de medición.
4. Seguimiento temporal. Obtener una línea de base antes de aplicar urea y registrar las variables durante un periodo común. Anotar fertilizaciones, riegos y aperturas de la cámara. Si una misma cámara se utiliza sucesivamente, establecer un procedimiento de renovación del aire entre mediciones.
5. Análisis. Comparar la evolución temporal y la variabilidad entre unidades experimentales. Las lecturas sucesivas de una misma maceta se tratarán como medidas repetidas. Se incorporarán altura, número de hojas y, al finalizar el ensayo, biomasa cuando el procedimiento lo permita.

El pH y las propiedades químicas del sustrato se obtendrán mediante análisis complementarios, considerando su relación con la interpretación de la volatilización discutida en [3]. Si se incorpora temperatura del suelo al análisis, se empleará una sonda específica para esa variable.

### 3.7. Aplicación y resultados esperados

La aplicación inicial de GREENPLANT será el seguimiento de ensayos de fertilización en un laboratorio académico. El sistema facilitará la consulta de los registros y la comparación de tratamientos en condiciones documentadas.

Los resultados del proyecto serán un prototipo con su documentación técnica, un procedimiento de calibración y operación, una base de datos identificada por unidad experimental, gráficas temporales y un informe comparativo. Las conclusiones sobre manejo de urea se formularán para las condiciones estudiadas e integrarán la información del sustrato y del cultivo.

El producto de esta etapa es la formulación del sistema y su aplicación [1]: fundamento científico, selección de componentes, arquitectura de integración, función del alojamiento y plan de evaluación. Los resultados esperados descritos corresponden a productos del proyecto.

### 3.8. Criterios de interpretación

Las variables principales se reportarán como concentraciones de gases dentro de la cámara. Para expresar pérdidas de nitrógeno o flujos de emisión se necesitaría un procedimiento adicional de cuantificación que considere volumen, intercambio de aire, tiempo y superficie de referencia. La metodología de medición con cámaras exige distinguir estas magnitudes [11].

El CO₂ se interpretará considerando el intercambio de aire [11] y las fuentes biológicas del suelo y las raíces [4]; su variación no se asignará exclusivamente a la urea. La comparación de tratamientos se apoyará en registros obtenidos dentro del intervalo calibrado y bajo condiciones equivalentes. Las recomendaciones agronómicas combinarán estos resultados con información del suelo y del cultivo.

## Referencias bibliográficas — formato IEEE

[1] J. C. Mankins, “Technology readiness assessments: A retrospective,” Acta Astronautica, vol. 65, n.os 9–10, pp. 1216–1223, 2009, doi: 10.1016/j.actaastro.2009.03.058. Disponible: https://doi.org/10.1016/j.actaastro.2009.03.058

[2] W.-f. Wan, F. Li, M. Hong, F. Chang y H.-y. Gao, “Effects of nitrogen rate and urease inhibitor on N₂O emission and NH₃ volatilization in drip irrigated potato fields,” Journal of Plant Nutrition and Fertilizers, vol. 24, n.º 3, pp. 693–702, 2018, doi: 10.11674/zwyf.17197. Disponible: https://doi.org/10.11674/zwyf.17197

[3] P. Rochette et al., “Ammonia volatilization and nitrogen retention: How deep to incorporate urea?,” Journal of Environmental Quality, vol. 42, n.º 6, pp. 1635–1642, 2013, doi: 10.2134/jeq2013.05.0192. Disponible: https://doi.org/10.2134/jeq2013.05.0192

[4] Y. Kuzyakov, “Sources of CO₂ efflux from soil and review of partitioning methods,” Soil Biology and Biochemistry, vol. 38, n.º 3, pp. 425–448, 2006, doi: 10.1016/j.soilbio.2005.08.020. Disponible: https://doi.org/10.1016/j.soilbio.2005.08.020

[5] M. Petric, F. Dodigović, I. Grčić, P. Markužić, L. Radetić y M. Topić, “Ammonia concentration monitoring using Arduino platform,” Environmental Engineering – Inženjerstvo okoliša, vol. 6, n.º 1, pp. 21–26, 2019, doi: 10.37023/ee.6.1.4. Disponible: https://doi.org/10.37023/ee.6.1.4

[6] H. Othman, G. Sieves, T. Guimarães y R. Azari, “A calibration chamber framework for low-cost indoor air quality sensor validation,” Building and Environment, vol. 287, art. 113856, ene. 2026, doi: 10.1016/j.buildenv.2025.113856. Disponible: https://doi.org/10.1016/j.buildenv.2025.113856

[7] P. Placidi, R. Morbidelli, D. Fortunati, N. Papini, F. Gobbi y A. Scorzoni, “Monitoring soil and ambient parameters in the IoT precision agriculture scenario: An original modeling approach dedicated to low-cost soil water content sensors,” Sensors, vol. 21, n.º 15, art. 5110, 2021, doi: 10.3390/s21155110. Disponible: https://doi.org/10.3390/s21155110

[8] R. Huerta, T. S. Mosqueiro, J. Fonollosa, N. F. Rulkov e I. Rodriguez-Lujan, “Online decorrelation of humidity and temperature in chemical sensors for continuous monitoring,” Chemometrics and Intelligent Laboratory Systems, vol. 157, pp. 169–176, 2016, doi: 10.1016/j.chemolab.2016.07.004. Disponible: https://doi.org/10.1016/j.chemolab.2016.07.004

[9] A. A. Bezborodov, “Розробка системи перевірки якості повітря на основі ESP32” [Desarrollo de un sistema de monitoreo de calidad del aire basado en ESP32], tesis de grado, especialidad de Ciencias de la Computación, Universidad Nacional V. N. Karazin de Járkiv, Járkiv, Ucrania, 2025. Consultado: 28-oct-2026. [En línea]. Disponible: https://ekhnuir.karazin.ua/handle/123456789/26414

[10] S. Berrios Gomez y H. J. Rivera Herrera, “Sistema IoT basado en ESP32 para el control y monitoreo de cultivos en invernadero con enfoque de agricultura 4.0,” Ingeniería Investiga, vol. 4, art. e624, 2022, doi: 10.47796/ing.v4i0.624. Disponible: https://doi.org/10.47796/ing.v4i0.624

[11] E. A. Davidson, K. Savage, L. V. Verchot y R. Navarro, “Minimizing artifacts and biases in chamber-based measurements of soil respiration,” Agricultural and Forest Meteorology, vol. 113, pp. 21–37, 2002, doi: 10.1016/S0168-1923(02)00100-4. Disponible: https://doi.org/10.1016/S0168-1923(02)00100-4

[12] R. Dubey et al., “Low-cost CO₂ NDIR sensors: Performance evaluation and calibration using machine learning techniques,” Sensors, vol. 24, n.º 17, art. 5675, 2024, doi: 10.3390/s24175675. Disponible: https://doi.org/10.3390/s24175675

[13] Zhengzhou Winsen Electronics Technology Co., Ltd., “Infrared CO₂ sensor module (model: MH-Z19B): User’s manual,” ver. 1.7, oct. 2020. Consultado: 28-oct-2026. [En línea]. Disponible: https://www.winsen-sensor.com/d/files/manual/mh-z19b.pdf

[14] Bosch Sensortec, “BME280: Data sheet,” rev. 1.24, feb. 2024. Consultado: 28-oct-2026. [En línea]. Disponible: https://www.bosch-sensortec.com/media/boschsensortec/downloads/datasheets/bst-bme280-ds002.pdf

[15] Espressif Systems, “ESP32 series datasheet,” ver. 5.3. Consultado: 28-oct-2026. [En línea]. Disponible: https://documentation.espressif.com/esp32_datasheet_en.html

[16] OASIS, MQTT Version 5.0, OASIS Standard, 7-mar-2019. Consultado: 28-oct-2026. [En línea]. Disponible: https://docs.oasis-open.org/mqtt/mqtt/v5.0/os/mqtt-v5.0-os.html

[17] H. Nishiyama et al., “Ammonia sensor,” patente de EE. UU. US7341694B2, 11-mar-2008. [En línea]. Disponible: https://patents.google.com/patent/US7341694B2/en

[18] INDECOPI, “Formulario de solicitud de registro de modelo de utilidad,” jun. 2026. Consultado: 28-oct-2026. [En línea]. Disponible: https://www.gob.pe/institucion/indecopi/informes-publicaciones/1272433-formulario-de-solicitud-de-registro-de-modelo-de-utilidad

[19] INDECOPI, “El Indecopi habilita servicio para que creadores de software registren sus programas a través de la plataforma de Registro Virtual de Obras,” 2024. Consultado: 28-oct-2026. [En línea]. Disponible: https://www.gob.pe/institucion/indecopi/noticias/906591-el-indecopi-habilita-servicio-para-que-creadores-de-software-registren-sus-programas-a-traves-de-la-plataforma-de-registro-virtual-de-obras
