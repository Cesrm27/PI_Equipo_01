# GREENPLANT — TRL 3
## Desarrollo experimental o prueba del concepto tecnológico

> **Proyecto:** sistema experimental de laboratorio para el monitoreo de NH₃(g), CO₂(g) y variables ambientales durante ensayos de fertilización con urea en papa (*Solanum tuberosum*), variedad Única.

<div align="center">

| Campo | Información |
|:---:|:---:|
| **Curso** | Proyecto Integrador |
| **Integrantes** | Cesar Rodrigo Milla Gómez; Anderson Josue Delerna Infantes; Kevin Esty Carvallo Neciosup; Shedira Lumeris Sihuincha Palacin |
| **Ingenieros** | Umbert Lewis De La Cruz, Maria Rejas, Harry Rivera y Renzo Chan |
| **Fecha de actualización** | 03/11/2026 |
| **Institución** | Universidad Peruana Cayetano Heredia |
| **Tema** | TRL 3 de GREENPLANT — Prueba de concepto |

</div>

## Contenido

1. [Introducción](#1-introducción)
2. [Ensayos analíticos: simulación estructural en SimScale](#2-ensayos-analíticos-simulación-estructural-en-simscale)
3. [Ensayos experimentales: fundamento químico y pruebas de sensores](#3-ensayos-experimentales-fundamento-químico-y-pruebas-de-sensores)
4. [Demo del prototipo](#4-demo-del-prototipo)
5. [Resultados y discusión](#5-resultados-y-discusión)
6. [Referencias bibliográficas](#referencias-bibliográficas)

---

# 1. Introducción

## 1.1 Qué representa el TRL 3

Mankins describe el TRL 3 como el nivel en el que se realiza una prueba de concepto analítica y experimental de las funciones críticas de una tecnología [[1]](#ref1). Según la definición empleada en el curso, en este nivel se demuestra que los principios básicos previstos en los niveles anteriores sustentan el desarrollo de la tecnología y se comienza a demostrar su viabilidad mediante estudios analíticos y de laboratorio. Para ello se exigen dos evidencias: **datos de ensayos experimentales o analíticos** y un **demo o prototipo** para las primeras pruebas.

## 1.2 Qué se prueba en GREENPLANT

GREENPLANT es una cámara de laboratorio en la que se coloca una maceta con papa y se mide, con cuatro sensores conectados a un microcontrolador ESP32, el gas que se libera después de fertilizar con urea:

- **MQ-137:** amoníaco gaseoso (NH₃), la variable principal.
- **MH-Z19B:** dióxido de carbono (CO₂), la variable complementaria.
- **BME280:** temperatura, humedad relativa y presión del aire.
- **Sensor capacitivo de humedad de tierra v1.2:** humedad del sustrato.

En el TRL 3 se pone a prueba este concepto con tres evidencias, una por sección:

1. **Ensayo analítico (sección 2):** simulación estructural en SimScale para comprobar que la cámara de PETG soporta el peso de la maceta.
2. **Ensayos experimentales (sección 3):** las reacciones químicas que el sistema debe registrar, las fórmulas con las que el ESP32 convierte las señales en datos y las pruebas de cada sensor con sus valores de referencia.
3. **Demo del prototipo (sección 4):** el montaje de los cuatro sensores con el ESP32 en una protoboard.

---

# 2. Ensayos analíticos: simulación estructural en SimScale

## 2.1 Objetivo, carga y criterio de aceptación

**Objetivo.** Comprobar que las piezas de la cámara, impresas en PETG, soportan el peso de la maceta sin deformarse de forma permanente ni romperse.

**Carga.** La cámara del TRL 2 se diseñó para una maceta de 1,9 L de sustrato. Sumando la maceta, el sustrato húmedo y la planta, el equipo adoptó una carga útil de 3 kg, redondeada hacia arriba para trabajar con margen. Su peso es:

$$
F = m \cdot g = 3\ \text{kg} \times 9{,}81\ \text{m/s}^2 \approx 29{,}4\ \text{N}
$$

**Criterio de aceptación.** El esfuerzo de Von Mises reúne en un solo valor los esfuerzos que actúan sobre un punto en todas las direcciones. Según el criterio de la energía de distorsión, un material dúctil no fluye mientras ese valor sea menor que su esfuerzo de fluencia, que es el esfuerzo a partir del cual el material empieza a deformarse de forma permanente [[2]](#ref2). Por eso, el esfuerzo máximo de Von Mises debe quedar muy por debajo del esfuerzo de fluencia del PETG. Se tomó un esfuerzo de fluencia de **25 MPa**, de la ficha técnica de Spectrum Filaments, medido según ASTM D638 [[3]](#ref3). Es la misma ficha de la que provienen el módulo de Young y la densidad del modelo (sección 2.3), y su valor es menor que la resistencia a la rotura del mismo material (46,9 MPa), lo que hace al criterio conservador.

## 2.2 Estudios realizados

Se prepararon dos estudios en SimScale. El primero, más simple, ya se resolvió y da el resultado de este informe. El segundo es más completo y está configurado, pero aún no se resuelve porque su malla debe corregirse (Tabla 1).

<p align="center"><em>Tabla 1. Estudios de simulación estructural realizados en SimScale.</em></p>

<div align="center">

| Estudio | Tipo de análisis | Piezas | Estado | Figuras |
|:---:|:---:|:---:|:---:|:---:|
| «Proyecto Integrador» | Dinámico | Soporte/planta (cuatro sólidos del modelo) | Resuelto: tres corridas completadas | Figura 3 |
| «GREENPLANT_Analisis_Estructural» | Estático | Base y soporte/planta | Configurado; malla por corregir | Figuras 1 y 2 |

</div>

## 2.3 Estudio estático: material, malla y condiciones de contorno

**Por qué un análisis estático.** En SimScale, el análisis estático calcula desplazamientos, deformaciones y esfuerzos que no dependen del tiempo, a partir de las restricciones y las cargas aplicadas, sin considerar efectos de inercia [[4]](#ref4). Como la maceta es una carga que permanece apoyada sobre la cámara durante todo el ensayo, sin golpes ni vibraciones, este es el análisis adecuado para la verificación definitiva. El modelo incluye dos sólidos, la base y el soporte/planta, unidos mediante dos contactos que representan el apoyo de una pieza sobre la otra (Figura 1).

**Material.** Ambas piezas se modelaron con el material «PETG – valores preliminares» (Tabla 2).

<p align="center"><em>Tabla 2. Propiedades del PETG asignadas en SimScale.</em></p>

<div align="center">

| Propiedad | Valor en SimScale | Fuente o justificación |
|:---:|:---:|:---:|
| Comportamiento | Lineal elástico | Este modelo es válido cuando las deformaciones son pequeñas y el esfuerzo no supera la fluencia [[5]](#ref5); el esfuerzo obtenido (0,108 MPa, sección 2.4) es mucho menor que la fluencia (25 MPa) |
| Dependencia direccional | Isótropo | El modelo supone propiedades iguales en todas las direcciones [[5]](#ref5); es una simplificación, porque en el PETG impreso por capas la resistencia a la tracción es la propiedad que más cambia con la orientación [[6]](#ref6) |
| Módulo de Young (E) | 1,874 × 10⁹ Pa (1874 MPa) | Módulo de tracción, ASTM D638 [[3]](#ref3) |
| Densidad (ρ) | 1270 kg/m³ | Peso específico de 1,27 g/cm³, ASTM D792 [[3]](#ref3) |
| Coeficiente de Poisson (ν) | 0,38 | Valor preliminar: no figura en la ficha técnica y se reemplazará por un valor medido o publicado |

</div>

El nombre «valores preliminares» indica precisamente que el coeficiente de Poisson todavía debe confirmarse antes de dar por definitivos los resultados de este estudio.

<p align="center">
<img width="900" alt="Figura 1. Propiedades del material PETG en el análisis estático de SimScale" src="https://github.com/user-attachments/assets/2e9a7c0b-c470-4f4b-b747-dbe84d3b418a" />
</p>
<p align="center"><em>Figura 1. Configuración del análisis estático «GREENPLANT_Analisis_Estructural»: material «PETG – valores preliminares» (lineal elástico e isótropo, E = 1,874 × 10⁹ Pa, ν = 0,38 y ρ = 1270 kg/m³) asignado a la base y al soporte/planta.</em></p>

**Malla y condiciones de contorno.** La Figura 2 muestra la malla del mismo estudio. Los números de la figura señalan:

1. **Condiciones de contorno:** un apoyo deslizante y una restricción anti-deslizamiento, que representan la mesa sobre la que descansa la cámara; una restricción anti-giro en el eje Z en los agujeros de fijación, que representa los tornillos; y la carga útil de 3 kg sobre la superficie donde se apoya la maceta.
2. **Refinamientos de malla:** la malla se hizo más fina en la zona de contacto entre piezas, en los agujeros de fijación, en la placa de carga y en los recortes y bordes, que es donde se esperan los mayores esfuerzos.
3. **Modelo:** la base, con sus aberturas y el saliente frontal, y el soporte/planta.
4. **Relación de aspecto:** la leyenda indica que los elementos de la malla tienen una relación de aspecto entre 1 y 1,374 × 10⁴.
5. **Estado:** la malla («Mesh 3») se generó, pero la corrida de este estudio todavía no se ha ejecutado.

<p align="center">
<img width="700" alt="Figura 2. Malla y condiciones de contorno del análisis estático en SimScale" src="https://github.com/user-attachments/assets/b7ae0bdf-5310-4cc0-b222-8c9606fd68bf" />
</p>
<p align="center"><em>Figura 2. Malla del estudio «GREENPLANT_Analisis_Estructural»: (1) condiciones de contorno, (2) refinamientos de malla, (3) modelo de la base y el soporte/planta, (4) leyenda de la relación de aspecto y (5) estado de la malla y de las corridas.</em></p>

**Por qué aún no se ejecuta.** La relación de aspecto es el cociente entre la longitud mayor y la menor de un elemento de la malla. SimScale indica que, en mallas tetraédricas para análisis estructural, un valor mayor que 16 hace muy probable que la simulación no converja [[7]](#ref7). El valor máximo de esta malla, 1,374 × 10⁴, supera ampliamente ese límite. Estos elementos tan alargados suelen aparecer en detalles muy delgados, como el relieve del texto «GREENPLANT» o los rebordes finos. Por eso, antes de resolver el estudio se simplificarán esos detalles o se refinará la malla en ellos hasta que la relación de aspecto máxima quede por debajo de 16.

## 2.4 Estudio dinámico: resultados

El estudio «Proyecto Integrador» es un análisis dinámico, es decir, uno que sí considera los efectos de inercia de la carga [[4]](#ref4), y se resolvió con tres corridas (Figura 3). Los números de la figura señalan:

1. **Cargas:** las dos fuerzas aplicadas sobre el modelo (Force 1 y Force 2).
2. **Corridas:** Run 1, Run 2 y Run 3, todas completadas. El resultado mostrado corresponde a Run 3.
3. **Pasos de tiempo:** la corrida tiene 11 pasos, desde 0 hasta 0,01 s.
4. **Resultado:** la distribución del esfuerzo sobre los cuatro sólidos del modelo (Part 1 a Part 4).
5. **Leyenda:** el esfuerzo de Von Mises va de 0 a 1,082 × 10⁵ Pa.

<p align="center">
<img width="700" alt="Figura 3. Esfuerzo de Von Mises en el estudio dinámico de SimScale" src="https://github.com/user-attachments/assets/1f8eb009-4290-4cc7-8dc7-39e1c5a59bd9" />
</p>
<p align="center"><em>Figura 3. Estudio «Proyecto Integrador»: (1) fuerzas aplicadas, (2) corridas de simulación, (3) pasos de tiempo, (4) distribución del esfuerzo en la cámara y (5) leyenda del esfuerzo de Von Mises.</em></p>

**Interpretación.** Casi toda la cámara aparece en azul, es decir, con esfuerzos cercanos a cero. Los valores más altos, en verde y amarillo, se concentran en el centro de la pared interior, que es la zona que más se flexiona. El esfuerzo máximo es de 1,082 × 10⁵ Pa, es decir, 0,108 MPa. Frente al esfuerzo de fluencia del PETG, el factor de seguridad es:

$$
FS = \frac{\sigma_{\text{fluencia}}}{\sigma_{\text{máx}}} = \frac{25\ \text{MPa}}{0{,}108\ \text{MPa}} \approx 231
$$

El factor de seguridad es el cociente entre la resistencia del material y el esfuerzo al que está sometido [[2]](#ref2). Un valor de 231 significa que la cámara soportaría una carga unas 231 veces mayor que la simulada antes de empezar a deformarse de forma permanente.

**Alcance del resultado.** El factor de seguridad debe leerse como una indicación de que la estructura es adecuada, no como un valor exacto, por tres razones. Primero, el fabricante advierte que los valores de su ficha son de referencia y no especificaciones de diseño [[3]](#ref3). Segundo, una pieza impresa con relleno parcial y por capas resiste menos que una probeta de ensayo, sobre todo cuando la carga separa las capas [[6]](#ref6). Tercero, la corrida dinámica dura solo 0,01 s y no representa una carga mantenida durante días. El margen es tan amplio que estas diferencias no cambian la conclusión, y el estudio estático de la sección 2.3 la confirmará una vez corregida su malla.

---

# 3. Ensayos experimentales: fundamento químico y pruebas de sensores

## 3.1 Reacciones químicas que registra GREENPLANT

Cuando la urea se aplica al sustrato húmedo, la enzima ureasa la descompone. La reacción produce carbonato de amonio, consume iones hidrógeno y eleva el pH alrededor del gránulo de fertilizante [[8]](#ref8). El proceso se resume en tres etapas:

1. **Hidrólisis de la urea:** la urea reacciona con el agua del sustrato y forma carbonato de amonio [[8]](#ref8).

$$
\text{CO(NH}_2\text{)}_2\,(\text{aq}) + 2\,\text{H}_2\text{O}\,(\text{l}) \longrightarrow (\text{NH}_4)_2\text{CO}_3\,(\text{aq}) \qquad (1)
$$

2. **Formación de dióxido de carbono:** en condiciones adecuadas, el carbono inorgánico derivado de la hidrólisis puede formar CO₂(g); la ecuación siguiente es una representación simplificada de una posible vía de acidificación, no una afirmación de que todo el carbono se libera como gas [[8]](#ref8), [[9]](#ref9).

$$
(\text{NH}_4)_2\text{CO}_3\,(\text{aq}) + 2\,\text{H}^+\,(\text{aq}) \longrightarrow 2\,\text{NH}_4^+\,(\text{aq}) + \text{CO}_2\,(\text{g}) + \text{H}_2\text{O}\,(\text{l}) \qquad (2)
$$

3. **Equilibrio entre amonio y amoníaco:** según el pH y la temperatura, el ion amonio acuoso, NH₄⁺(aq), puede estar en equilibrio con amoníaco, NH₃(aq), y este puede transferirse a la fase gaseosa como NH₃(g), que es lo que mide el MQ-137 [[8]](#ref8).

$$
\text{NH}_4^+\,(\text{aq}) + \text{OH}^-\,(\text{aq}) \rightleftharpoons \text{NH}_3\,(\text{aq}) + \text{H}_2\text{O}\,(\text{l}) \rightleftharpoons \text{NH}_3\,(\text{g}) + \text{H}_2\text{O}\,(\text{l}) \qquad (3)
$$

**Factores que controlan el proceso.** El equilibrio de la ecuación (3) depende del pH: la fracción del nitrógeno amoniacal presente como NH₃ pasa de 0,058 % a pH 6 a 36,5 % a pH 9 [[8]](#ref8). La temperatura también influye, porque un sustrato más cálido acelera la actividad de la ureasa y aumenta el amoníaco disuelto [[8]](#ref8).

**Contenido de nitrógeno de la urea.** Por su fórmula química, CO(NH₂)₂, la urea contiene 46,6 % de nitrógeno en masa:

$$
\%\text{N} = \frac{2 \times 14{,}01\ \text{g/mol}}{60{,}06\ \text{g/mol}} \times 100 \approx 46{,}6\ \%
$$

Este valor permite convertir la dosis de nitrógeno de cada tratamiento en la masa de urea que se aplica a cada maceta.

## 3.2 Qué sensor registra cada parte del proceso

Cada sensor mide una variable que aparece en las ecuaciones (1) a (3) o que las controla:

- **MQ-137:** mide el NH₃(g) de la ecuación (3), la variable principal del estudio.
- **MH-Z19B:** mide el CO₂(g). Una parte proviene de la ecuación (2), pero otra parte proviene de la respiración de las raíces, de los microorganismos y de la descomposición de la materia orgánica del sustrato [[9]](#ref9), por lo que su lectura no se atribuye solo a la urea.
- **BME280:** mide la temperatura, que acelera la hidrólisis y desplaza el equilibrio de la ecuación (3) [[8]](#ref8), y la humedad relativa, que altera la respuesta de los sensores de óxido metálico como el MQ-137 [[10]](#ref10).
- **Sensor capacitivo de humedad de tierra v1.2:** mide el agua del sustrato, que es un reactivo de la ecuación (1) [[8]](#ref8).

## 3.3 Conversión de las señales en datos

El ESP32 recibe dos tipos de señales:

- **Señales digitales:** el BME280 y el MH-Z19B entregan sus valores ya calculados, por I²C [[11]](#ref11) y por UART [[12]](#ref12), respectivamente.
- **Señales analógicas:** el MQ-137 y el sensor capacitivo entregan una tensión. El convertidor analógico-digital del ESP32 la transforma en un número entero entre 0 y 4095 (12 bits) [[13]](#ref13), que se convierte en tensión con la siguiente relación:

$$
V = \frac{\text{lectura}}{4095} \times V_{\text{máx}}
$$

donde $V_{\text{máx}}$ es la tensión máxima de la escala configurada. Con la atenuación de 11 dB, Espressif recomienda medir entre 150 y 2450 mV, porque fuera de ese intervalo la conversión es menos precisa [[13]](#ref13).

**Protección de las entradas del ESP32.** El circuito del MQ-137 funciona con 5 V [[14]](#ref14), mientras que el ESP32 funciona a 3,3 V y sus entradas no deben recibir una tensión mayor que la de su alimentación [[15]](#ref15). Por eso, antes de conectar la salida analógica del MQ-137 se comprueba con un multímetro que no supere ese valor; si lo supera, se intercala un divisor de tensión y la tensión leída se multiplica por el factor del divisor para recuperar el valor real.

**Resistencia del MQ-137.** El sensor forma un divisor de tensión con una resistencia de carga $R_L$, alimentado con una tensión $V_C$ de 5 V [[14]](#ref14). Aplicando la ley de Ohm a ese divisor, a partir de la tensión medida en la resistencia de carga, $V_{RL}$, se calcula la resistencia del sensor:

$$
R_S = R_L \times \frac{V_C - V_{RL}}{V_{RL}}
$$

El valor de $R_L$ corresponde a la resistencia de carga del módulo y se mide con un multímetro antes de la calibración. La concentración de NH₃ se obtiene a partir del cociente $R_S/R_0$, donde $R_0$ es la resistencia del sensor en aire limpio. La relación entre ese cociente y la concentración se determina calibrando el sensor frente a concentraciones conocidas de NH₃, como hicieron Petric et al. con el mismo modelo [[16]](#ref16).

**Conversión entre ppm y mg/m³.** Para relacionar la lectura del MQ-137 con la masa de nitrógeno aplicada, la concentración se expresa en masa por volumen, con la relación que emplea NIOSH, basada en la masa molar del gas (17,03 g/mol para el NH₃) y en el volumen molar del aire a 25 °C y 1 atm (24,45 L/mol) [[17]](#ref17):

$$
C_{\text{mg/m}^3} = C_{\text{ppm}} \times \frac{17{,}03}{24{,}45}
$$

## 3.4 Procedimiento de las pruebas

Las pruebas se realizaron con el prototipo en protoboard de la sección 4. Cada sensor siguió un procedimiento propio:

1. **MH-Z19B:** se encendió al aire libre, se esperó su precalentamiento de 3 minutos [[12]](#ref12) y se registró la lectura durante 5 minutos. Othman et al. validaron este mismo modelo frente a un equipo de referencia en una cámara de calibración [[18]](#ref18).
2. **BME280:** se registraron la temperatura, la humedad relativa y la presión del aire del laboratorio.
3. **Sensor capacitivo v1.2:** se insertó en el sustrato y se registró la humedad que indica. Para convertir esa lectura en contenido real de agua se usa como referencia el método gravimétrico normalizado, que obtiene el agua pesando la muestra antes y después de secarla en estufa [[19]](#ref19), y la señal se relaciona con ese contenido como en el trabajo de Placidi et al. [[20]](#ref20).
4. **MQ-137:** se registró su lectura en aire limpio, que sirve como punto de partida ($R_0$) de la fórmula de la sección 3.3. El fabricante exige un precalentamiento de más de 48 horas antes de usarlo [[14]](#ref14), y la calibración frente a concentraciones conocidas de NH₃ se realiza después [[16]](#ref16).

## 3.5 Valores de referencia y criterio de aceptación

Cada lectura se compara con un valor de referencia tomado de la bibliografía o de la hoja de datos del fabricante (Tabla 3). Estos valores son los que el sensor debería mostrar si funciona bien, y sirven como criterio para aceptar o rechazar cada prueba.

<p align="center"><em>Tabla 3. Valores de referencia y márgenes de aceptación de cada prueba.</em></p>

<div align="center">

| Sensor | Prueba | Valor de referencia | Margen aceptable | Fuente |
|:---:|:---:|:---:|:---:|:---:|
| MH-Z19B | CO₂ en aire exterior | 426,1 ppm (promedio mundial, julio de 2026) | ± (50 ppm + 5 % de la lectura) | NOAA [[21]](#ref21); fabricante [[12]](#ref12) |
| BME280 | Temperatura | Lectura de un termómetro de referencia | ± 1,0 °C (entre 0 y 65 °C) | Bosch [[11]](#ref11) |
| BME280 | Humedad relativa | Lectura de un higrómetro de referencia | ± 3 % HR | Bosch [[11]](#ref11) |
| BME280 | Presión atmosférica | Presión local del día: 1014 hPa | ± 1,0 hPa | Bosch [[11]](#ref11) |
| Sensor capacitivo v1.2 | Humedad del sustrato | Contenido de agua por pesaje: 34,2 % | Diferencia menor que el error típico de este tipo de sensor | ASTM [[19]](#ref19); Placidi et al. [[20]](#ref20) |
| MQ-137 | NH₃ en aire limpio | Por debajo de 5 ppm, el límite inferior del sensor | Lectura estable, que se usa como R₀ | Fabricante [[14]](#ref14) |

</div>

**Cálculo del error.** Para cada prueba se calcula el error porcentual entre la lectura y el valor de referencia:

$$
\text{Error (\%)} = \frac{\left|\text{valor medido} - \text{valor de referencia}\right|}{\text{valor de referencia}} \times 100
$$

La prueba se acepta si la diferencia queda dentro del margen de la Tabla 3.

**Por qué el CO₂ se mide al aire libre.** El valor de 426,1 ppm de la NOAA corresponde al aire de fondo del planeta [[21]](#ref21). En exteriores, el CO₂ suele estar entre unos 380 y 500 ppm, mientras que en interiores la concentración promedio tiende a ser mayor porque los ocupantes exhalan CO₂ [[22]](#ref22).

**Relación entre presión y altitud.** La presión del aire disminuye a medida que aumenta la altitud. La Atmósfera Estándar de EE. UU. de 1976 describe esa relación con la siguiente fórmula, donde *P*₀ es la presión al nivel del mar y *h* la altitud en metros [[23]](#ref23):

$$
P = P_0 \times \left(1 - \frac{h}{44\,330{,}77}\right)^{5{,}256}
$$

Cerca del nivel del mar, la fórmula indica que la presión baja aproximadamente 1 hPa por cada 8 m de subida. Esta relación se usa en la sección 3.6 para interpretar la diferencia entre el BME280 y la presión local del día.

**Por qué el MQ-137 se prueba en aire limpio.** En aire limpio no hay amoníaco suficiente para que el sensor lo detecte, por lo que la lectura esperada queda por debajo de su límite inferior de 5 ppm [[14]](#ref14). Esa lectura no se compara con un número exacto, sino que se usa como punto de partida ($R_0$). La concentración que se espera dentro de la cámara después de fertilizar, de 13 a 105 ppm según la estimación del TRL 2 [[24]](#ref24), [[25]](#ref25), se comprobará en los ensayos con macetas.

## 3.6 Resultados de las pruebas

La Tabla 4 presenta las lecturas obtenidas y su comparación con los valores de referencia.

<p align="center"><em>Tabla 4. Resultados de las pruebas iniciales de los sensores.</em></p>

<div align="center">

| Sensor | Variable | Valor medido | Valor de referencia | Diferencia | Resultado |
|:---:|:---:|:---:|:---:|:---:|:---:|
| MH-Z19B | CO₂ en aire exterior | 450 ppm | 426,1 ppm | +23,9 ppm (5,6 %) | Aceptado: dentro del margen de ± 72,5 ppm |
| BME280 | Temperatura | 26 °C | Termómetro de referencia | — | Pendiente: falta la lectura de referencia |
| BME280 | Humedad relativa | 45 % | Higrómetro de referencia | — | Pendiente: falta la lectura de referencia |
| BME280 | Presión atmosférica | 1010 hPa | 1014 hPa | −4 hPa (0,39 %) | Fuera de ± 1,0 hPa; explicable por la altitud |
| Sensor capacitivo v1.2 | Humedad del sustrato | 35 % | 34,2 % | +0,8 puntos (2,3 %) | Aceptado |
| MQ-137 | NH₃ en aire limpio | 1,0 ppm | Menor que 5 ppm | Por debajo del límite | Aceptado como línea de base |

</div>

Para cada sensor se explica primero por qué se obtuvo ese valor, según el principio con el que mide, y después se compara con el valor que se esperaba.

### 3.6.1 MH-Z19B: CO₂ del aire exterior

**Por qué se obtuvo 450 ppm.** El MH-Z19B es un sensor infrarrojo no dispersivo (NDIR): emite luz infrarroja a través de una cámara con aire y mide cuánta absorbe el CO₂, que es proporcional a su concentración [[12]](#ref12). Al aire libre, la lectura refleja el CO₂ de fondo del planeta más el aporte de las fuentes cercanas. El valor de 426,1 ppm de la NOAA es un promedio global medido en sitios alejados de ciudades [[21]](#ref21); en zonas urbanas, el tránsito, la combustión y las personas cercanas elevan la concentración local, que en exteriores suele estar entre 380 y 500 ppm [[22]](#ref22). Una lectura algo mayor que el promedio global es, por tanto, lo esperado en un campus urbano.

**Comparación con el valor esperado.** La lectura difiere en +23,9 ppm del promedio global, un error de 5,6 %. Para una lectura de 450 ppm, el margen del fabricante es de ± (50 + 0,05 × 450) = ± 72,5 ppm [[12]](#ref12). Como la diferencia es menor que ese margen y el valor está dentro del intervalo típico del aire exterior, la prueba se acepta.

### 3.6.2 BME280: temperatura y humedad relativa

**Por qué se obtuvieron 26 °C y 45 %.** Ambos valores están dentro del rango de operación del sensor. Según Bosch, la temperatura que entrega el BME280 depende no solo del aire, sino también de la temperatura de la placa y del autocalentamiento del propio sensor [[11]](#ref11). En el prototipo, el módulo está cerca del ESP32 y del MQ-137, cuyo calentador funciona de forma continua [[14]](#ref14), por lo que la temperatura medida puede quedar algo por encima de la del aire del laboratorio. Además, la humedad relativa depende de la temperatura: con la misma cantidad de vapor, una temperatura mayor da una humedad relativa menor. Para reducir este efecto se alejará el BME280 de las fuentes de calor y se usará el modo forzado, que Bosch recomienda cuando se mide con poca frecuencia [[11]](#ref11).

**Comparación con el valor esperado.** Estos dos valores no pueden aceptarse ni rechazarse todavía, porque no se registró la lectura simultánea de un termómetro y un higrómetro de referencia. Con ella, la prueba se aceptará si la diferencia no supera ± 1,0 °C y ± 3 % HR [[11]](#ref11).

### 3.6.3 BME280: presión atmosférica

**Por qué se obtuvo 1010 hPa.** El BME280 es un sensor de presión barométrica absoluta: mide la presión real del aire en el lugar donde se encuentra [[11]](#ref11). En cambio, los servicios meteorológicos no publican la presión de cada lugar, sino la presión «reducida al nivel del mar», que corrige la medición como si la estación estuviera a 0 m de altitud. Así se pueden comparar estaciones situadas a distintas alturas, pero el valor publicado es mayor que la presión real de cualquier lugar elevado [[26]](#ref26). El BME280 no hace esa corrección, por lo que su lectura debe ser menor que la presión reportada.

**Comparación con el valor esperado.** La lectura de 1010 hPa es 4 hPa menor que la presión local del día, de 1014 hPa, un error de 0,39 %. La diferencia supera la exactitud de ± 1,0 hPa del sensor [[11]](#ref11), pero su sentido es el esperado: si los 1014 hPa son la presión reducida al nivel del mar, la fórmula de la sección 3.5 indica que una diferencia de 4 hPa corresponde a unos 33 m de altitud [[23]](#ref23). Por tanto, si el laboratorio se encuentra cerca de esa altitud, la diferencia se explica por la altura y no por un error del sensor. Una segunda causa posible es la soldadura del sensor al módulo, que según Bosch puede desplazar la lectura de presión entre −0,5 y +2,0 hPa [[11]](#ref11). Para confirmarlo se usará la altitud exacta del laboratorio: con ella se calcula la presión que corresponde a ese lugar, y la prueba se acepta si la lectura queda a ± 1,0 hPa de ese valor.

### 3.6.4 Sensor capacitivo v1.2: humedad del sustrato

**Por qué se obtuvo 35 %.** El sensor funciona como un condensador cuyas placas están dentro del sustrato. La capacidad del condensador depende de la constante dieléctrica del material que lo rodea: la del agua es cercana a 80, mientras que la del suelo seco está entre 3 y 5 [[27]](#ref27). Por eso, cuanto más agua tiene el sustrato, mayor es la capacidad y menor la tensión que entrega el sensor. El programa transforma esa tensión en un porcentaje, interpolando entre la lectura del sensor en aire (sustrato seco) y en agua (sustrato saturado) [[20]](#ref20).

**Comparación con el valor esperado.** El contenido de agua por pesaje, obtenido con el método gravimétrico de la norma ASTM D2216 [[19]](#ref19), fue de 34,2 %. La lectura del sensor difiere en +0,8 puntos porcentuales, un error relativo de 2,3 %. Como referencia, Nagahage et al. compararon un sensor capacitivo de bajo costo similar con el método gravimétrico y obtuvieron un error cuadrático medio de 0,09 cm³/cm³, es decir, unos 9 puntos porcentuales [[28]](#ref28). La diferencia obtenida es mucho menor, por lo que la prueba se acepta. Sin embargo, la coincidencia se comprobó en un solo punto; para usar el sensor en los ensayos se repetirá la comparación con varios contenidos de agua y se obtendrá la curva de calibración propia del sustrato, como recomiendan Placidi et al. [[20]](#ref20).

### 3.6.5 MQ-137: NH₃ en aire limpio

**Por qué se obtuvo 1,0 ppm.** En el aire exterior, el NH₃ se encuentra normalmente entre 0,3 y 6 ppb [[29]](#ref29), es decir, entre unas 170 y 3300 veces menos que la lectura de 1,0 ppm. Por tanto, ese valor no corresponde a amoníaco real, sino a la señal de base del sensor. El MQ-137 mide porque su capa sensible cambia de resistencia al reaccionar con el gas, y esa resistencia también varía con la temperatura y la humedad del aire [[14]](#ref14), [[10]](#ref10). Además, la capa responde a otros gases, como las aminas orgánicas, y su señal solo se estabiliza después del precalentamiento de más de 48 horas que exige el fabricante [[14]](#ref14). Finalmente, la fórmula que transforma $R_S/R_0$ en ppm se ajusta con concentraciones conocidas de NH₃ [[16]](#ref16); aplicada por debajo de 5 ppm, fuera del intervalo del sensor, produce un número pequeño, pero sin significado físico.

**Comparación con el valor esperado.** Lo esperado en aire limpio era una lectura menor que el límite inferior de 5 ppm del sensor [[14]](#ref14), y la lectura de 1,0 ppm cumple esa condición. La prueba se acepta como línea de base: el sensor responde de forma estable y esa lectura sirve para fijar $R_0$. La concentración que se espera dentro de la cámara después de fertilizar, de 13 a 105 ppm [[24]](#ref24), [[25]](#ref25), sí está dentro del intervalo de medición, y se verificará en los ensayos con macetas.

---

# 4. Demo del prototipo

La Figura 4 muestra el primer prototipo funcional de GREENPLANT: los cuatro sensores conectados a un ESP32 sobre una protoboard y alimentados por USB. La placa PCB3 diseñada en el TRL 2 todavía no se ha fabricado; la protoboard permite probar las conexiones y el programa antes de pasar a la placa definitiva.

<p align="center">
<img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/df3b0659-fddb-437e-8a87-a0ebe7662c99" />
</p>
<p align="center"><em>Figura 4. Prototipo de GREENPLANT en protoboard: ESP32 con los sensores BME280, MQ-137, MH-Z19B y el sensor capacitivo de humedad de tierra v1.2.</em></p>

En la figura se identifican los cinco componentes:

- **ESP32:** recibe las señales de los cuatro sensores y se alimenta por el cable USB.
- **MQ-137:** el LED rojo encendido del módulo indica que está energizado.
- **MH-Z19B:** sensor de CO₂ por absorción infrarroja no dispersiva (NDIR); su etiqueta indica el rango de 0 a 5000 ppm, una de las configuraciones que ofrece el fabricante [[12]](#ref12).
- **BME280:** módulo de temperatura, humedad y presión conectado por I²C [[11]](#ref11).
- **Sensor capacitivo v1.2:** conectado por su cable de tres hilos, listo para insertarse en el sustrato.

Este montaje demuestra que los cuatro sensores pueden conectarse y alimentarse al mismo tiempo desde un solo ESP32, que es la función central del concepto formulado en el TRL 2.

---

# 5. Resultados y discusión

**Estructura.** El estudio dinámico (Figura 3) muestra un esfuerzo máximo de 0,108 MPa y un factor de seguridad cercano a 231 frente al esfuerzo de fluencia del PETG [[3]](#ref3). Por tanto, el diseño de la cámara en PETG es adecuado para la carga prevista. El estudio estático (Figuras 1 y 2), que incluye también la base, confirmará este resultado una vez que su malla cumpla el límite de relación de aspecto recomendado por SimScale [[7]](#ref7).

**Fundamento químico.** Las ecuaciones (1) a (3) muestran que el NH₃(g) que mide el MQ-137 proviene de la hidrólisis de la urea y del equilibrio entre amonio y amoníaco, y que el proceso depende del agua del sustrato y de la temperatura, que registran el sensor capacitivo y el BME280 [[8]](#ref8). Así, los cuatro sensores cubren tanto el producto principal de la reacción como las condiciones que lo controlan.

**Instrumentación.** El prototipo de la Figura 4 demuestra que los cuatro sensores funcionan integrados en un mismo montaje. En las pruebas iniciales (Tabla 4), tres resultados se aceptan: el MH-Z19B midió el CO₂ del aire exterior dentro del margen del fabricante; el sensor capacitivo coincidió con el contenido de agua por pesaje, con una diferencia de 0,8 puntos; y el MQ-137 entregó una línea de base por debajo de su límite de detección, como se esperaba en aire limpio. La presión del BME280 fue 4 hPa menor que la presión local del día, una diferencia que corresponde a unos 33 m de altitud y que se confirmará con la altitud exacta del laboratorio. Para completar la verificación faltan la comparación de la temperatura y la humedad con instrumentos de referencia, la curva de calibración del sensor capacitivo con varios contenidos de agua y la calibración del MQ-137 con concentraciones conocidas de NH₃.

---

# Referencias bibliográficas

<a id="ref1"></a>[1] J. C. Mankins, “Technology readiness assessments: A retrospective,” Acta Astronautica, vol. 65, n.os 9–10, pp. 1216–1223, 2009, doi: 10.1016/j.actaastro.2009.03.058. Disponible: https://doi.org/10.1016/j.actaastro.2009.03.058

<a id="ref2"></a>[2] R. G. Budynas y J. K. Nisbett, Shigley’s Mechanical Engineering Design, 11.ª ed. Nueva York, NY, EE. UU.: McGraw-Hill Education, 2020.

<a id="ref3"></a>[3] Spectrum Group Sp. z o.o., “Technical data sheet: The Filament PETG,” 23-sep-2024. Consultado: 03-nov-2026. [En línea]. Disponible: https://spectrumfilaments.com/wp-content/uploads/2024/11/eng_tds_the_filament_petg.pdf

<a id="ref4"></a>[4] SimScale, “Static analysis,” SimScale Documentation. Consultado: 03-nov-2026. [En línea]. Disponible: https://www.simscale.com/docs/analysis-types/static/

<a id="ref5"></a>[5] SimScale, “Linear elastic materials,” SimScale Documentation. Consultado: 03-nov-2026. [En línea]. Disponible: https://www.simscale.com/docs/simulation-setup/materials/linear-elastic-materials/

<a id="ref6"></a>[6] J. K. Azcaray, D. Gomez-Lendinez, S. Tarancón, E. Tejado y M. Braun, “Anisotropy and defect tolerance of FFF-manufactured PETG: A combined tensile, compressive and mode I fracture study,” Applied Sciences, vol. 16, n.º 19, art. 9401, 2026, doi: 10.3390/app16199401. Disponible: https://doi.org/10.3390/app16199401

<a id="ref7"></a>[7] SimScale, “Mesh quality,” SimScale Documentation. Consultado: 03-nov-2026. [En línea]. Disponible: https://www.simscale.com/docs/simulation-setup/meshing/mesh-quality/

<a id="ref8"></a>[8] N. Rayne y C. Bandura, “Ammonia loss from urea-containing fertilizers,” University of Wisconsin–Madison Division of Extension, Crops and Soils. Consultado: 30-oct-2026. [En línea]. Disponible: https://cropsandsoils.extension.wisc.edu/articles/ammonia-loss-from-urea-containing-fertilizers/

<a id="ref9"></a>[9] Y. Kuzyakov, “Sources of CO₂ efflux from soil and review of partitioning methods,” Soil Biology and Biochemistry, vol. 38, n.º 3, pp. 425–448, 2006, doi: 10.1016/j.soilbio.2005.08.020. Disponible: https://doi.org/10.1016/j.soilbio.2005.08.020

<a id="ref10"></a>[10] R. Huerta, T. S. Mosqueiro, J. Fonollosa, N. F. Rulkov e I. Rodriguez-Lujan, “Online decorrelation of humidity and temperature in chemical sensors for continuous monitoring,” Chemometrics and Intelligent Laboratory Systems, vol. 157, pp. 169–176, 2016, doi: 10.1016/j.chemolab.2016.07.004. Disponible: https://doi.org/10.1016/j.chemolab.2016.07.004

<a id="ref11"></a>[11] Bosch Sensortec, “BME280: Data sheet,” rev. 1.24, feb. 2024. Consultado: 28-oct-2026. [En línea]. Disponible: https://www.bosch-sensortec.com/media/boschsensortec/downloads/datasheets/bst-bme280-ds002.pdf

<a id="ref12"></a>[12] Zhengzhou Winsen Electronics Technology Co., Ltd., “Infrared CO₂ sensor module (model: MH-Z19B): User’s manual,” ver. 1.6, 23-abr-2020. Consultado: 03-nov-2026. [En línea]. Disponible: https://www.winsen-sensor.com/d/files/infrared-gas-sensor/ndir-co2-sensor/mh-z19b-co2-manual(ver1_6).pdf

<a id="ref13"></a>[13] Espressif Systems, “Analog to Digital Converter,” ESP-IDF Programming Guide, v3.1.6. Consultado: 30-oct-2026. [En línea]. Disponible: https://docs.espressif.com/projects/esp-idf/en/v3.1.6/api-reference/peripherals/adc.html

<a id="ref14"></a>[14] Zhengzhou Winsen Electronics Technology Co., Ltd., “Ammonia gas sensor (model: MQ137): Manual,” ver. 1.6, jul. 2021. Consultado: 30-oct-2026. [En línea]. Disponible: https://www.winsen-sensor.com/d/files/manual/mq137.pdf

<a id="ref15"></a>[15] Espressif Systems, “ESP32 series datasheet,” ver. 5.3. Consultado: 28-oct-2026. [En línea]. Disponible: https://documentation.espressif.com/esp32_datasheet_en.html

<a id="ref16"></a>[16] M. Petric, F. Dodigović, I. Grčić, P. Markužić, L. Radetić y M. Topić, “Ammonia concentration monitoring using Arduino platform,” Environmental Engineering – Inženjerstvo okoliša, vol. 6, n.º 1, pp. 21–26, 2019, doi: 10.37023/ee.6.1.4. Disponible: https://doi.org/10.37023/ee.6.1.4

<a id="ref17"></a>[17] National Institute for Occupational Safety and Health (NIOSH), “Conversion calculator,” Centers for Disease Control and Prevention. Consultado: 03-nov-2026. [En línea]. Disponible: https://wwwn.cdc.gov/Niosh-oeb/Resource/Calculator

<a id="ref18"></a>[18] H. Othman, G. Sieves, T. Guimarães y R. Azari, “A calibration chamber framework for low-cost indoor air quality sensor validation,” Building and Environment, vol. 287, art. 113856, ene. 2026, doi: 10.1016/j.buildenv.2025.113856. Disponible: https://doi.org/10.1016/j.buildenv.2025.113856

<a id="ref19"></a>[19] ASTM International, Standard Test Methods for Laboratory Determination of Water (Moisture) Content of Soil and Rock by Mass, ASTM D2216-19. West Conshohocken, PA, EE. UU.: ASTM International, 2019.

<a id="ref20"></a>[20] P. Placidi, R. Morbidelli, D. Fortunati, N. Papini, F. Gobbi y A. Scorzoni, “Monitoring soil and ambient parameters in the IoT precision agriculture scenario: An original modeling approach dedicated to low-cost soil water content sensors,” Sensors, vol. 21, n.º 15, art. 5110, 2021, doi: 10.3390/s21155110. Disponible: https://doi.org/10.3390/s21155110

<a id="ref21"></a>[21] NOAA Global Monitoring Laboratory, “Trends in atmospheric carbon dioxide: Global monthly mean CO₂.” Consultado: 03-nov-2026. [En línea]. Disponible: https://gml.noaa.gov/ccgg/trends/global.html

<a id="ref22"></a>[22] T. Tillett, “Don’t hold your breath: Indoor CO₂ exposure and impaired decision making,” Environmental Health Perspectives, vol. 120, n.º 12, p. A475, 2012, doi: 10.1289/ehp.120-a475a. Disponible: https://doi.org/10.1289/ehp.120-a475a

<a id="ref23"></a>[23] NOAA, NASA y U.S. Air Force, U.S. Standard Atmosphere, 1976, NOAA-S/T 76-1562. Washington, D. C., EE. UU.: U.S. Government Printing Office, 1976.

<a id="ref24"></a>[24] FAO e IFA, Global Estimates of Gaseous Emissions of NH₃, NO and N₂O from Agricultural Land. Roma, Italia: Food and Agriculture Organization of the United Nations e International Fertilizer Industry Association, 2001. Consultado: 30-oct-2026. [En línea]. Disponible: https://www.fao.org/4/y2780e/y2780e00.htm

<a id="ref25"></a>[25] W.-f. Wan, F. Li, M. Hong, F. Chang y H.-y. Gao, “Effects of nitrogen rate and urease inhibitor on N₂O emission and NH₃ volatilization in drip irrigated potato fields,” Journal of Plant Nutrition and Fertilizers, vol. 24, n.º 3, pp. 693–702, 2018, doi: 10.11674/zwyf.17197. Disponible: https://doi.org/10.11674/zwyf.17197

<a id="ref26"></a>[26] National Weather Service, “Pressure definitions,” NWS Boulder, CO. Consultado: 03-nov-2026. [En línea]. Disponible: https://www.weather.gov/bou/pressure_definitions

<a id="ref27"></a>[27] G. C. Topp, J. L. Davis y A. P. Annan, “Electromagnetic determination of soil water content: Measurements in coaxial transmission lines,” Water Resources Research, vol. 16, n.º 3, pp. 574–582, 1980, doi: 10.1029/WR016i003p00574. Disponible: https://doi.org/10.1029/WR016i003p00574

<a id="ref28"></a>[28] E. A. A. D. Nagahage, I. S. P. Nagahage y T. Fujino, “Calibration and validation of a low-cost capacitive moisture sensor to integrate the automated soil moisture monitoring system,” Agriculture, vol. 9, n.º 7, art. 141, 2019, doi: 10.3390/agriculture9070141. Disponible: https://doi.org/10.3390/agriculture9070141

<a id="ref29"></a>[29] Agency for Toxic Substances and Disease Registry (ATSDR), Toxicological Profile for Ammonia, cap. 2. Atlanta, GA, EE. UU.: U.S. Department of Health and Human Services, 2004. [En línea]. Disponible: https://www.atsdr.cdc.gov/ToxProfiles/tp126-c2.pdf
