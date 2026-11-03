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

Cuando la urea se aplica al sustrato húmedo, la enzima ureasa la descompone. La reacción produce carbonato de amonio, consume iones hidrógeno y eleva el pH alrededor del gránulo de fertilizante [[8]](#ref8). El proceso se resume en cuatro ecuaciones [[8]](#ref8):

**Hidrólisis de la urea.** La urea reacciona con el agua del sustrato y forma carbonato de amonio:

$$
\text{CO(NH}_2\text{)}_2\,(aq) + 2\,\text{H}_2\text{O}\,(l) \longrightarrow (\text{NH}_4)_2\text{CO}_3\,(aq) \qquad (1)
$$

**Formación de amonio y dióxido de carbono.** El carbonato de amonio reacciona con los iones hidrógeno del medio, libera amonio y puede liberar CO₂:

$$
(\text{NH}_4)_2\text{CO}_3\,(aq) + 2\,\text{H}^+\,(aq) \longrightarrow 2\,\text{NH}_4^+\,(aq) + \text{CO}_2\,(g) + \text{H}_2\text{O}\,(l) \qquad (2)
$$

**Equilibrio entre amonio y amoníaco.** El amonio se transforma en amoníaco disuelto:

$$
\text{NH}_4^+\,(aq) + \text{OH}^-\,(aq) \rightleftharpoons \text{NH}_3\,(aq) + \text{H}_2\text{O}\,(l) \qquad (3)
$$

**Paso del amoníaco al aire.** El amoníaco disuelto pasa al aire como gas, que es lo que mide el MQ-137:

$$
\text{NH}_3\,(aq) \rightleftharpoons \text{NH}_3\,(g) \qquad (4)
$$

**Factores que controlan el proceso.** El equilibrio de la ecuación (3) depende del pH: la fracción del nitrógeno amoniacal presente como NH₃ pasa de 0,058 % a pH 6 a 36,5 % a pH 9 [[8]](#ref8). La temperatura también influye, porque un sustrato más cálido acelera la actividad de la ureasa y aumenta el amoníaco disuelto [[8]](#ref8). La ecuación (2) es una representación simplificada: parte del carbono puede quedar disuelto como bicarbonato o carbonato, por lo que no todo el carbono de la urea pasa al aire como CO₂.

**Contenido de nitrógeno de la urea.** Por su fórmula química, CO(NH₂)₂, la urea contiene 46,6 % de nitrógeno en masa:

$$
\%\text{N} = \frac{2 \times 14{,}01\ \text{g/mol}}{60{,}06\ \text{g/mol}} \times 100 \approx 46{,}6\ \%
$$

Este valor permite convertir la dosis de nitrógeno de cada tratamiento en la masa de urea que se aplica a cada maceta.

## 3.2 Qué sensor registra cada parte del proceso

Cada sensor mide una variable que aparece en las ecuaciones (1) a (4) o que las controla:

- **MQ-137:** mide el NH₃(g) de la ecuación (4), la variable principal del estudio.
- **MH-Z19B:** mide el CO₂(g). Una parte proviene de la ecuación (2), pero otra parte proviene de la respiración de las raíces, de los microorganismos y de la descomposición de la materia orgánica del sustrato [[9]](#ref9), por lo que su lectura no se atribuye solo a la urea.
- **BME280:** mide la temperatura, que acelera la hidrólisis y desplaza el equilibrio de la ecuación (3) [[8]](#ref8), y la humedad relativa, que altera la respuesta de los sensores de óxido metálico como el MQ-137 [[10]](#ref10).
- **Sensor capacitivo de humedad de tierra v1.2:** mide el agua del sustrato, que es un reactivo de la ecuación (1) [[8]](#ref8).
- **ESP32:** reúne las lecturas de los cuatro sensores, les asigna fecha, hora y tratamiento, y las transmite.

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

## 3.4 Pruebas iniciales de los sensores

Las pruebas se realizan con el prototipo en protoboard de la sección 4. Cada sensor sigue un procedimiento propio:

1. **MH-Z19B:** se enciende al aire libre, se espera su precalentamiento de 3 minutos [[12]](#ref12) y se anota la lectura durante 5 minutos. Othman et al. validaron este mismo modelo frente a un equipo de referencia en una cámara de calibración [[18]](#ref18).
2. **BME280:** se coloca junto a un termómetro y un higrómetro de referencia, se espera 10 minutos y se anotan la temperatura, la humedad relativa y la presión.
3. **Sensor capacitivo v1.2:** se inserta en una muestra de sustrato seco y se anota su señal; luego se repite en el mismo sustrato saturado de agua. Ambas muestras se pesan antes y después de secarlas en estufa para obtener su contenido real de agua por el método gravimétrico normalizado [[19]](#ref19), y la señal se relaciona con ese contenido como en el trabajo de Placidi et al. [[20]](#ref20).
4. **MQ-137:** se deja energizado más de 48 horas, como exige el fabricante [[14]](#ref14), y luego se anota su tensión en aire limpio para calcular $R_0$ con la fórmula de la sección 3.3. La calibración frente a concentraciones conocidas de NH₃ se realiza después [[16]](#ref16).
5. **ESP32:** se deja el programa funcionando 30 minutos y se comprueba que se registraron todas las lecturas de los cuatro sensores.

Cada valor medido se anota en la Tabla 3.

<p align="center"><em>Tabla 3. Registro de las pruebas iniciales de los sensores.</em></p>

<div align="center">

| Sensor | Condición de prueba | Lectura obtenida | Valor de referencia (Tabla 4) | Error (%) |
|:---:|:---:|:---:|:---:|:---:|
| MH-Z19B | Aire exterior | ⚠️ *Completar* | 426,1 ppm | ⚠️ *Completar* |
| BME280 | Temperatura del laboratorio | ⚠️ *Completar* | Lectura del termómetro | ⚠️ *Completar* |
| BME280 | Humedad relativa del laboratorio | ⚠️ *Completar* | Lectura del higrómetro | ⚠️ *Completar* |
| BME280 | Presión atmosférica | ⚠️ *Completar* | ≈ 995 hPa | ⚠️ *Completar* |
| Sensor capacitivo v1.2 | Sustrato seco y sustrato saturado | ⚠️ *Completar* | Contenido de agua por pesaje | — |
| MQ-137 | Aire limpio, tras 48 h de precalentamiento | ⚠️ *Completar* | Menor que 5 ppm | — |
| ESP32 | Lectura simultánea de los cuatro sensores | ⚠️ *Completar* | Sin lecturas perdidas | — |

</div>

## 3.5 Valores de referencia y criterio de aceptación

Para saber si una lectura es correcta, se compara con un valor de referencia tomado de la bibliografía o de la hoja de datos del fabricante (Tabla 4). **Estos valores no son resultados medidos:** son los que el sensor debería mostrar si funciona bien, y sirven como criterio para aceptar o rechazar cada prueba.

<p align="center"><em>Tabla 4. Valores de referencia y márgenes de aceptación de cada prueba.</em></p>

<div align="center">

| Sensor | Prueba | Valor de referencia | Margen aceptable | Fuente |
|:---:|:---:|:---:|:---:|:---:|
| MH-Z19B | CO₂ en aire exterior | 426,1 ppm (promedio mundial, julio de 2026) | ± (50 ppm + 5 % de la lectura): de 355 a 497 ppm | NOAA [[21]](#ref21); fabricante [[12]](#ref12) |
| BME280 | Temperatura | Lectura del termómetro de referencia | ± 1,0 °C (entre 0 y 65 °C) | Bosch [[11]](#ref11) |
| BME280 | Humedad relativa | Lectura del higrómetro de referencia | ± 3 % HR | Bosch [[11]](#ref11) |
| BME280 | Presión atmosférica | ≈ 995 hPa a 150 m de altitud | ± 1,0 hPa, más la variación del clima del día | Bosch [[11]](#ref11) |
| Sensor capacitivo v1.2 | Sustrato seco frente a saturado | Contenido de agua por pesaje | Diferencia clara y repetible entre ambas lecturas | Placidi et al. [[20]](#ref20) |
| MQ-137 | NH₃ en aire limpio | Por debajo de 5 ppm, el límite inferior del sensor | Lectura estable, que se usa como R₀ | Fabricante [[14]](#ref14) |
| MQ-137 | NH₃ en la cámara durante los ensayos | De 13 a 105 ppm con 30 min de cierre (estimación del TRL 2) | Dentro del rango de 5 a 500 ppm del sensor | FAO e IFA [[22]](#ref22); Wan et al. [[23]](#ref23); fabricante [[14]](#ref14) |
| ESP32 | Lectura simultánea | Cuatro lecturas en cada ciclo | Sin lecturas perdidas | — |

</div>

**Cálculo del error.** Para cada prueba se calcula el error porcentual entre la lectura y el valor de referencia:

$$
\text{Error (\%)} = \frac{\left|\text{valor medido} - \text{valor de referencia}\right|}{\text{valor de referencia}} \times 100
$$

La prueba se acepta si la diferencia queda dentro del margen de la Tabla 4.

> **Ejemplo de cálculo (no es un dato medido).** Si el MH-Z19B mostrara 450 ppm al aire libre, la diferencia con la referencia sería de 450 − 426,1 = 23,9 ppm, es decir, un error de 5,6 %. Para esa lectura, el margen del fabricante es de ± (50 + 0,05 × 450) = ± 72,5 ppm. Como 23,9 ppm es menor que 72,5 ppm, la prueba se aceptaría.

**Por qué el CO₂ se mide al aire libre.** El valor de 426,1 ppm de la NOAA corresponde al aire de fondo del planeta [[21]](#ref21). En exteriores, el CO₂ suele estar entre unos 380 y 500 ppm, mientras que en interiores la concentración promedio tiende a ser mayor porque los ocupantes exhalan CO₂ [[24]](#ref24). Por eso esta prueba debe hacerse al aire libre y lejos de vehículos.

**Presión esperada según la altitud.** La presión de referencia se estima con la fórmula derivada de la Atmósfera Estándar de EE. UU. de 1976 [[25]](#ref25), donde *h* es la altitud del laboratorio en metros:

$$
P = 1013{,}25 \times \left(1 - \frac{h}{44\,330{,}77}\right)^{5{,}256}\ \text{hPa}
$$

Para *h* = 150 m, el resultado es de unos 995 hPa. Si el laboratorio está a otra altitud, se reemplaza el valor de *h*. La presión real del día puede diferir algunos hectopascales por las condiciones del clima.

**Por qué el MQ-137 tiene dos referencias.** En aire limpio, la concentración de amoníaco está por debajo del límite inferior del sensor, por lo que esa lectura no se compara con un número sino que se usa como punto de partida ($R_0$). La referencia de 13 a 105 ppm corresponde a lo que se espera medir dentro de la cámara después de fertilizar y se comprobará en los ensayos con macetas.

---

# 4. Demo del prototipo

La Figura 4 muestra el primer prototipo funcional de GREENPLANT: los cuatro sensores conectados a un ESP32 sobre una protoboard y alimentados por USB. La placa PCB3 diseñada en el TRL 2 todavía no se ha fabricado; la protoboard permite probar las conexiones y el programa antes de pasar a la placa definitiva.

<p align="center">
<img width="700" alt="Figura 4. Prototipo de GREENPLANT en protoboard" src="https://github.com/user-attachments/assets/befc1ff9-16fe-463d-8d77-6e56ef6711e0" />
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

**Fundamento químico.** Las ecuaciones (1) a (4) muestran que el NH₃(g) que mide el MQ-137 proviene de la hidrólisis de la urea y del equilibrio entre amonio y amoníaco, y que el proceso depende del agua del sustrato y de la temperatura, que registran el sensor capacitivo y el BME280 [[8]](#ref8). Así, los cuatro sensores cubren tanto el producto principal de la reacción como las condiciones que lo controlan.

**Instrumentación.** El prototipo de la Figura 4 demuestra la integración física de los cuatro sensores con el ESP32. Las pruebas de la Tabla 3, comparadas con los valores de referencia de la Tabla 4, completan la prueba de concepto experimental al mostrar que cada variable puede medirse con un margen de error conocido.

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

<a id="ref22"></a>[22] FAO e IFA, Global Estimates of Gaseous Emissions of NH₃, NO and N₂O from Agricultural Land. Roma, Italia: Food and Agriculture Organization of the United Nations e International Fertilizer Industry Association, 2001. Consultado: 30-oct-2026. [En línea]. Disponible: https://www.fao.org/4/y2780e/y2780e00.htm

<a id="ref23"></a>[23] W.-f. Wan, F. Li, M. Hong, F. Chang y H.-y. Gao, “Effects of nitrogen rate and urease inhibitor on N₂O emission and NH₃ volatilization in drip irrigated potato fields,” Journal of Plant Nutrition and Fertilizers, vol. 24, n.º 3, pp. 693–702, 2018, doi: 10.11674/zwyf.17197. Disponible: https://doi.org/10.11674/zwyf.17197

<a id="ref24"></a>[24] T. Tillett, “Don’t hold your breath: Indoor CO₂ exposure and impaired decision making,” Environmental Health Perspectives, vol. 120, n.º 12, p. A475, 2012, doi: 10.1289/ehp.120-a475a. Disponible: https://doi.org/10.1289/ehp.120-a475a

<a id="ref25"></a>[25] NOAA, NASA y U.S. Air Force, U.S. Standard Atmosphere, 1976, NOAA-S/T 76-1562. Washington, D. C., EE. UU.: U.S. Government Printing Office, 1976.
