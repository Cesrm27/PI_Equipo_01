# Modelado Lateral — Pieza de Fijación

## Vista lateral de la pieza

En la siguiente imagen se muestra el **modelado lateral de la pieza de fijación**, donde se pueden observar los pequeños orificios destinados a la colocación de los tornillos de montaje.

<img width="1600" height="774" alt="image" src="https://github.com/user-attachments/assets/532e1bb1-a5a9-4007-ab8e-c857449d3b7c" />

---

## Características del diseño

* **Vista:** Lateral
* **Elemento principal:** Pieza de fijación
* **Geometría:** Pieza con forma de cuña
* **Orificios:** Pequeños agujeros para la instalación de tornillos
* **Función de los orificios:** Permitir la fijación y montaje de la pieza
* **Modelado:** Diseño tridimensional realizado en Onshape
* **Material empleado en la simulación:** PLA

### Orificios de fijación

Los pequeños agujeros ubicados en la pieza están diseñados para recibir los **tornillos de montaje**, permitiendo asegurar la pieza a la estructura correspondiente. Estos puntos de fijación son importantes para el análisis estructural, debido a que representan las zonas donde la pieza se encuentra restringida o transmite las cargas hacia la estructura.

---

## Material empleado

Para el análisis estructural se consideró **PLA (ácido poliláctico)** como material de la pieza, debido a que es el material previsto para su fabricación mediante impresión 3D.

El PLA presenta propiedades mecánicas adecuadas para prototipos y piezas de fijación sometidas a cargas moderadas. Para la simulación se utilizan sus propiedades mecánicas, como el módulo de elasticidad, coeficiente de Poisson y densidad, necesarias para determinar la respuesta de la pieza frente a las cargas aplicadas.

---

## Condiciones de carga y gravedad

Para representar las condiciones físicas a las que estaría sometida la pieza, se consideró la **gravedad terrestre**, utilizando:

$$
g = 9.81\;m/s^2
$$

La dirección de la gravedad se estableció **verticalmente hacia abajo**, en dirección al centro de la Tierra. Esta condición representa el peso propio de la pieza.

La fuerza producida por la gravedad se calcula mediante la expresión:

$$
F_g=m\cdot g
$$

donde:

* \(F_g\) = fuerza producida por el peso de la pieza, en N.
* \(m\) = masa de la pieza, en kg.
* \(g\) = aceleración gravitacional, \(9.81\;m/s^2\).

Por ejemplo, si la pieza tuviera una masa de \(0.10\;kg\), su peso sería:

$$
F_g=0.10(9.81)=0.981\;N
$$

Por lo tanto, la gravedad permite considerar el efecto real del peso propio de la pieza durante el análisis.

### Fuerza aplicada

Además del peso propio, se consideró una **carga externa aplicada sobre la cara opuesta al extremo fijo**. Esta condición representa una presión o fuerza externa que podría recibir la pieza durante su funcionamiento.

La aplicación de esta fuerza permite evaluar cómo se distribuyen los esfuerzos y desplazamientos desde la zona de aplicación hacia los puntos de fijación.

La justificación física de la carga se basa en la segunda ley de Newton:

$$
F=m\cdot a
$$

La fuerza aplicada produce una respuesta mecánica en la pieza y genera esfuerzos internos que deben ser soportados por la geometría y por las zonas de fijación.

En conjunto, las condiciones consideradas son:

1. **Soporte fijo:** representa la zona donde la pieza se encuentra asegurada mediante los tornillos.
2. **Gravedad:** \(9.81\;m/s^2\), dirigida verticalmente hacia abajo, para representar el peso propio.
3. **Carga externa:** aplicada sobre la cara opuesta al extremo fijo para evaluar la resistencia de la pieza ante una acción externa.

---

## Resultado de la simulación

<img width="1600" height="772" alt="image" src="https://github.com/user-attachments/assets/52413d43-e0eb-4499-b1b7-303d54361f87" />

La pieza presenta una geometría tipo cuña, con un extremo fijo y una carga aplicada sobre la cara opuesta. El resultado mostrado corresponde al **desplazamiento absoluto en fase Y**, representado mediante un gradiente de colores.

La escala presentada varía aproximadamente entre **0 y 180 rad**. La mayor variación se concentra hacia el extremo angosto de la pieza, mientras que las regiones próximas a la fijación presentan una variación menor debido a las restricciones impuestas.

Este resultado permite observar cómo responde la pieza ante la excitación aplicada y determinar las regiones que presentan una mayor variación de desplazamiento.

---

## Respuesta electromagnética

<img width="1600" height="762" alt="image" src="https://github.com/user-attachments/assets/7678729b-196e-4b73-800e-27d78a046045" />

La geometría tipo placa/bloque presenta un degradado de azul a rojo, correspondiente a valores de **EM** comprendidos aproximadamente entre:

$$
0 \quad \text{y} \quad 1.656\times10^{-11}
$$

Los valores obtenidos son extremadamente pequeños. A una frecuencia de **0 Hz**, esto indica que la respuesta electromagnética dinámica asociada al análisis es prácticamente nula. Por ello, bajo esta condición de frecuencia, el comportamiento electromagnético de la pieza resulta despreciable.

---

## Conclusión del análisis

El modelado tridimensional de la pieza de fijación fue realizado en **Onshape**, mientras que las condiciones de simulación y el análisis de respuesta se realizaron considerando las propiedades del **PLA**.

Se consideró la acción de la gravedad con una aceleración de \(9.81\;m/s^2\) en dirección vertical hacia abajo, representando el peso propio de la pieza. Asimismo, se aplicó una carga externa sobre la cara opuesta a la zona fija con el propósito de evaluar la respuesta de la estructura ante una acción externa.

La combinación de las restricciones, la gravedad y la carga aplicada permite estudiar el comportamiento de la pieza y determinar las zonas donde se presentan mayores desplazamientos o variaciones de respuesta.

---

## Modelado en Onshape

El diseño tridimensional de la pieza fue desarrollado en **Onshape**.

**Link:** https://cad.onshape.com/documents/70658c4b5d3fe9a19752c02d/w/dce491f4056c340a6e6822a1/e/b34eb9c8975484f3f167059e?renderMode=0&uiState=6a9106726d662ac4fef301d1
