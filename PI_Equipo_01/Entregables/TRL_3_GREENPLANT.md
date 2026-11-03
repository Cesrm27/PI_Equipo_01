# TRL 3 – Desarrollo y preparación de la prueba de concepto experimental de GREENPLANT

**Universidad Peruana Cayetano Heredia**  
**Ingeniería Informática e Industrial – Proyecto Integrador | 2026-II**  
**Proyecto:** GREENPLANT  
**Equipo:** Equipo 01  
**Repositorio:** https://github.com/Cesrm27/PI_Equipo_01  
**Fecha:** 2 de noviembre de 2026

> **Estado de este informe:** documento técnico de preparación y evaluación de TRL 3. Se utiliza numeración de referencias estilo Vancouver (`[1]`, `[2]`, etc.), con citas en los párrafos. Los procedimientos y criterios son propuestas para aplicar y documentar; **no constituyen resultados ya obtenidos**. Las configuraciones reales de la placa, cámara, energía, software y tratamientos deben cotejarse con el hardware y las evidencias del equipo.
>
> **Corrección de componentes confirmada por el equipo:** para NH₃ se utilizará **MQ-137** y para CO₂ **MH-Z19C**. No se utilizará el ME3-NH₃ ni el MH-Z19B. La selección de estos componentes es una decisión del equipo; las referencias [5] y [6] respaldan sus características técnicas.

## 1. Introducción

### 1.1. ¿Qué representa el TRL 3?

El nivel de madurez tecnológica 3 (*Technology Readiness Level 3*, TRL 3) se refiere a la demostración analítica y experimental de funciones o características críticas de un concepto tecnológico. En este nivel se realizan estudios, modelos o pruebas de laboratorio que permitan valorar su viabilidad, normalmente antes de validar una integración robusta y completa en un entorno operativo. Por ello, contar con componentes seleccionados o con un prototipo ensamblado no demuestra por sí solo que se haya alcanzado el TRL 3: se requieren observaciones y resultados documentados que corroboren las funciones críticas [1,2].

En GREENPLANT, la función crítica consiste en obtener señales útiles y trazables de gases y variables ambientales mediante sensores conectados a un ESP32, registrar su evolución temporal y estudiar su comportamiento en un experimento controlado con plantas de papa y fertilización con urea. La demostración analítica deberá relacionar la hipótesis de trabajo, la instrumentación, los protocolos y los criterios de evaluación con resultados verificables [1,2].

### 1.2. Problema que atiende GREENPLANT

La fertilización nitrogenada es importante para los cultivos, pero parte del nitrógeno aplicado mediante urea puede perderse por volatilización de amoníaco (NH₃). La magnitud de este proceso depende de las propiedades del suelo, humedad, temperatura y prácticas de aplicación, entre otras condiciones. Por ese motivo resulta relevante estudiar experimentalmente cómo evoluciona el NH₃ bajo tratamientos controlados y registrar variables que pueden ayudar a interpretar los cambios observados [3,4].

GREENPLANT busca observar concentraciones de NH₃ y CO₂ dentro de una cámara experimental asociada al cultivo de papa. Se debe diferenciar **concentración en la cámara** de **flujo o masa total volatilizada**: obtener una lectura de gas no basta para calcular directamente la cantidad total de nitrógeno perdida, porque la cuantificación de emisiones requiere un procedimiento de muestreo, condiciones de volumen y ventilación conocidas y una metodología apropiada [4].

### 1.3. Propuesta tecnológica

La propuesta integra sensores de gases y variables ambientales con una unidad de adquisición ESP32 y un sistema de registro de datos. El sensor MQ-137 responde al NH₃ mediante un elemento semiconductor; el MH-Z19C mide CO₂ mediante absorción infrarroja no dispersiva (NDIR); el BME280 permite medir temperatura y humedad ambiental; y un sensor de humedad de suelo v2.1 aporta información sobre el sustrato. Las características de funcionamiento del MQ-137, MH-Z19C, BME280 y ESP32 están descritas por sus fabricantes [5–7,9].

La visualización local mediante LCD, la transmisión de datos y su almacenamiento son partes previstas en la arquitectura del proyecto. Las interfaces y capacidades disponibles del ESP32 hacen técnicamente posible esta integración, pero la elección de plataforma, frecuencia de lectura, formato y desempeño deben demostrarse con la implementación real [9,10].

### 1.4. Alcance del documento

El propósito de este TRL 3 es formular y documentar la prueba de concepto que permita verificar la adquisición y el tratamiento de los datos, así como establecer las condiciones mínimas para realizar comparaciones entre ensayos. En correspondencia con la definición de TRL 3, el alcance se centra en resultados analíticos y experimentales de funciones críticas, no en declarar un producto agrícola ya validado [1,2].

Se diferencian cuatro tipos de información: **(a)** decisiones de diseño del equipo, **(b)** especificaciones de fabricantes, **(c)** fundamento científico de investigaciones publicadas y **(d)** resultados obtenidos por GREENPLANT. Solo el último grupo puede utilizarse para afirmar desempeño medido del prototipo.

## 2. Fundamento científico y tecnológico

### 2.1. Volatilización de NH₃ derivada de la urea

Después de la aplicación de urea al suelo, las transformaciones del nitrógeno pueden favorecer la liberación de NH₃ a la atmósfera. La bibliografía agronómica indica que el ambiente edáfico, la temperatura, la humedad y la forma de aplicación condicionan la volatilización; por tanto, las comparaciones deben considerar variables de contexto y evitar atribuciones causales basadas en una sola lectura [3].

En el ensayo propuesto, un cambio en la señal de NH₃ del MQ-137 sería una observación experimental que deberá contrastarse con controles y condiciones conocidas. Cuando se quiera estimar cuantitativamente emisión o pérdida de nitrógeno, se deberán utilizar métodos adecuados al tipo de cámara y a su intercambio de aire, pues las cámaras cerradas y los sistemas dinámicos presentan limitaciones y fuentes de incertidumbre diferentes [4].

### 2.2. CO₂ como variable complementaria

El CO₂ se propone como una variable de seguimiento del ambiente dentro de la cámara experimental. Su evolución puede estar influida por procesos biológicos del suelo y de la planta, además de aperturas, entradas de aire y condiciones de ventilación. Por ello, la lectura del MH-Z19C no debe interpretarse automáticamente como una medida de volatilización nitrogenada. Su utilidad en GREENPLANT será proporcionar una serie temporal complementaria a los registros de NH₃, temperatura y humedad [4,6].

### 2.3. Sensor de amoníaco MQ-137

El MQ-137 es un sensor semiconductor basado en dióxido de estaño (SnO₂). Su resistencia o conductividad varía ante la presencia de NH₃ y puede responder también a otras sustancias, incluidas determinadas aminas. Winsen publica un rango de detección nominal de **5 a 500 ppm** y especifica un calentador de **5 V**; además indica un precalentamiento prolongado bajo condiciones estándar, por lo que la preparación del sensor y la calibración deben documentarse cuidadosamente [5].

Una salida analógica del MQ-137 o de su módulo no es una concentración en ppm por sí misma. La transformación a concentración depende de las características del circuito, de la calibración y de las condiciones de prueba. Hasta disponer de referencias y una curva validada, GREENPLANT reportará la **lectura cruda o señal relativa** en lugar de presentar valores absolutos de NH₃ como comprobados [5].

### 2.4. Sensor de dióxido de carbono MH-Z19C

El MH-Z19C es un módulo NDIR diseñado para la medición de CO₂, con salidas UART y PWM, alimentación especificada de aproximadamente **5 V** y nivel de interfaz UART de **3,3 V**. El fabricante presenta distintas variantes de rango; por ello debe comprobarse el rango de la unidad adquirida antes de realizar pruebas y seleccionar los procedimientos de calibración pertinentes [6].

El sensor permite disponer de una lectura digital de CO₂, pero su aplicación en una cámara con humedad y cambios de concentración requiere respetar condiciones ambientales, tiempo de estabilización y prácticas de calibración recomendadas. Las mediciones fuera de rango o inestables deben identificarse en el registro de datos [6].

### 2.5. Sensores ambientales y humedad del suelo

El BME280 integra mediciones de temperatura, humedad relativa y presión barométrica, además de interfaces I²C y SPI. En GREENPLANT se prevé aprovechar la temperatura y la humedad relativa para describir las condiciones ambientales y apoyar la interpretación de las lecturas de gases. Su colocación debe minimizar influencias térmicas locales y exposición directa a fuentes de calor o condensación [7].

El sensor de humedad de suelo v2.1 incorporado por el equipo permitirá observar cambios relativos del sustrato. Su modelo exacto y fabricante deben confirmarse con el inventario; por ello no se le asignan especificaciones no verificadas. Estudios sobre sensores capacitivos de humedad muestran que la calibración específica del suelo puede mejorar considerablemente la calidad de las estimaciones, lo cual justifica ensayar el sensor con el sustrato real del proyecto [8].

### 2.6. ESP32, lectura analógica y comunicación

El ESP32 dispone de interfaces ADC, UART, I²C y capacidades Wi-Fi que permiten conectar dispositivos de adquisición y transmitir información. No obstante, el firmware debe ajustarse a las restricciones de sus pines, la configuración del convertidor analógico-digital y los niveles eléctricos de los sensores [9].

En particular, el ADC del ESP32 presenta variabilidad de referencia que puede influir en la conversión de valores crudos a voltaje. La documentación de Espressif recomienda procedimientos de calibración cuando se necesiten voltajes más confiables. Para el MQ-137 debe comprobarse que la tensión entregada por el módulo no supere lo admitido por la entrada seleccionada del ESP32 [10].

## 3. Objetivos e hipótesis de la prueba de concepto

### 3.1. Objetivo general

Desarrollar y documentar una prueba de concepto experimental de GREENPLANT mediante la integración de los sensores MQ-137, MH-Z19C, BME280 y humedad de suelo v2.1 con un ESP32, a fin de verificar la adquisición, trazabilidad, almacenamiento y análisis de datos de NH₃, CO₂ y condiciones ambientales en ensayos controlados de cultivo de papa con fertilización de urea, en concordancia con la evidencia requerida para TRL 3 [1,2].

### 3.2. Objetivos específicos

1. Definir la arquitectura funcional y eléctrica de los subsistemas del prototipo, verificando los requisitos técnicos de sus sensores e interfaces [5–7,9].
2. Preparar el montaje físico y la disposición de sensores en la cámara experimental, documentando sus características y condiciones de muestreo [4].
3. Comprobar individualmente las lecturas de gases y las variables ambientales, identificando incertidumbres y necesidades de calibración [5–8,10].
4. Verificar la adquisición de registros con fecha, identificación del ensayo, variable, valor, unidad y estado de lectura [9].
5. Diseñar los tratamientos experimentales con urea y sus controles para posibilitar comparaciones reproducibles [3,4].
6. Preparar un conjunto de datos para análisis descriptivo y, si existe información suficiente, para exploración mediante Machine Learning.
7. Contrastar los resultados con criterios definidos previamente y establecer el grado de cumplimiento de la prueba de concepto TRL 3 [1,2].

### 3.3. Hipótesis tecnológicas

**H1 (adquisición):** los sensores seleccionados podrán generar registros de variables de interés que el ESP32 capture de manera identificable y repetible bajo condiciones de ensayo establecidas. La factibilidad técnica de las interfaces proviene de las fichas de los fabricantes, pero su funcionamiento en GREENPLANT deberá verificarse experimentalmente [5–7,9].

**H2 (trazabilidad):** el sistema podrá asociar cada lectura con su variable, unidad, fecha/hora, identificación de tratamiento y estado de funcionamiento, permitiendo reconstruir las series temporales.

**H3 (comparación):** el registro conjunto de gases y condiciones del entorno permitirá observar diferencias entre tratamientos experimentales cuando se definan controles y se registren las condiciones que podrían afectar el resultado. Esta hipótesis no supone que toda diferencia observada sea consecuencia exclusiva de la fertilización [3,4].

**H4 (análisis de datos):** con suficientes datos válidos y un diseño experimental adecuado, será posible explorar asociaciones o patrones; la factibilidad de entrenar y validar un modelo de Machine Learning se decidirá después de revisar el dataset.

## 4. Arquitectura técnica propuesta

### 4.1. Visión general

La arquitectura de GREENPLANT sigue una cadena funcional: **cámara con cultivo de papa y sustrato → sensores → ESP32 → LCD y comunicación → repositorio de datos → dashboard → análisis estadístico/ML**. Esta estructura aprovecha las capacidades de entrada analógica, UART, buses digitales y conectividad del ESP32; su operación integrada requiere ensayos de interoperabilidad y no debe darse por validada antes de registrar evidencia [9,10].

### 4.2. Subsistemas

| Subsistema | Elemento principal | Función | Condición de validación |
|---|---|---|---|
| Sensado de amoníaco | MQ-137 | Respuesta asociada a NH₃ | Señal estable y calibración documentada [5] |
| Sensado de CO₂ | MH-Z19C | Medición NDIR de CO₂ | Lectura UART/PWM válida y revisión de rango [6] |
| Sensado ambiental | BME280 | Temperatura y humedad relativa | Comunicación y lectura coherentes [7] |
| Sensado de sustrato | Humedad de suelo v2.1 | Seguimiento de humedad relativa | Modelo confirmado y prueba de calibración [8] |
| Procesamiento | ESP32 | Adquisición y empaquetado | Firmware, pines y registros verificables [9,10] |
| Visualización local | LCD | Presentar valores y estados | Fotografías y pruebas de visualización |
| Comunicaciones | Wi-Fi/plataforma definida | Transferencia de mediciones | Comparación de datos enviados/recibidos |
| Experimento | Cámara y planta de papa | Contener y caracterizar condiciones | Dimensiones, ventilación y protocolo documentados [4] |
| Alimentación | Baterías y regulación | Proveer tensiones y corriente | Mediciones de consumo, estabilidad y protección |

### 4.3. Esquema de conexiones: aspectos a comprobar

La comunicación del MH-Z19C puede realizarse mediante UART, mientras que el BME280 emplea I²C o SPI según la versión de módulo utilizada. En contraste, el MQ-137 necesita un circuito de lectura y acondicionamiento de su respuesta eléctrica. El ESP32 puede implementar estas interfaces, siempre que el diseño respete los niveles de alimentación, tierra compartida cuando corresponda y los límites de entrada [5–7,9,10].

| Elemento | Interfaz prevista | Puntos de verificación |
|---|---|---|
| MQ-137 | Salida analógica del módulo a ADC | Calentador de 5 V, respuesta y tensión admisible en ADC [5,10] |
| MH-Z19C | UART | Alimentación a 5 V, RX/TX y niveles de interfaz [6] |
| BME280 | I²C | Voltaje del módulo, SDA/SCL, resistencias de pull-up [7] |
| Humedad suelo v2.1 | Analógica, por confirmar | Modelo, alimentación y calibración [8,10] |
| LCD | Según módulo adquirido | Alimentación, interfaz y dirección si usa I²C |
| ESP32 | Wi-Fi | Cobertura, manejo de desconexiones y registro [9] |

**Advertencia eléctrica:** la existencia de un pin de salida analógica en un módulo de MQ-137 no autoriza conectarlo sin medición previa a una entrada del ESP32. Deben comprobarse el voltaje máximo de la señal y, cuando corresponda, el uso de acondicionamiento o divisor resistivo [5,9,10].

### 4.4. Cámara experimental y ubicación de componentes

La cámara experimental se utilizará para observar variaciones de gases asociadas a las condiciones del ensayo. Deben documentarse sus dimensiones internas y volumen efectivo, posición de planta y sustrato, ubicación de sensores y condiciones de apertura o ventilación. La literatura sobre técnicas de medición de NH₃ señala que la geometría de la cámara y el intercambio de aire influyen en las mediciones, lo que hace imprescindible describir el sistema de muestreo [4].

La instalación debe mantener accesibles los sensores para inspección y reducir el riesgo de que el calor del MQ-137 afecte directamente otras lecturas o al cultivo. La cámara debe revisarse con relación a la condensación y a la exposición ambiental admitida por los módulos [5–7].

### 4.5. Alimentación y protección

La alimentación deberá cubrir el consumo de calentamiento del MQ-137, el funcionamiento del MH-Z19C, el ESP32 y los módulos auxiliares. Las fichas muestran que los sensores de gas tienen requisitos específicos de alimentación que deben verificarse antes de seleccionar la regulación eléctrica. El consumo y la autonomía no se pueden declarar sin medir las corrientes reales del montaje [5,6,9].

## 5. Desarrollo físico del prototipo: avance y evidencias

### 5.1. Diseño de la estructura

El equipo deberá presentar el diseño mecánico de la cámara mediante planos, medidas, fotografías o archivos CAD. Es importante justificar la forma de acceso a la planta, el espacio reservado al cableado y a los sensores, y el procedimiento de ventilación porque estas condiciones pueden afectar la repetibilidad de las concentraciones medidas [4].

**Registro de diseño por completar:**

| Evidencia | Información necesaria | Estado |
|---|---|---|
| Diseño CAD | Enlace, versión y fecha | [PENDIENTE] |
| Dimensiones internas | Alto, ancho, largo y volumen medido | [PENDIENTE] |
| Material de cámara | Tipo y método de fabricación | [PENDIENTE] |
| Ubicación del MQ-137 | Coordenadas/altura y fijación | [PENDIENTE] |
| Ubicación del MH-Z19C | Coordenadas/altura y fijación | [PENDIENTE] |
| Espacio para planta | Maceta, sustrato y acceso | [PENDIENTE] |
| Ventilación/aperturas | Descripción y frecuencia | [PENDIENTE] |

### 5.2. Fabricación y ensamblaje

El proceso de ensamblaje se documentará de forma cronológica: preparación de la cámara, montaje de sensores, fijación del ESP32, incorporación de pantalla y reguladores, revisión del cableado y comprobaciones eléctricas. En la evaluación TRL 3 estas evidencias describen el soporte físico de la prueba de concepto, pero las fotografías de montaje no reemplazan la demostración de funciones críticas [1,2].

**Bitácora sugerida:** fecha, componente, versión, responsable, tarea realizada, resultado, incidencia, corrección y evidencia visual o de medición.

### 5.3. Verificación mecánica y mantenimiento

Se revisará que el montaje pueda repetirse, que los sensores puedan retirarse para mantenimiento y que sus entradas de aire no queden obstruidas. Si se cambia la posición de un sensor, deberá documentarse porque la distribución de aire de una cámara puede introducir diferencias entre ensayos [4].

### 5.4. Figuras pendientes de incorporar

- Figura 1. Render o CAD general de GREENPLANT.
- Figura 2. Cámara experimental con medidas.
- Figura 3. Ubicación de sensores de gases y BME280.
- Figura 4. Vista del PCB, ESP32, LCD y alimentación.
- Figura 5. Fotografía del prototipo ensamblado.

Todas las imágenes deben provenir del desarrollo real y llevar fecha y versión del montaje.

## 6. Integración electrónica y software

### 6.1. Adquisición de datos

El firmware deberá iniciar sensores, verificar la disponibilidad de sus interfaces, leer las variables y reportar errores. Para el ADC del ESP32 se documentarán resolución, atenuación, canal y, cuando sea necesario, calibración de voltaje, siguiendo las recomendaciones de Espressif [9,10].

Los datos del MQ-137 deberán almacenar la señal cruda y el método de cálculo utilizado. Las lecturas expresadas en ppm se diferenciarán de las que solo representan una respuesta relativa; esta distinción es necesaria porque el sensor requiere un proceso de calibración y su respuesta puede depender de otras condiciones [5].

### 6.2. Estructura propuesta del registro

Cada medición conservará una etiqueta de ensayo y una marca temporal, lo que facilita reconstruir la secuencia de observación y comparar tratamientos. La propuesta de campos se presenta a continuación; es una decisión metodológica de GREENPLANT, no una especificación impuesta por el fabricante.

| Campo | Descripción | Ejemplo ilustrativo |
|---|---|---|
| `id_ensayo` | Identificador de sesión | `PAPA_T01_R01` |
| `fecha_hora` | Marca temporal con zona | `2026-11-02T10:00:00-05:00` |
| `tratamiento` | Control o condición de urea | `control` |
| `variable` | Parámetro medido | `co2` |
| `valor` | Dato numérico | `650` (solo ejemplo de formato) |
| `unidad` | ppm, °C, %HR, ADC, etc. | `ppm` |
| `origen_sensor` | Modelo y versión | `MH-Z19C` |
| `estado` | Válido, calentando, error | `valido` |
| `version_firmware` | Compilación del código | `v0.x` |

**Nota:** el ejemplo numérico es exclusivamente una demostración del formato del registro y **no es una lectura real del prototipo**.

### 6.3. Comunicación y almacenamiento

Se comprobará el envío de registros desde el ESP32 a la plataforma efectivamente seleccionada por el equipo, comparando los mensajes emitidos y almacenados. La capacidad de Wi-Fi del ESP32 justifica la arquitectura propuesta, pero latencia, pérdidas y estabilidad deben medirse en la implementación real [9].

### 6.4. Visualización y análisis

La pantalla LCD deberá mostrar variables, unidades y mensajes de estado. En la plataforma de análisis, las series de tiempo se visualizarán por sensor, ensayo y tratamiento. Para evitar interpretaciones erróneas, el sistema diferenciará mediciones válidas, valores faltantes, lectura fuera de rango y periodos de calentamiento de sensores [5,6].

## 7. Metodología de la prueba de concepto experimental

### 7.1. Enfoque metodológico

La prueba de concepto se ejecutará por etapas: **inspección física → revisión eléctrica → verificación individual de sensores → adquisición y transmisión → caracterización de cámara → ensayos controlados → análisis**. La secuencia responde al objetivo del TRL 3 de producir evidencia reproducible sobre funciones críticas, y evita dar por validado el sistema a partir del solo ensamblaje [1,2].

### 7.2. Protocolo P01 – Verificación física y eléctrica

**Objetivo:** comprobar que el montaje es seguro, accesible y compatible con los requisitos de los módulos. **Procedimiento:** inspeccionar cableado, polaridad, tensiones de alimentación, continuidad, fijaciones y accesibilidad. Registrar el voltaje de los módulos y la señal máxima que alcanza las entradas ADC. **Evidencia:** fotografías, esquema, mediciones de multímetro y lista de verificación. Los límites eléctricos deberán compararse con las especificaciones del MQ-137, MH-Z19C y ESP32 [5,6,9,10]. **Estado:** [PENDIENTE DE EVIDENCIA].

### 7.3. Protocolo P02 – Verificación individual del MQ-137

**Objetivo:** observar la respuesta cruda y la estabilidad de la señal asociada al NH₃. **Procedimiento:** montar el circuito conforme a la ficha aplicable, registrar el calentamiento, observar la señal en condiciones de referencia reproducibles y documentar las variaciones. No usar exposiciones improvisadas a amoníaco ni generar concentraciones desconocidas en espacios ocupados. Para obtener ppm deberá emplearse un procedimiento de calibración seguro y una referencia conocida. El MQ-137 requiere precalentamiento prolongado y su respuesta puede ser sensible a compuestos distintos del NH₃ [5]. **Evidencia:** registros ADC/voltaje, condiciones ambientales, bitácora y curva de respuesta si se dispone de referencia. **Estado:** [PENDIENTE].

### 7.4. Protocolo P03 – Verificación del MH-Z19C

**Objetivo:** comprobar la comunicación y coherencia de las lecturas de CO₂. **Procedimiento:** verificar alimentación, inicializar UART, comprobar mensajes válidos, respetar la estabilización indicada por el fabricante y contrastar con una referencia disponible según el rango exacto del módulo. Registrar errores de comunicación, periodos de calentamiento y posibles condiciones de saturación [6]. **Evidencia:** lecturas seriales, capturas y hoja de contraste. **Estado:** [PENDIENTE].

### 7.5. Protocolo P04 – Verificación del BME280 y humedad de suelo

**Objetivo:** comprobar lectura de temperatura, humedad ambiental y respuesta del sensor de sustrato. **Procedimiento:** contrastar el BME280 con una referencia apropiada y ubicar el sensor de humedad de suelo en muestras del sustrato real con niveles de agua documentados. El uso de calibración específica del suelo está respaldado por estudios de precisión en sensores económicos de humedad [7,8]. **Evidencia:** tabla de mediciones, repetición de pruebas y curva de calibración cuando corresponda. **Estado:** [PENDIENTE].

### 7.6. Protocolo P05 – Integridad del registro y transmisión

**Objetivo:** comprobar que cada lectura conserva la identificación y que los registros son recibidos íntegros. **Procedimiento:** emitir registros identificables durante un tiempo definido, contar mensajes transmitidos y almacenados, revisar duplicados y marcas temporales, e introducir una desconexión controlada si se implementa un mecanismo de recuperación. La conectividad Wi-Fi y recursos del ESP32 hacen viable el ensayo, cuyo desempeño deberá medirse [9]. **Evidencia:** logs de origen/destino, conteos, capturas del dashboard. **Estado:** [PENDIENTE].

### 7.7. Protocolo P06 – Caracterización de la cámara

**Objetivo:** identificar condiciones de operación relevantes para interpretar las concentraciones de gas. **Procedimiento:** medir volumen efectivo, registrar ventilación, tiempo de cierre, aperturas y posición de sensores; evaluar diferencias de lectura con y sin manipulación de la cámara. Los métodos de cámara pueden alterar o condicionar la medición de NH₃, por lo que su descripción y control son requisitos de una comparación sólida [4]. **Evidencia:** ficha de cámara, plano, fotografías y serie temporal de prueba. **Estado:** [PENDIENTE].

### 7.8. Protocolo P07 – Ensayo de fertilización con urea

**Objetivo:** recopilar series de NH₃, CO₂ y condiciones ambientales bajo tratamientos de fertilización en plantas de papa. **Diseño previsto:** incluir una condición control sin urea y al menos una condición con urea, con dosis y repeticiones definidas por el equipo y, de ser posible, revisadas con asesoría agronómica. Mantener o registrar tipo de sustrato, masa, humedad inicial, temperatura, volumen de cámara, riego, etapa de la planta y ventilación. La elección de estas variables responde a factores conocidos que influyen en la volatilización de NH₃ y a las limitaciones de medición en cámaras [3,4].

**Procedimiento:** (1) caracterizar y preparar las unidades experimentales; (2) registrar condiciones iniciales; (3) aplicar el tratamiento según protocolo; (4) obtener series temporales con frecuencia definida; (5) documentar riego, apertura de cámara e incidencias; (6) conservar datos originales; (7) comparar los tratamientos con métodos estadísticos apropiados. Una concentración medida dentro de la cámara no deberá presentarse como masa de nitrógeno emitida sin un método adicional que lo sustente [4]. **Estado:** [PENDIENTE].

### 7.9. Protocolo P08 – Análisis exploratorio y Machine Learning

**Objetivo:** evaluar si los datos experimentales permiten identificar patrones útiles. **Procedimiento:** revisar registros faltantes, sincronización temporal, valores extremos instrumentales, distribución por ensayo y repetición, y visualizar tendencias. Si se desarrolla un modelo, definir antes su objetivo y las etiquetas, separar el entrenamiento de la evaluación por ensayos o unidades experimentales para evitar fugas de información y documentar las métricas.

El análisis computacional es una etapa propuesta del proyecto; no se anticipan porcentajes de precisión, modelos seleccionados ni conclusiones sin dataset y pruebas. Para la evaluación TRL 3 resulta prioritario demostrar primero las funciones críticas de medición y registro [1,2]. **Estado:** [PENDIENTE].

### 7.10. Protocolo P09 – Consumo eléctrico y continuidad

**Objetivo:** medir el consumo en diferentes estados de operación y comprobar la estabilidad del sistema. **Procedimiento:** medir tensión y corriente del conjunto durante calentamiento, adquisición, transmisión y visualización; registrar reinicios y caídas de tensión. El calentador del MQ-137 y el consumo del MH-Z19C deben tenerse en cuenta en el balance energético, conforme a los datos de fabricante [5,6]. **Evidencia:** tabla de consumos y gráfica de tensión/corriente. **Estado:** [PENDIENTE].

## 8. Indicadores y criterios de aceptación

Los indicadores se definirán *antes* de la ejecución. Las fichas de fabricante pueden orientar tolerancias y rangos, pero la aceptación final debe considerar el objetivo de prueba y las condiciones reales del prototipo. Se evitará fijar valores de exactitud o autonomía sin mediciones que los respalden [5–7,9,10].

| Indicador | Cálculo o evidencia | Criterio a fijar |
|---|---|---|
| Lectura MQ-137 | Señal cruda, tiempo y condición de prueba | Estabilidad/repetibilidad [DEFINIR] |
| Lectura MH-Z19C | Respuesta UART y contraste | Rango/validez conforme a ficha [6] |
| Lectura BME280 | Contraste de T y HR | Tolerancia según referencia [7] |
| Humedad de suelo | Contraste por nivel del sustrato | Error/repetibilidad [DEFINIR] |
| Integridad de datos | Registros completos / registros emitidos | Umbral [DEFINIR] |
| Pérdida de registros | No recibidos / emitidos | Umbral [DEFINIR] |
| Continuidad de operación | Tiempo sin reinicios | Objetivo de prueba [DEFINIR] |
| Caracterización de cámara | Volumen y procedimiento registrados | Documentación completa [4] |
| Trazabilidad | Lecturas con ID, hora y unidad | Campos obligatorios completos |
| Repetibilidad del ensayo | Comparación de réplicas | Método y umbral [DEFINIR] |
| Capacidad analítica | Tablas y gráficas reproducibles | Dataset válido y documentado |

**Fórmulas sugeridas:** porcentaje de recepción = (registros recibidos válidos / registros emitidos) × 100; porcentaje de registros incompletos = (registros incompletos / registros almacenados) × 100. Las fórmulas describen indicadores de evaluación propuestos y no resultados del proyecto.

## 9. Estado de avance y trazabilidad de evidencias

Los estados que siguen se dejan abiertos porque este informe no dispone de pruebas, fotografías ni datasets certificados del montaje actual. El marco TRL 3 requiere evidencia de demostración analítica y experimental; por ello no sería correcto registrar como concluida una actividad sin su soporte documental [1,2].

| Actividad | Evidencia exigida | Estado |
|---|---|---|
| Definición del problema | Documento de formulación | [ACTUALIZAR] |
| Selección MQ-137/MH-Z19C | Inventario/fichas | Selección confirmada por el equipo |
| Selección BME280 y humedad v2.1 | Inventario/fichas | [CONFIRMAR MÓDULOS] |
| Diseño de cámara | CAD, planos y dimensiones | [ACTUALIZAR] |
| Fabricación | Fotografías/bitácora | [ACTUALIZAR] |
| Diseño PCB y conexiones | Esquemático y revisión eléctrica | [ACTUALIZAR] |
| Lectura de sensores | Logs y datos crudos | [PENDIENTE DE EVIDENCIA] |
| Caracterización/calibración | Curvas, referencias y condiciones | [PENDIENTE] |
| Almacenamiento/dashboard | Registros de extremo a extremo | [PENDIENTE] |
| Ensayos de urea | Plan, bitácora y dataset | [PENDIENTE] |
| Análisis estadístico/ML | Notebook, métricas y discusión | [PENDIENTE] |
| Evidencia de funciones críticas | Informe de pruebas reproducibles | [PENDIENTE] |

### 9.1. Formato de bitácora

`Fecha | Responsable | Versión hardware | Versión firmware | ID ensayo | Tratamiento | Condiciones | Actividad | Observaciones | Fallas | Archivo de evidencia`.

### 9.2. Control de versiones

Cada archivo de mediciones deberá asociarse a la configuración de la cámara, versión de firmware, sensor, tratamiento y fecha del ensayo. Esta trazabilidad permitirá distinguir cambios debidos a la instrumentación frente a cambios del tratamiento experimental.

## 10. Resultados experimentales [PENDIENTES DE INCORPORAR]

Este documento **no afirma** que se hayan completado pruebas de adquisición, calibración o ensayos de fertilización. La evidencia analítica y experimental será el elemento determinante para sostener el logro del TRL 3 [1,2].

### 10.1. Resultados de montaje

[PENDIENTE: fotografías, esquema, dimensiones reales de la cámara y verificación eléctrica].

### 10.2. Resultados de adquisición

[PENDIENTE: series temporales crudas de MQ-137, MH-Z19C, BME280 y sensor de humedad del suelo, con condición y unidad].

### 10.3. Resultados de calibración

[PENDIENTE: referencias utilizadas, lecturas, repeticiones, incertidumbre y curvas de calibración si se dispone de ellas]. En el MQ-137, no interpretar una curva no calibrada como concentración absoluta de NH₃ [5].

### 10.4. Resultados de comunicación

[PENDIENTE: logs, tasa de entrega, campos faltantes, latencia y evidencia del dashboard].

### 10.5. Resultados de ensayos con urea

[PENDIENTE: plan de tratamientos, replicación, datos crudos, gráficas y comparación]. La interpretación de emisiones deberá indicar las limitaciones de la cámara y del método de medición [4].

### 10.6. Análisis de datos y modelos

[PENDIENTE: procesamiento, figuras, métricas y discusión de patrones. Si no existe dataset suficiente, describir únicamente el análisis exploratorio].

## 11. Riesgos y limitaciones

El empleo de sensores económicos en un estudio experimental requiere considerar calentamiento, calibración, interferencias y resolución, además de las restricciones propias de una cámara de gases. Estas limitaciones están documentadas en las fichas de los fabricantes y en la bibliografía sobre métodos de cuantificación de NH₃ [4–8,10].

| Riesgo | Efecto potencial | Mitigación / fuente |
|---|---|---|
| MQ-137 sin calibración | Falsa precisión de NH₃ en ppm | Registrar señal relativa y calibrar [5] |
| Respuesta a otros gases | Interferencia en señal de NH₃ | Documentar condiciones y controles [5] |
| Calentamiento del MQ-137 | Mayor consumo y sesgo térmico | Respetar ficha y separar sensores [5] |
| CO₂ influido por respiración/ventilación | Atribuciones causales erróneas | Estandarizar condiciones de cámara [4,6] |
| Sensor de humedad sin calibración | Datos relativos mal interpretados | Calibrar por tipo de sustrato [8] |
| Entradas ADC fuera de rango | Daños o lecturas erróneas | Verificar tensión y acondicionar [9,10] |
| Ventilación/fugas no controladas | Series no comparables | Documentar cámara y eventos [4] |
| Registros incompletos | Pérdida de trazabilidad | ID, secuencia, estados y respaldo |
| Pocas réplicas | Comparaciones poco robustas | Planificar ensayos repetidos |
| Dataset limitado | Modelo ML no generalizable | Limitar alcance y validar por ensayo |
| Alimentación insuficiente | Reinicios del sistema | Medir consumo y estabilidad [5,6,9] |

## 12. Matriz de cumplimiento del TRL 3

La NASA y el Departamento de Energía describen el TRL 3 como una fase que requiere evidencia experimental y analítica de las funciones críticas. Por tanto, el nivel no debe declararse alcanzado simplemente por disponer de sensores, PCB, código o fotografías del montaje [1,2].

| Requisito | Evidencia mínima | Situación |
|---|---|---|
| Concepto tecnológico definido | Problema, objetivo y arquitectura | Definido documentalmente |
| Fundamentación científica | Bibliografía y relación con hipótesis | Incluida en este informe |
| Requisitos de instrumentación | Fichas, esquema y selección | Documentado parcialmente |
| Diseño de prueba de concepto | Protocolos e indicadores | Propuesto en este informe |
| Funciones críticas de lectura | Logs de mediciones y pruebas | Pendiente de evidencia |
| Caracterización de sensores | Calibración/contraste y limitaciones | Pendiente |
| Trazabilidad y almacenamiento | Dataset y pruebas de recepción | Pendiente |
| Experimento con papa y urea | Controles, bitácora y repeticiones | Pendiente |
| Análisis de resultados | Figuras, tablas y discusión | Pendiente |
| Demostración TRL 3 | Resultados verificables y conclusiones | No acreditada todavía |

**Evaluación provisional:** GREENPLANT cuenta con un concepto y una ruta metodológica para su prueba de concepto. La acreditación de TRL 3 queda condicionada a que se ejecuten y documenten las pruebas de funciones críticas con resultados suficientes [1,2].

## 13. Conclusiones preliminares y siguientes pasos

1. GREENPLANT constituye una propuesta de monitoreo experimental orientada a estudiar señales de NH₃, CO₂ y condiciones ambientales en el cultivo de papa sometido a tratamientos de fertilización con urea. La relevancia agronómica del estudio se fundamenta en la literatura sobre volatilización de amoníaco [3,4].
2. Los sensores definidos para gases son MQ-137 y MH-Z19C. Sus principios de medición son distintos y exigen verificaciones específicas: el primero requiere especial atención a la respuesta semiconductor y a la calibración; el segundo se basa en NDIR y dispone de salida digital UART [5,6].
3. El BME280 y el sensor de humedad del suelo aportarán contexto ambiental; es necesario verificar su instalación, condiciones de operación y, para el sustrato, un método de calibración apropiado [7,8].
4. El ESP32 es técnicamente apropiado para organizar las interfaces y el registro de datos, siempre que se comprueben las tensiones, la adquisición analógica y la conectividad en el montaje real [9,10].
5. La concentración observada en la cámara no debe confundirse con una tasa de emisión de NH₃ ni con una estimación directa de nitrógeno perdido sin metodología de cuantificación validada [4].
6. El cumplimiento de TRL 3 requerirá resultados documentados, reproducibles y contrastados con los indicadores previstos, conforme a las definiciones de madurez tecnológica consultadas [1,2].

**Pasos inmediatos recomendados:** terminar el inventario y esquema eléctrico definitivo; verificar el montaje y las lecturas individuales; definir controles, dosis y réplicas con asesoría agronómica; registrar los datos originales; y completar las tablas de resultados y discusión a partir de evidencias reales.

## 14. Referencias bibliográficas

*Estilo Vancouver. Fecha de consulta de sitios web: 2 de noviembre de 2026. La numeración coincide con las citas incluidas en el texto.*

[1] National Aeronautics and Space Administration (NASA). **Technology Readiness Levels** [Internet]. Washington, DC: NASA; 2023 [citado 2026 nov 2]. Disponible en: https://www.nasa.gov/directorates/somd/space-communications-navigation-program/technology-readiness-levels/

[2] U.S. Department of Energy. **Technology Readiness Levels (TRLs)** [Internet]. Washington, DC: DOE [citado 2026 nov 2]. Disponible en: https://www.energy.gov/cmei/technology-readiness-levels-trls

[3] Skorupka M, Nosalewicz A. **Ammonia volatilization from fertilizer urea—A new challenge for agriculture and industry in view of growing global demand for food and energy crops.** Agriculture. 2021;11(9):822. doi:10.3390/agriculture11090822. Disponible en: https://www.mdpi.com/2077-0472/11/9/822

[4] Scotto di Perta E, Fiorentino N, Carozzi M, Cervelli E, Pindozzi S. **A review of chamber and micrometeorological methods to quantify NH₃ emissions from fertilisers field application.** International Journal of Agronomy. 2020;2020:8909784. doi:10.1155/2020/8909784. Disponible en: https://doi.org/10.1155/2020/8909784

[5] Zhengzhou Winsen Electronics Technology Co., Ltd. **MQ137 Ammonia Gas Sensor: specifications and operating principle** [Internet]. [citado 2026 nov 2]. Disponible en: https://www.winsen-sensor.com/sensors/toxic-gas-sensor/mq137.html

[6] Zhengzhou Winsen Electronics Technology Co., Ltd. **MH-Z19C NDIR CO₂ Sensor for HVAC and IAQ: specifications** [Internet]. [citado 2026 nov 2]. Disponible en: https://www.winsen-sensor.com/sensors/air-quality-sensor/mh-z19c.html

[7] Bosch Sensortec. **BME280 humidity sensor: product information and datasheet** [Internet]. [citado 2026 nov 2]. Disponible en: https://www.bosch-sensortec.com/en/products/environmental-sensors/humidity-sensors-bme280

[8] Domínguez-Niño JM, et al. **On the accuracy of factory-calibrated low-cost soil water content sensors.** Sensors. 2019;19(14):3101. doi:10.3390/s19143101. Disponible en: https://pubmed.ncbi.nlm.nih.gov/31337053/

[9] Espressif Systems. **ESP32 Series Datasheet** [Internet]. [citado 2026 nov 2]. Disponible en: https://documentation.espressif.com/esp32_datasheet_en.html

[10] Espressif Systems. **Analog to Digital Converter (ADC) Calibration Driver – ESP32** [Internet]. ESP-IDF Programming Guide [citado 2026 nov 2]. Disponible en: https://docs.espressif.com/projects/esp-idf/en/latest/esp32/api-reference/peripherals/adc/adc_calibration.html

---

## Anexos por completar

- **Anexo A.** CAD, planos y medidas de la cámara experimental.
- **Anexo B.** Fotografías fechadas de fabricación y ensamblaje.
- **Anexo C.** Inventario real, modelos y fichas técnicas de los módulos.
- **Anexo D.** Esquemático, PCB y tabla de conexión de pines al ESP32.
- **Anexo E.** Firmware, versión, parámetros de adquisición y repositorio.
- **Anexo F.** Procedimiento experimental: tratamientos, controles y réplicas.
- **Anexo G.** Calibración, contraste instrumental y mediciones de referencia.
- **Anexo H.** Bitácora, datos crudos y trazabilidad de ensayos.
- **Anexo I.** Gráficas, estadísticos y resultados por tratamiento.
- **Anexo J.** Capturas del LCD, dashboard y almacenamiento.
- **Anexo K.** Código y evaluación de Machine Learning, si aplica.
