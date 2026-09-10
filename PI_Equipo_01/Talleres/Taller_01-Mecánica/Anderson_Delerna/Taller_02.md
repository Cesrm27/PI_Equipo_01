# Anderson Josue Delerna Infantes

<img width="1470" height="833" alt="Captura de pantalla de la simulación estructural" src="https://github.com/user-attachments/assets/74ce78c4-b9da-4eee-a50b-5fee20238bba" />

<img width="1470" height="833" alt="Captura de pantalla de la simulación estructural" src="https://github.com/user-attachments/assets/82a7c35c-3bb2-4ae7-aacb-4d19351e6ebc" />

## Simulación estructural

Se realizó una **simulación estática estructural en SimScale**, utilizando **PLA (ácido poliláctico)** como material del modelo, debido a que este es el material considerado para la fabricación del prototipo mediante impresión 3D.

Durante el análisis se aplicó una **fuerza lateral de 10 N** para evaluar la respuesta de la estructura ante una carga externa. Esta fuerza permite analizar las zonas de la pieza que pueden presentar una mayor concentración de esfuerzos cuando recibe una acción horizontal.

También se consideró la acción de la **gravedad**, utilizando una aceleración de:

$$
g = 9.81\;m/s^2
$$

La gravedad fue aplicada en el **eje Z, en dirección vertical hacia abajo**, con el objetivo de representar el efecto del peso propio del modelo bajo condiciones normales de funcionamiento. Esta condición permite obtener una representación más cercana a las condiciones físicas reales a las que estaría sometida la estructura.

> **Nota:** La aplicación de la gravedad en el eje Z representa el peso propio del modelo. No representa por sí sola una caída; para simular una caída sería necesario establecer una condición de impacto o una aceleración asociada al evento.

## Resultado de la simulación

El resultado muestra la distribución del **esfuerzo de Von Mises**, expresado en **kPa**. Las zonas de color azul representan menores niveles de esfuerzo, mientras que los colores verde y amarillo indican una mayor concentración de esfuerzos, principalmente cerca del área donde se aplica la fuerza y en algunos bordes de la estructura.

El esfuerzo de Von Mises permite evaluar la intensidad de los esfuerzos internos generados en el material como consecuencia de las cargas aplicadas. De esta manera, es posible identificar las regiones que podrían ser más susceptibles a deformaciones o fallas.

La simulación permite comprobar si la estructura fabricada en **PLA** presenta un comportamiento adecuado frente a una fuerza lateral de **10 N**, además de considerar el efecto de su propio peso debido a la gravedad. Esto permite identificar posibles puntos críticos que podrían requerir refuerzos o modificaciones en el diseño antes de realizar la impresión 3D.

## Justificación de las fuerzas empleadas

### Fuerza lateral de 10 N

Para evaluar la resistencia del diseño, se aplicó una **fuerza lateral de 10 N**. Para establecer una referencia física de esta magnitud, se puede relacionar la fuerza con una masa equivalente mediante la segunda ley de Newton:

$$
F=m\cdot g
$$

Despejando la masa:

$$
m=\frac{F}{g}
$$

Sustituyendo:

$$
m=\frac{10\;N}{9.81\;m/s^2}
$$

$$
m\approx1.02\;kg
$$

Por lo tanto, una fuerza de **10 N** es aproximadamente equivalente al peso de una masa de **1.02 kg** bajo la gravedad terrestre. Esta equivalencia permite establecer una referencia física para la carga utilizada en la simulación.

La fuerza lateral representa una posible carga externa que el prototipo podría experimentar durante su **manipulación, transporte, montaje o uso**, como una presión accidental o un pequeño impacto lateral. La elección de una carga horizontal permite analizar una condición relevante para la estructura, debido a que este tipo de acción puede generar concentraciones de esfuerzo y deformaciones en las paredes, bordes y uniones.

### Fuerza debida a la gravedad

La gravedad se estableció con una aceleración de:

$$
g=9.81\;m/s^2
$$

y se aplicó en el **eje Z, hacia abajo**.

La fuerza asociada al peso propio se determina mediante:

$$
F_g=m\cdot g
$$

donde \(m\) corresponde a la masa del modelo. Por ejemplo, si el modelo tuviera una masa de \(0.5\;kg\):

$$
F_g=0.5(9.81)=4.905\;N
$$

Esto significa que la gravedad genera una carga equivalente al peso de la propia estructura. Su inclusión permite considerar el efecto que tiene el peso del prototipo sobre los soportes y demás elementos estructurales.

## Conclusión

La simulación permitió analizar el comportamiento mecánico del modelo fabricable en **PLA** frente a dos condiciones principales: su **peso propio debido a la gravedad** y una **fuerza lateral de 10 N**.

La gravedad se aplicó en el eje **Z y en dirección vertical hacia abajo**, mientras que la fuerza lateral se utilizó para representar una carga externa horizontal. La combinación de ambas condiciones proporciona una evaluación más representativa del comportamiento de la estructura y permite identificar las zonas con mayor concentración de esfuerzos.

Debido a que el prototipo será fabricado mediante impresión 3D, este análisis previo permite detectar posibles zonas críticas y realizar modificaciones en el diseño antes de proceder con su fabricación.

## Enlaces

* **Link Onshape:** https://cad.onshape.com/documents/dae8f7a73956d3b566d1a60f/w/a5dffbfe064b9d50272f2cdf/e/bb81f5c0199a20d959042ea5

* **Link SimScale:** https://www.simscale.com/workbench/?pid=7504301741564267457&rru=dbe5b96e-8d73-40da-902e-8cec9a6e712c&ci=cb471e84-5a4c-4fa6-9256-862663648714&mt=SIMULATION_RESULT&ct=SOLUTION_FIELD
