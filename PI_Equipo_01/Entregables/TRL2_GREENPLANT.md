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

Definición del TRL 2 en GREENPLANT

Mankins describe los niveles de madurez tecnológica como una escala que va desde la observación de principios básicos hasta la operación de un sistema probado [1]. Según la definición de niveles empleada en el curso, en el TRL 2 se desarrolla investigación aplicada para explorar los usos prácticos de una propuesta tecnológica cuyas aplicaciones todavía son especulativas. Este nivel se sustenta en un análisis del estado del arte acotado al concepto de aplicación, da importancia a la propiedad intelectual y se desarrolla en un entorno de laboratorio.

En GREENPLANT, el concepto que se formula es un sistema experimental de laboratorio que registra amoníaco gaseoso, NH₃(g), dióxido de carbono gaseoso, CO₂(g), las condiciones del aire y la humedad del sustrato durante ensayos de fertilización con urea en plantas de papa (Solanum tuberosum) de la variedad Única, liberada en el Perú en 1998 y adaptada desde la costa hasta la sierra [2]. La aplicación que se explora es comparar cómo cambia el amoníaco registrado según la dosis y la forma de aplicación de la urea, ya que parte del nitrógeno de este fertilizante puede perderse como NH₃(g) después de aplicarlo [3], [4].

1. Artículos científicos que respaldan la propuesta tecnológica

1.1. Medición de amoníaco con el sensor MQ-137

Petric et al. desarrollaron un dispositivo de monitoreo de amoníaco con un sensor MQ-137 conectado a una placa Croduino Basic 2 y compararon sus registros con un analizador Geotech GA5000 [5]. El estudio calibró el dispositivo en un entorno controlado y evaluó su repetibilidad, lo que demuestra que este sensor de bajo costo puede entregar mediciones útiles de NH₃ siempre que se calibre frente a una referencia. Este es el antecedente principal para usar el MQ-137 en GREENPLANT.

Según el fabricante, el material sensible del MQ-137 es dióxido de estaño (SnO₂), su rango de detección va de 5 a 500 ppm de amoníaco, funciona con un calentador de 5 V y requiere más de 48 horas de precalentamiento antes de usarse [6]. Siguiendo el criterio de Petric et al., GREENPLANT calibrará la señal analógica del sensor con gas patrón de NH₃ de concentración conocida y verificará la calibración con el método de absorción en ácido, procedimiento que también se empleó para validar el detector de volatilización de la patente CN115097075B [7].

Huerta et al. mostraron que la temperatura y la humedad del aire alteran la respuesta de los sensores de óxido metálico, como el MQ-137, y propusieron un método para corregir ese efecto a partir de registros ambientales simultáneos [8]. Por esta razón, GREENPLANT registrará la temperatura y la humedad del aire en el mismo instante que la señal de amoníaco.

1.2. Medición de dióxido de carbono con el sensor MH-Z19B

Othman et al. construyeron una cámara de calibración para validar sensores de calidad del aire de bajo costo y compararon el MH-Z19B con un monitor de referencia Onset HOBO MX1102 [9]. Su trabajo incluyó la evaluación experimental del sensor y su corrección por regresión, por lo que respalda directamente el modelo elegido para GREENPLANT. De forma complementaria, Dubey et al. evaluaron otros sensores de CO₂ de tecnología infrarroja no dispersiva (NDIR) frente a un instrumento de referencia y mostraron la importancia de calibrarlos antes de usarlos [10].

El fabricante del MH-Z19B indica que el sensor mide CO₂ por absorción infrarroja, se comunica por UART y necesita que su ventana de difusión quede libre y alejada de fuentes de calor [11]. En GREENPLANT, el MH-Z19B se contrastará con una referencia antes de comparar tratamientos, siguiendo el procedimiento de Othman et al. [9].

1.3. Condiciones del aire y humedad del sustrato

El BME280 registra temperatura, humedad relativa y presión del aire, y entrega sus datos por el bus I²C [12]. La tesis de Bezborodov describe un equipo de monitoreo del aire que integra el ESP32, el BME280 y el MH-Z19B, lo que confirma que estos componentes pueden trabajar juntos [13]. El fabricante advierte que la lectura de temperatura depende del calor del propio circuito [12]; por eso el sensor debe ubicarse lejos de las fuentes de calor de la placa.

Para la humedad del sustrato se eligió la sonda capacitiva v1.2. Placidi et al. estudiaron este sensor dentro de un sistema de monitoreo agrícola de bajo costo y relacionaron su señal con el contenido de agua del suelo medido por métodos de referencia [14]. A partir de ese trabajo, GREENPLANT calibrará la sonda en el mismo sustrato de los ensayos, comparando su señal con el contenido de agua obtenido al pesar muestras húmedas y secas.

1.4. Medición de gases en cámaras y diseño de la cámara en Onshape

Davidson et al. analizaron las fuentes de error en las mediciones de gases realizadas con cámaras y concluyeron que el volumen, la duración de la medición, el mezclado del aire y las perturbaciones que introduce la propia cámara deben controlarse o documentarse [15]. Baneschi et al. propusieron un protocolo para cámaras cerradas que recomienda calibrar en el intervalo de valores esperado, repetir las mediciones y elegir con cuidado el intervalo de tiempo usado para ajustar la curva de concentración; además, encontraron que la regresión lineal ofrece la mejor reproducibilidad [16]. Othman et al., por su parte, evaluaron la circulación del aire y la estabilidad ambiental de su cámara de calibración [9]. Estos tres trabajos son la base del diseño de la cámara de GREENPLANT.

A partir de esos criterios, el equipo modeló en Onshape un prototipo de tres piezas de PETG que se apilan sobre una misma huella de 180 × 180 mm (Figura 1). La base, de 180 × 180 mm en planta, aloja la placa electrónica y la fuente; su cara superior tiene aberturas que comunican los sensores con el aire de la cámara, y su frente incluye un saliente inclinado de 127 mm de ancho y 26 mm de proyección para la pantalla (Figura 2). La pieza Soporte/Planta forma las paredes de la cámara, con 180 mm de lado exterior, 170 mm entre paredes y 200 mm de altura; una de sus caras queda abierta para colocar y retirar la maceta (Figura 3). La tapa, de 180 × 180 mm y 4,082 mm de espesor, cierra la cámara por arriba y se fija con cuatro perforaciones en las esquinas (Figura 4).

<img width="400" height="500" alt="WhatsApp Image 2026-10-30 at 11 02 56 AM" src="https://github.com/user-attachments/assets/ae8d851e-f7b2-4c90-b3de-7b02eb0877fd" />


Figura 1. Vista de conjunto del prototipo modelado en Onshape: tapa, cámara (Soporte/Planta) y base, en el orden en que se ensamblan.

<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/c711088a-44b7-4ca6-9874-f98113872913" />


Figura 2. Plano de la Base: vistas superior, frontal, lateral e isométrica (Onshape, PETG, escala 1:5).

<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/81ca0a23-d4d7-4291-96eb-4c09884b8da9" />


Figura 3. Plano del Soporte/Planta: cámara de cultivo con una cara abierta (Onshape, PETG, escala 1:5).

<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/f4767c66-5cf2-4a17-953f-8e0a3ee07dd9" />


Figura 4. Plano de la Tapa: placa de 180 × 180 mm con perforaciones de fijación (Onshape, PETG, escala 1:5).

Cada decisión del modelo responde a uno de los criterios citados. La electrónica queda en la base, separada del aire que se mide, porque el BME280 se ve afectado por el calor del circuito [12] y el MQ-137 opera con un calentador de 5 V [6]. Las aberturas de la base permiten el intercambio de aire que el fabricante del MH-Z19B exige para su ventana de difusión [11]. La placa incluye además una salida de 12 V para un ventilador, cuyo régimen se documentará porque el mezclado del aire influye en la concentración registrada [15], [9]. Finalmente, durante las mediciones la cara abierta del Soporte/Planta se cerrará con un panel, ya que las fugas y la renovación no controlada del aire alteran la lectura [15].

Las dimensiones del modelo permiten calcular el volumen de la cámara, dato que Davidson et al. y Baneschi et al. consideran necesario para interpretar las concentraciones [15], [16]. Con las cotas interiores del plano, la cámara tiene 5,8 L; si se usa una maceta de 15 cm de diámetro superior, 12 cm de diámetro inferior y 13 cm de altura, que ocupa 1,9 L, quedan cerca de 3,9 L de aire. Con esa altura de maceta quedan unos 7 cm libres sobre el sustrato, por lo que las mediciones de gases se concentrarán en los primeros días después de la siembra; para estudiar plantas más desarrolladas se necesitará un Soporte/Planta más alto.

Con ese volumen se estimó si el MQ-137 podrá detectar el amoníaco. En la superficie de la maceta (0,018 m²), una dosis de 160 kg N/ha equivale a 0,28 g de nitrógeno y una de 80 kg N/ha a 0,14 g. Si se pierde entre 5 y 20 % de ese nitrógeno como amoníaco, rango reportado por la FAO y la IFA [4], y la pérdida se reparte en los cinco días en que Wan et al. observaron los picos de volatilización en papa [17], la cámara cerrada alcanzaría a 25 °C entre 4 y 35 ppm después de 10 minutos y entre 13 y 105 ppm después de 30 minutos. Como el MQ-137 detecta desde 5 ppm [6], un cierre de 10 minutos dejaría el caso de menor pérdida fuera de su rango; por eso se propone un cierre de 30 minutos. Esta estimación es de orden de magnitud, no considera fugas, adsorción en las paredes ni picos mayores al promedio diario, y se verificará en el TRL 3.

1.5. Integración electrónica en la placa PCB3

Berrios Gomez y Rivera Herrera desarrollaron en el Perú un sistema basado en ESP32 para monitorear variables ambientales y del suelo en un invernadero de lechugas, con nodos que enviaban la información a un nodo central para almacenarla y consultarla [18]. Junto con la tesis de Bezborodov [13], este trabajo respalda el uso del ESP32 como unidad de adquisición en GREENPLANT. A partir de esos antecedentes, el equipo diseñó una placa propia, la PCB3, que reúne todas las conexiones del sistema (Figura 5).

<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/a4f95e06-0d6d-45b1-ba11-f57689b66f14" />


Figura 5. Guía de la placa PCB3, cara superior. Los recuadros identifican los sensores (amarillo), el control (celeste), las salidas y la pantalla (magenta) y la alimentación (naranja). Vista generada a partir de los archivos Gerber.

La PCB3 se diseñó en EasyEDA Pro como un circuito impreso de dos capas de aproximadamente 107 × 110 mm, con cuatro perforaciones de 3,1 mm para tornillos M3, de modo que cabe dentro de la base de 180 × 180 mm. Los archivos de fabricación están listos, pero la placa aún no se ha fabricado ni probado. Los sensores no se sueldan a la placa, sino que se conectan mediante conectores de cuatro pines, en el caso del MQ-137, el MH-Z19B y el BME280, y de tres pines, en el caso de la sonda de humedad (conector P1). Así, cada sensor puede ubicarse junto a su abertura de la base o dentro de la maceta mediante cables.

La energía entra a 12 V por una bornera. Un convertidor LM2596 reduce esa tensión a 5 V para el ESP32, los sensores, la pantalla y el módulo de relés [19], mientras que la línea de 12 V alimenta el ventilador y la luz LED. El ESP32, de 30 pines según la huella de la placa, entrega a su vez 3,3 V, que sirven de referencia para el lado de baja tensión de un conversor de nivel lógico [20].

En cuanto a la comunicación, el BME280 comparte con el ESP32 un bus I²C de 3,3 V conectado a GPIO21 y GPIO22 [12]. La pantalla LCD 1602 trabaja a 5 V mediante un adaptador I²C; estos adaptadores usan expansores de entradas y salidas como el PCF8574 [21], y el modelo exacto se confirmará al montar la placa. Como los dos buses trabajan a tensiones distintas, la placa incluye un conversor de nivel lógico, técnica descrita por NXP para buses I²C [22]. El MH-Z19B usa el segundo puerto UART del ESP32, en GPIO16 y GPIO17 [11], [20].

Las señales analógicas del MQ-137 y de la sonda de humedad llegan a GPIO34 y GPIO32, que pertenecen al ADC1 del ESP32. Esta elección es necesaria porque el ADC2 solo puede usarse cuando el controlador Wi-Fi no está activo [23], y GREENPLANT transmitirá sus datos por Wi-Fi mediante el protocolo MQTT, que organiza la comunicación en un esquema de publicación y suscripción [24]. Por último, el ESP32 controla un módulo de dos relés de 5 V, del tipo SRD-05VDC-SL-C [25], mediante GPIO25 y GPIO26, y un LED de estado mediante GPIO2 [20].

1.6. Interpretación del dióxido de carbono

Kuzyakov revisó las fuentes del CO₂ que sale del suelo y distinguió las contribuciones de las raíces, de los microorganismos y de la descomposición de la materia orgánica [26]. A esas fuentes se suma la fotosíntesis, que fija CO₂ cuando la planta recibe luz; Li et al. evaluaron precisamente la fotosíntesis, la biomasa y el rendimiento de plantas de papa cultivadas con iluminación LED en cámara de crecimiento [27]. Por ello, GREENPLANT registrará el CO₂ como variable complementaria, documentará los periodos de encendido de la luz y no atribuirá sus variaciones solo a la urea, mientras que el NH₃(g) se mantiene como la variable principal del estudio.

1.7. Síntesis del respaldo científico

En conjunto, los artículos revisados respaldan cada componente de la propuesta: el MQ-137 cuenta con un antecedente de calibración frente a un analizador [5]; el MH-Z19B, con una validación en cámara [9]; la sonda capacitiva, con una caracterización agrícola [14]; y la integración con ESP32, con un sistema aplicado en el Perú [18]. Los trabajos sobre cámaras [15], [16] orientan el diseño en Onshape y el procedimiento de medición. Sin embargo, ninguno de los estudios revisados combina estos sensores en una cámara de laboratorio para comparar tratamientos de urea en papa variedad Única. Ese vacío es el espacio que explora GREENPLANT en el TRL 2, con aplicaciones que todavía deben comprobarse experimentalmente.

2. Análisis de patentabilidad y protección

Esta sección evalúa si GREENPLANT podría protegerse mediante una patente y cuál es el mecanismo adecuado para cada parte del proyecto. El análisis se basa en la Decisión 486 de la Comunidad Andina, que establece el régimen común de propiedad industrial vigente en el Perú [28], y en una búsqueda de patentes relacionadas con la propuesta.

2.1. Requisitos de patentabilidad

La Decisión 486 establece que una invención es patentable cuando cumple tres requisitos [28]. El primero es la novedad: según el artículo 16, una invención es nueva cuando no está comprendida en el estado de la técnica. El segundo es el nivel inventivo: según el artículo 18, la invención no debe resultar obvia ni derivarse de manera evidente del estado de la técnica para una persona del oficio. El tercero es la aplicación industrial: según el artículo 19, su objeto debe poder producirse o utilizarse en cualquier tipo de industria.

La misma norma define, en su artículo 81, el modelo de utilidad como toda nueva forma, configuración o disposición de elementos de un objeto que permita un mejor o diferente funcionamiento, utilización o fabricación, o que le proporcione una utilidad, ventaja o efecto técnico que antes no tenía [28]. Esta figura resulta relevante para GREENPLANT porque su aporte físico está en la configuración de la cámara y no en un nuevo principio de medición.

2.2. Búsqueda de patentes relacionadas

La búsqueda se realizó en Google Patents y Patsnap con términos como «ammonia volatilization detection device», «plant growth chamber CO₂» y «greenhouse environmental monitoring system». Se identificaron cuatro documentos cercanos a GREENPLANT.

El documento más próximo es la patente china CN115097075B, de la Universidad de Ciencia y Tecnología de Kunming, solicitada en 2022 [7]. Describe un equipo de campo para detectar en línea la volatilización de amoníaco, formado por una cámara de gas, cuatro sensores de NH₃ entre los que se encuentra un MQ-137, placas Arduino y un módulo inalámbrico ESP8266. A diferencia de GREENPLANT, este equipo no mide CO₂, condiciones del aire ni humedad del sustrato, y está pensado para el campo abierto, no para macetas dentro de una cámara de laboratorio.

La patente estadounidense US5341595A, de Griggs, Bartley y Rule, describe una cámara de crecimiento exterior hermética, con control de temperatura y humedad, adaptada para analizar la absorción de CO₂ por las plantas [29]. No mide amoníaco ni está orientada a la fertilización, y corresponde a una cámara de gran tamaño, no a un equipo de bajo costo. La solicitud china CN114365649A, de Liu, propone un sistema de monitoreo para invernaderos con sensores de CO₂, temperatura, humedad, humedad del suelo y luz, además de ventiladores e iluminación controlados a distancia [30]; tampoco mide amoníaco ni compara tratamientos de urea, y fue rechazada en 2024.

Por último, la patente US7341694B2, de Nishiyama et al., protege un sensor de amoníaco con una capa sensible de ZrO₂ que contiene tungsteno [31]. Su objeto es el elemento de detección, mientras que GREENPLANT utiliza sensores comerciales y no desarrolla un nuevo elemento sensor. Esta búsqueda es preliminar: en la siguiente etapa se ampliará a la base de INDECOPI y a Espacenet, y se usarán los códigos de clasificación de los documentos encontrados.

2.3. Evaluación de patentabilidad de GREENPLANT

En cuanto a la novedad, la combinación exacta de NH₃, CO₂, condiciones del aire y humedad del sustrato en una cámara modular para comparar tratamientos de urea no apareció en la búsqueda. Sin embargo, sus partes ya forman parte del estado de la técnica: el uso de un MQ-137 con microcontrolador y transmisión inalámbrica para medir la volatilización de amoníaco [7], las cámaras de crecimiento con monitoreo de CO₂ [29] y los sistemas de monitoreo con sensores ambientales y de suelo [30].

En cuanto al nivel inventivo, combinar sensores comerciales de funciones conocidas con un microcontrolador sería previsible para una persona del oficio, que es precisamente la situación que el artículo 18 excluye [28]. La aplicación industrial, en cambio, sí se cumple, porque el equipo puede fabricarse a partir del modelo de Onshape y de los archivos de la placa, y utilizarse en laboratorios agrícolas [28]. En consecuencia, no se recomienda solicitar una patente de invención para el sistema completo.

2.4. Estrategia de protección

La configuración física de la cámara podría protegerse como modelo de utilidad, siempre que se demuestre una ventaja técnica [28]; la solicitud ante INDECOPI debe describir esa ventaja de forma concreta [32]. A partir de los planos de Onshape (Figuras 2 a 4), las características que podrían sustentarla son cuatro: la separación, dentro de una misma huella de 180 × 180 mm, entre el compartimento electrónico y el aire donde crece la planta, orientada a reducir la influencia del calor de la placa sobre las lecturas [12], [6]; las aberturas de la base, que comunican los sensores con la cámara sin introducir la placa en ella [11]; el visor inclinado, que permite leer las mediciones sin abrir la cámara [15]; y la unión de las tres piezas con perforaciones en las esquinas, que facilita desmontar el equipo.

Aun así, una caja protectora para la electrónica ya es una práctica conocida [18], y el equipo de Kunming también separa sus compartimentos de detección y de limpieza [7]. Por ello, la solicitud solo sería viable si los ensayos del TRL 3 demuestran un efecto técnico concreto, por ejemplo, una menor diferencia de temperatura entre el aire de la cámara y el entorno con el equipo en funcionamiento.

El código desarrollado para adquirir, organizar, transmitir y visualizar los datos se protegerá mediante derecho de autor como programa de ordenador. El equipo documentará su autoría, conservará sus versiones y distinguirá las bibliotecas de terceros; INDECOPI permite registrar este tipo de obras en su plataforma de Registro Virtual de Obras [33].

Finalmente, debe cuidarse la divulgación del proyecto. En el Perú, la divulgación de una invención dentro de los 12 meses anteriores a la solicitud no afecta su novedad [34]. Como GREENPLANT se presentará en las exposiciones del curso, la fecha de la primera presentación pública marcará el inicio de ese plazo si el equipo decide solicitar un modelo de utilidad.

3. Perfil o propuesta del proyecto
3.1. Título

GREENPLANT: sistema experimental de laboratorio para el monitoreo de NH₃(g), CO₂(g) y variables ambientales en ensayos de fertilización con urea en papa (Solanum tuberosum) variedad Única.

3.2. Problema y justificación

La papa es un cultivo de gran importancia alimentaria y económica en el Perú, cuya producción sostienen más de 700 mil agricultores de 19 regiones [35]. Para fertilizarla se usa con frecuencia urea, pero parte de su nitrógeno puede perderse como NH₃(g): cuando la ureasa del suelo hidroliza la urea, el pH sube alrededor del gránulo y favorece la formación de amoníaco [3]. La FAO y la IFA estiman pérdidas de 15 a 20 % del nitrógeno aplicado en superficie y de 5 a 15 % cuando la urea se incorpora al suelo [4].

En papa, Wan et al. observaron que la volatilización aumentó con la dosis de nitrógeno [17], y Lee et al. compararon la volatilización de amoníaco con urea y sulfato de amonio durante su cultivo [36]; en otros suelos, Rochette et al. comprobaron que la profundidad de incorporación modifica las pérdidas [37]. Falta, sin embargo, una herramienta de bajo costo que permita comparar estos factores en laboratorio con la variedad Única. GREENPLANT responde a esa necesidad reuniendo en un solo equipo los sensores respaldados en la sección 1.

3.3. Pregunta de investigación e hipótesis

La pregunta que orienta el proyecto es la siguiente: ¿cómo varía la concentración de NH₃(g) registrada en una cámara de laboratorio con macetas de papa variedad Única según la dosis (80 o 160 kg N/ha) y la forma de aplicación (superficial o incorporada) de la urea, considerando el CO₂(g), las condiciones del aire y la humedad del sustrato?

La hipótesis de trabajo (H₁) plantea que, con la misma dosis, la urea aplicada en superficie producirá concentraciones de NH₃(g) más altas que la urea incorporada, y que, con la misma forma de aplicación, la dosis de 160 kg N/ha producirá concentraciones más altas que la de 80 kg N/ha. Esta dirección se basa en las mayores pérdidas reportadas para la aplicación superficial [4], [3], en el efecto de la profundidad de incorporación [37] y en el aumento de la volatilización con la dosis observado en papa [17]. La hipótesis nula (H₀) plantea que ni la dosis ni la forma de aplicación modifican la concentración de NH₃(g) registrada.

3.4. Objetivos

El objetivo general es desarrollar un sistema experimental de laboratorio que registre NH₃(g), CO₂(g), condiciones del aire y humedad del sustrato, y que permita comparar de forma relativa la concentración de NH₃(g) entre dosis y formas de aplicación de urea en macetas de papa variedad Única. Los resultados servirán para ordenar los tratamientos según su riesgo relativo de volatilización, no para calcular pérdidas absolutas de nitrógeno ni para recomendar dosis.

Para alcanzarlo se plantean cinco objetivos específicos. El primero es sustentar la selección de sensores y el esquema de medición con artículos científicos y documentación técnica. El segundo es integrar los sensores y el ESP32 en una versión corregida de la placa y montarlos en la cámara modelada en Onshape. El tercero es establecer procedimientos de calibración y registro para cada sensor. El cuarto es obtener y comparar series de medición identificadas por tratamiento, repetición y día. El quinto es evaluar, en el TRL 3, si la pendiente de acumulación en la cámara permite estimar flujos de NH₃ y pasar de comparaciones relativas a estimaciones de pérdida [16], [15].

3.5. Arquitectura del sistema

La plataforma reúne la cámara modelada en Onshape (sección 1.4), la placa PCB3 con el ESP32 (sección 1.5), los cuatro sensores y una aplicación de registros. El ESP32 leerá los sensores y publicará cada medición como un mensaje JSON en un bróker MQTT; una aplicación suscrita al bróker almacenará los datos y los mostrará en gráficas [24]. Cada registro conservará la señal original del sensor y el valor calculado, junto con la fecha, la hora, el tratamiento y la identificación de la maceta, mientras que la pantalla LCD mostrará las últimas lecturas en el propio equipo.

3.6. Errores de diseño de la PCB3 y correcciones para la PCB4

La revisión de los archivos de fabricación de la PCB3 detectó dos errores de diseño que se corregirán en una nueva versión, la PCB4, antes de conectar los sensores. El primero es que las salidas del MQ-137 llegan directamente al ESP32. El circuito de medición del sensor trabaja con 5 V [6], por lo que su salida puede acercarse a ese valor, mientras que las entradas del ESP32 admiten como máximo su tensión de alimentación de 3,3 V [20]; además, con una atenuación de 11 dB, el intervalo de medición recomendado es de 150 a 2450 mV [23]. En la PCB4 se añadirá un divisor resistivo en la salida analógica y una adaptación de nivel en la salida digital, y la salida de la sonda de humedad recibirá la misma corrección si supera ese intervalo.

El segundo error es que el ventilador y la luz LED reciben 12 V directamente, de modo que los relés no pueden encenderlos ni apagarlos. En la PCB4, la línea positiva de cada carga pasará por los contactos de un relé [25], para que el ESP32 controle el mezclado del aire y el periodo de luz. Al montar el equipo, además, el BME280 se ubicará lejos del convertidor LM2596 y del calentador del MQ-137 [12], [6], y se definirá el panel que cierra la cara abierta de la cámara [15].

3.7. Plan experimental

El plan adapta la comparación de dosis en papa de Wan et al. [17] y el estudio de incorporación de urea de Rochette et al. [37]. Se proponen cinco tratamientos: un control sin urea y las cuatro combinaciones de dos dosis, 80 y 160 kg N/ha, con dos formas de aplicación, superficial e incorporada. Las dosis corresponden a las que Zúñiga et al. evaluaron en papa de la sierra central del Perú [38]; como ese estudio usó variedades nativas, se toman como referencia y no como recomendación para Única. En la aplicación superficial, los gránulos quedarán sobre el sustrato; en la incorporada, se enterrarán a unos 5 cm, dentro del intervalo de profundidad en el que la incorporación reduce la pérdida de amoníaco [3], [37].

Según su fórmula, CO(NH₂)₂, la urea contiene 46,6 % de nitrógeno. En una maceta de 15 cm de diámetro (0,018 m²), 80 kg N/ha equivalen a 0,14 g de nitrógeno, es decir, 0,30 g de urea, y 160 kg N/ha equivalen a 0,28 g de nitrógeno, es decir, 0,61 g de urea. Estos valores se ajustarán a la concentración declarada en el envase y se pesarán con una balanza de 0,01 g.

La urea se aplicará en la siembra. En el cultivo comercial, el INIA aplica la mitad del nitrógeno en la siembra y la otra mitad, como urea, en el primer aporque [39]; el ensayo evalúa solo la aplicación en la siembra porque la altura de la cámara limita las mediciones a plantas pequeñas y porque los picos de volatilización ocurren en los primeros días después de fertilizar [17]. Todas las macetas usarán tubérculo-semilla de la variedad Única y un mismo sustrato, cuyo pH y propiedades químicas se analizarán porque influyen en la volatilización [40]. Existe además un antecedente del cultivo de Única en invernadero con fertilización de fondo con urea [41].

Cada tratamiento tendrá tres repeticiones, es decir, 15 macetas, número coherente con las tres o cuatro repeticiones en bloques completos al azar empleadas en la evaluación de la variedad Única [2]. Como el prototipo tiene una sola cámara, las macetas permanecerán fuera de ella en las mismas condiciones y entrarán una por una para cada medición. Medir las 15 macetas en un día tomaría unas 10 horas, considerando 30 minutos de cierre y 10 de ventilación por maceta. Por eso, el ensayo se organizará en tres ciclos sucesivos: en cada ciclo se siembra y fertiliza una repetición de los cinco tratamientos, y cada día se miden sus cinco macetas en orden aleatorio, en unas 3,5 horas. Cada ciclo funciona como un bloque, de modo que las diferencias entre semanas no se confunden con el efecto de los tratamientos [2].

Cada ciclo incluirá un día de línea de base antes de fertilizar y siete días de medición después de la aplicación, periodo que cubre los picos observados entre el primer y el quinto día [17]. En cada medición se registrarán la curva de NH₃(g) durante los 30 minutos de cierre, el CO₂(g), la temperatura, la humedad relativa y la humedad del sustrato. La variable principal será la concentración de NH₃(g) al final del cierre, y la secundaria, la pendiente de acumulación ajustada por regresión lineal, opción que Baneschi et al. recomiendan por su reproducibilidad [16]. Los tratamientos se compararán mediante un análisis de varianza en bloques completos al azar, con el ciclo como bloque y los días como medidas repetidas de cada maceta.

Antes del ensayo se realizarán dos verificaciones. La primera es instrumental: fabricar la PCB4, comprobar sus tensiones de 12 V, 5 V y 3,3 V [19], [20], precalentar el MQ-137 durante más de 48 horas [6], calibrarlo con gas patrón dentro de la cámara [5], contrastar el MH-Z19B con una referencia [9] y calibrar la sonda en el sustrato del ensayo [14]. La segunda es del montaje: imprimir las tres piezas, medir el volumen real de la cámara, revisar el cierre del panel frontal y registrar el régimen del ventilador [15], [16]. Terminada la fase de gases, las macetas seguirán creciendo fuera de la cámara y se registrarán su emergencia, altura y número de hojas como información complementaria.

3.8. Resultados esperados y criterios de interpretación

Los resultados del proyecto serán un prototipo construido a partir de los planos de Onshape y de la PCB4, un procedimiento de calibración y operación, una base de datos identificada por maceta, gráficas de la evolución de cada variable y un informe que ordene los tratamientos según la concentración relativa de NH₃(g). Esa ordenación permitirá orientar de forma preliminar el manejo de la urea, por ejemplo, saber si incorporarla reduce el amoníaco registrado frente a dejarla en superficie. No permitirá recomendar una dosis, porque esa decisión requiere análisis del suelo, conocer los requerimientos del cultivo y validar en campo [4], [39].

Las variables se reportarán como concentraciones dentro de la cámara. Una concentración en ppm no permite calcular por sí sola el porcentaje del nitrógeno que se volatilizó; para ello se necesita el flujo, que en una cámara cerrada se estima como F = (ΔC/Δt) × V/A, donde ΔC/Δt es la pendiente de acumulación, V el volumen de aire y A la superficie cubierta [15], [16]. El TRL 2 se limita a la comparación relativa, y la estimación de flujos se evaluará en el TRL 3. Del mismo modo, el CO₂(g) se interpretará considerando el intercambio de aire [15], las fuentes biológicas del suelo y de las raíces [26] y la fotosíntesis bajo la luz LED [27], sin atribuir sus variaciones solo a la urea.

3.9. Criterios de cierre del TRL 2 y paso al TRL 3

El TRL 2 se cumple cuando el concepto tecnológico y su aplicación están formulados y respaldados [1]. En GREENPLANT, esto se demuestra con cuatro productos de este informe: el respaldo científico de cada componente (sección 1); el análisis de patentabilidad y la estrategia de protección (sección 2); el diseño conceptual de la cámara en Onshape y de la placa electrónica, con sus errores identificados (secciones 1.4, 1.5 y 3.6); y un plan experimental con tratamientos, dosis, repeticiones, duración y una estimación de la concentración esperada (secciones 1.4 y 3.7).

El paso al TRL 3 corresponde a la prueba de concepto analítica y experimental [1]. Para GREENPLANT, esa prueba consistirá en fabricar la PCB4 e imprimir las tres piezas de la cámara, medir su volumen real y comprobar su cierre, obtener la curva de calibración del MQ-137 dentro de la cámara después de su precalentamiento y realizar un ciclo piloto que confirme que las concentraciones registradas quedan dentro del rango de 5 a 500 ppm del sensor [6].

Referencias bibliográficas

[1] J. C. Mankins, “Technology readiness assessments: A retrospective,” Acta Astronautica, vol. 65, n.os 9–10, pp. 1216–1223, 2009, doi: 10.1016/j.actaastro.2009.03.058. Disponible: https://doi.org/10.1016/j.actaastro.2009.03.058

[2] R. O. Gutiérrez-Rosales, J. A. Espinoza-Trelles y M. Bonierbale, “UNICA: variedad peruana para mercado fresco y papa frita con tolerancia y resistencia para condiciones climáticas adversas,” Revista Latinoamericana de la Papa, vol. 14, n.º 1, pp. 41–50, 2007. Consultado: 30-oct-2026. [En línea]. Disponible: https://dialnet.unirioja.es/descarga/articulo/5512141.pdf

[3] N. Rayne y C. Bandura, “Ammonia loss from urea-containing fertilizers,” University of Wisconsin–Madison Division of Extension, Crops and Soils. Consultado: 30-oct-2026. [En línea]. Disponible: https://cropsandsoils.extension.wisc.edu/articles/ammonia-loss-from-urea-containing-fertilizers/

[4] FAO e IFA, Global Estimates of Gaseous Emissions of NH₃, NO and N₂O from Agricultural Land. Roma, Italia: Food and Agriculture Organization of the United Nations e International Fertilizer Industry Association, 2001. Consultado: 30-oct-2026. [En línea]. Disponible: https://www.fao.org/4/y2780e/y2780e00.htm

[5] M. Petric, F. Dodigović, I. Grčić, P. Markužić, L. Radetić y M. Topić, “Ammonia concentration monitoring using Arduino platform,” Environmental Engineering – Inženjerstvo okoliša, vol. 6, n.º 1, pp. 21–26, 2019, doi: 10.37023/ee.6.1.4. Disponible: https://doi.org/10.37023/ee.6.1.4

[6] Zhengzhou Winsen Electronics Technology Co., Ltd., “Ammonia gas sensor (model: MQ137): Manual,” ver. 1.6, jul. 2021. Consultado: 30-oct-2026. [En línea]. Disponible: https://www.winsen-sensor.com/d/files/manual/mq137.pdf

[7] Kunming University of Science and Technology, “Ammonia volatilization online detection device based on Arduino board,” patente de China CN115097075B, solicitud CN202210747868.2, 29-jun-2022. Consultado: 30-oct-2026. [En línea]. Disponible: https://eureka.patsnap.com/patent/CN115097075B

[8] R. Huerta, T. S. Mosqueiro, J. Fonollosa, N. F. Rulkov e I. Rodriguez-Lujan, “Online decorrelation of humidity and temperature in chemical sensors for continuous monitoring,” Chemometrics and Intelligent Laboratory Systems, vol. 157, pp. 169–176, 2016, doi: 10.1016/j.chemolab.2016.07.004. Disponible: https://doi.org/10.1016/j.chemolab.2016.07.004

[9] H. Othman, G. Sieves, T. Guimarães y R. Azari, “A calibration chamber framework for low-cost indoor air quality sensor validation,” Building and Environment, vol. 287, art. 113856, ene. 2026, doi: 10.1016/j.buildenv.2025.113856. Disponible: https://doi.org/10.1016/j.buildenv.2025.113856

[10] R. Dubey et al., “Low-cost CO₂ NDIR sensors: Performance evaluation and calibration using machine learning techniques,” Sensors, vol. 24, n.º 17, art. 5675, 2024, doi: 10.3390/s24175675. Disponible: https://doi.org/10.3390/s24175675

[11] Zhengzhou Winsen Electronics Technology Co., Ltd., “Infrared CO₂ sensor module (model: MH-Z19B): User’s manual,” ver. 1.7, oct. 2020. Consultado: 28-oct-2026. [En línea]. Disponible: https://www.winsen-sensor.com/d/files/manual/mh-z19b.pdf

[12] Bosch Sensortec, “BME280: Data sheet,” rev. 1.24, feb. 2024. Consultado: 28-oct-2026. [En línea]. Disponible: https://www.bosch-sensortec.com/media/boschsensortec/downloads/datasheets/bst-bme280-ds002.pdf

[13] A. A. Bezborodov, “Розробка системи перевірки якості повітря на основі ESP32” [Desarrollo de un sistema de monitoreo de calidad del aire basado en ESP32], tesis de grado, especialidad de Ciencias de la Computación, Universidad Nacional V. N. Karazin de Járkiv, Járkiv, Ucrania, 2025. Consultado: 28-oct-2026. [En línea]. Disponible: https://ekhnuir.karazin.ua/handle/123456789/26414

[14] P. Placidi, R. Morbidelli, D. Fortunati, N. Papini, F. Gobbi y A. Scorzoni, “Monitoring soil and ambient parameters in the IoT precision agriculture scenario: An original modeling approach dedicated to low-cost soil water content sensors,” Sensors, vol. 21, n.º 15, art. 5110, 2021, doi: 10.3390/s21155110. Disponible: https://doi.org/10.3390/s21155110

[15] E. A. Davidson, K. Savage, L. V. Verchot y R. Navarro, “Minimizing artifacts and biases in chamber-based measurements of soil respiration,” Agricultural and Forest Meteorology, vol. 113, pp. 21–37, 2002, doi: 10.1016/S0168-1923(02)00100-4. Disponible: https://doi.org/10.1016/S0168-1923(02)00100-4

[16] I. Baneschi et al., “Non-steady-state closed dynamic chamber to measure soil CO₂ respiration: A protocol to reduce uncertainty,” Frontiers in Environmental Science, vol. 10, art. 1048948, 2023, doi: 10.3389/fenvs.2022.1048948. Disponible: https://doi.org/10.3389/fenvs.2022.1048948

[17] W.-f. Wan, F. Li, M. Hong, F. Chang y H.-y. Gao, “Effects of nitrogen rate and urease inhibitor on N₂O emission and NH₃ volatilization in drip irrigated potato fields,” Journal of Plant Nutrition and Fertilizers, vol. 24, n.º 3, pp. 693–702, 2018, doi: 10.11674/zwyf.17197. Disponible: https://doi.org/10.11674/zwyf.17197

[18] S. Berrios Gomez y H. J. Rivera Herrera, “Sistema IoT basado en ESP32 para el control y monitoreo de cultivos en invernadero con enfoque de agricultura 4.0,” Ingeniería Investiga, vol. 4, art. e624, 2022, doi: 10.47796/ing.v4i0.624. Disponible: https://doi.org/10.47796/ing.v4i0.624

[19] Texas Instruments, “LM2596 SIMPLE SWITCHER® power converter 150-kHz 3-A step-down voltage regulator,” SNVS124G, mar. 2023. Consultado: 30-oct-2026. [En línea]. Disponible: https://www.ti.com/lit/gpn/lm2596

[20] Espressif Systems, “ESP32 series datasheet,” ver. 5.3. Consultado: 28-oct-2026. [En línea]. Disponible: https://documentation.espressif.com/esp32_datasheet_en.html

[21] Texas Instruments, “PCF8574 remote 8-bit I/O expander for I²C bus,” SCPS068K, sep. 2024. Consultado: 30-oct-2026. [En línea]. Disponible: https://www.ti.com/lit/gpn/pcf8574

[22] NXP Semiconductors, “Level shifting techniques in I²C-bus design,” nota de aplicación AN10441. Consultado: 30-oct-2026. [En línea]. Disponible: https://www.mouser.com/pdfDocs/AN10441.pdf

[23] Espressif Systems, “Analog to Digital Converter,” ESP-IDF Programming Guide, v3.1.6. Consultado: 30-oct-2026. [En línea]. Disponible: https://docs.espressif.com/projects/esp-idf/en/v3.1.6/api-reference/peripherals/adc.html

[24] OASIS, MQTT Version 5.0, OASIS Standard, 7-mar-2019. Consultado: 28-oct-2026. [En línea]. Disponible: https://docs.oasis-open.org/mqtt/mqtt/v5.0/os/mqtt-v5.0-os.html

[25] Ningbo Songle Relay, “SRD-05VDC-SL-C,” ficha del componente. Consultado: 30-oct-2026. [En línea]. Disponible: https://www.lcsc.com/product-detail/C35449.html

[26] Y. Kuzyakov, “Sources of CO₂ efflux from soil and review of partitioning methods,” Soil Biology and Biochemistry, vol. 38, n.º 3, pp. 425–448, 2006, doi: 10.1016/j.soilbio.2005.08.020. Disponible: https://doi.org/10.1016/j.soilbio.2005.08.020

[27] J. Li et al., “Evaluating LED parameters in a growth chamber to maintain potato yield and enhance minitubers production in greenhouse with molecular insights,” Scientific Reports, vol. 16, art. 16976, 2026, doi: 10.1038/s41598-026-37163-0. Disponible: https://doi.org/10.1038/s41598-026-37163-0

[28] Comunidad Andina, “Decisión 486: Régimen Común sobre Propiedad Industrial,” 14-sep-2000. Consultado: 30-oct-2026. [En línea]. Disponible: https://www.comunidadandina.org/StaticFiles/DocOf/DEC486.pdf

[29] S. H. Griggs, W. E. Bartley y A. O. Rule III, “Environmental chamber for plant growth analysis,” patente de EE. UU. US5341595A, 30-ago-1994. [En línea]. Disponible: https://patents.google.com/patent/US5341595

[30] D. Liu, “Smart greenhouse environment monitoring and control system,” solicitud de patente de China CN114365649A, 19-abr-2022. Consultado: 30-oct-2026. [En línea]. Disponible: https://patents.google.com/patent/CN114365649A/en

[31] H. Nishiyama et al., “Ammonia sensor,” patente de EE. UU. US7341694B2, 11-mar-2008. [En línea]. Disponible: https://patents.google.com/patent/US7341694B2/en

[32] INDECOPI, “Formulario de solicitud de registro de modelo de utilidad,” jun. 2026. Consultado: 28-oct-2026. [En línea]. Disponible: https://www.gob.pe/institucion/indecopi/informes-publicaciones/1272433-formulario-de-solicitud-de-registro-de-modelo-de-utilidad

[33] INDECOPI, “El Indecopi habilita servicio para que creadores de software registren sus programas a través de la plataforma de Registro Virtual de Obras,” 2024. Consultado: 28-oct-2026. [En línea]. Disponible: https://www.gob.pe/institucion/indecopi/noticias/906591-el-indecopi-habilita-servicio-para-que-creadores-de-software-registren-sus-programas-a-traves-de-la-plataforma-de-registro-virtual-de-obras

[34] Organización Mundial de la Propiedad Intelectual (OMPI), “Período de gracia: disposiciones de las legislaciones nacionales y regionales,” Comité Permanente sobre el Derecho de Patentes. Consultado: 30-oct-2026. [En línea]. Disponible: https://www.wipo.int/documents/d/scp/docs-es-national-laws-grace-period.pdf

[35] Ministerio de Desarrollo Agrario y Riego (MIDAGRI), “Más de 700 mil agricultores de 19 regiones sustentan la producción de papa en el país,” 2025. Consultado: 30-oct-2026. [En línea]. Disponible: https://www.gob.pe/institucion/midagri/noticias/1178150-midagri-mas-de-700-mil-agricultores-de-19-regiones-sustentan-la-produccion-de-papa-en-el-pais

[36] Y.-J. Lee et al., “Comparison of ammonia volatilization in paddy and field soils fertilized with urea and ammonium sulfate during rice, potato, and Chinese cabbage cultivation,” Atmospheric Pollution Research, vol. 15, n.º 4, art. 102049, 2024, doi: 10.1016/j.apr.2024.102049. Disponible: https://doi.org/10.1016/j.apr.2024.102049

[37] P. Rochette et al., “Ammonia volatilization and nitrogen retention: How deep to incorporate urea?,” Journal of Environmental Quality, vol. 42, n.º 6, pp. 1635–1642, 2013, doi: 10.2134/jeq2013.05.0192. Disponible: https://doi.org/10.2134/jeq2013.05.0192

[38] L. Zúñiga, A. Oswald y J. Sánchez, “Efecto de la fertilización orgánica e inorgánica sobre variedades de papas nativas en la sierra central de Perú,” en XXIII Congreso de la Asociación Latinoamericana de la Papa: Memorias, Universidad Nacional de Mar del Plata, Argentina, 2008, pp. 123–124. Consultado: 30-oct-2026. [En línea]. Disponible: https://pgc-snia.inia.gob.pe:8443/jspui/bitstream/inia/784/1/Zu%c3%b1iga-Efecto_fertilizaci%c3%b3n_org%c3%a1nica_inorg%c3%a1nica.pdf

[39] H. A. Cabrera Hoyos y F. Escobal Valencia, Buenas prácticas agrícolas en el cultivo de papa. Cajamarca, Perú: Instituto Nacional de Innovación Agraria, Estación Experimental Agraria Baños del Inca, 2013. Consultado: 30-oct-2026. [En línea]. Disponible: https://pgc-snia.inia.gob.pe:8443/jspui/bitstream/inia/109/1/Cultivo_papa_Cajamarca_2013.pdf

[40] B. Sunderlage y R. L. Cook, “Soil property and fertilizer additive effects on ammonia volatilization from urea,” Soil Science Society of America Journal, vol. 82, n.º 1, pp. 253–259, 2018, doi: 10.2136/sssaj2017.05.0151. Disponible: https://doi.org/10.2136/sssaj2017.05.0151

[41] Y. C. Miguel García, “Efecto de los enraizadores naturales en la producción de tubérculos de papa (Solanum tuberosum L.) prebásica en dos cultivares,” tesis de grado, Facultad de Agronomía, Universidad Nacional del Centro del Perú, Huancayo, Perú, 2025. Consultado: 30-oct-2026. [En línea]. Disponible: https://repositorio.uncp.edu.pe/server/api/core/bitstreams/0a9dd4ea-009f-4b03-aa02-e823a37e3458/content
