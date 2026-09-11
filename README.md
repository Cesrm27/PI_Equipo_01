<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=rect&color=0:07111F,50:285C3A,100:4CAF50&height=230&section=header&text=GREENPLANT%20&fontSize=58&fontColor=FFFFFF&fontAlignY=42&desc=IoT%20%7C%20Monitoreo%20Experimental%20%7C%20Agricultura%20Inteligente&descSize=18&descAlignY=68&animation=fadeIn" width="100%"/>
</p>

<p align="center">
  <strong>Sistema para el monitoreo experimental del cultivo de papa y sus emisiones gaseosas</strong>
</p>

<p align="center">
  <strong>PROYECTO INTEGRADOR · 2026-II</strong>
  <br>
  <sub>Universidad Peruana Cayetano Heredia · Ingeniería Informática + Ingeniería Industrial</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/IoT-ESP32-285C3A?style=for-the-badge&logo=espressif&logoColor=white"/>
  <img src="https://img.shields.io/badge/Agricultura-Inteligente-66BB6A?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Sostenibilidad-ODS%2013-2E7D32?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/ODS%202-Hambre%20Cero-4C9F38?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/ODS%209-Innovación%20e%20Infraestructura-EA6A00?style=for-the-badge"/>
</p>

<br>

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Montserrat&weight=600&size=22&duration=2800&pause=900&color=4CAF50&center=true&vCenter=true&width=750&lines=MEDIR+%E2%86%92+REGISTRAR+%E2%86%92+ANALIZAR+%E2%86%92+COMPARAR;Tecnolog%C3%ADa+IoT+para+una+agricultura+m%C3%A1s+sostenible" />
</p>

---

# 🌱 Simulación del funcionamiento de GREENPLANT

```mermaid
flowchart LR

    A["🌱 CULTIVO DE PAPA"] --> B["📦 CÁMARA EXPERIMENTAL"]

    B --> C["📡 SENSORES"]

    C --> C1["🌫️ GASES"]
    C --> C2["🌡️ TEMPERATURA"]
    C --> C3["💧 HUMEDAD"]
    C --> C4["🧂 CONDUCTIVIDAD"]
    C --> C5["💡 ILUMINACIÓN"]

    C1 --> D["⚙️ ESP32"]
    C2 --> D
    C3 --> D
    C4 --> D
    C5 --> D

    D --> E["💾 ADQUISICIÓN Y REGISTRO DE DATOS"]

    E --> F["📊 ANÁLISIS DE DATOS"]

    F --> G["🔎 COMPARACIÓN DE RESULTADOS"]

    G --> H["📈 INFORMACIÓN PARA EL ANÁLISIS DEL CULTIVO"]

    style A fill:#285C3A,color:#fff,stroke:#4CAF50
    style B fill:#388E3C,color:#fff,stroke:#81C784
    style C fill:#1565C0,color:#fff,stroke:#64B5F6
    style D fill:#37474F,color:#fff,stroke:#90A4AE
    style F fill:#EF6C00,color:#fff,stroke:#FFB74D
    style G fill:#00838F,color:#fff,stroke:#80DEEA
    style H fill:#2E7D32,color:#fff,stroke:#81C784

``` 
# 🔄 Flujo principal

**Cultivo → Cámara → Sensores → ESP32 → Datos → Análisis → Comparación**

GREENPLANT busca obtener datos del cultivo de papa bajo condiciones experimentales controladas para posteriormente analizarlos y encontrar patrones relacionados con las variables medidas.

---

# 🌍 Objetivos de Desarrollo Sostenible

<p align="center">
  <img src="https://img.shields.io/badge/ODS%2013-Acción%20por%20el%20Clima-3F7E44?style=for-the-badge" />
  <img src="https://img.shields.io/badge/ODS%202-Hambre%20Cero-4C9F38?style=for-the-badge" />
  <img src="https://img.shields.io/badge/ODS%209-Innovación%20e%20Infraestructura-EA6A00?style=for-the-badge" />
</p>

## 🌱 ODS 13 · Acción por el Clima

GREENPLANT se relaciona con el **ODS 13: Acción por el Clima**, debido a que busca contribuir al monitoreo y análisis experimental de gases asociados a actividades agrícolas.

El proyecto utiliza **IoT y sensores** para generar información que permita estudiar el comportamiento de las variables medidas durante los ensayos.

### 🎯 Meta 13.3 · Educación y sensibilización sobre el cambio climático

La **Meta 13.3** busca mejorar la educación, la sensibilización y la capacidad humana e institucional relacionada con la mitigación, adaptación y reducción de los efectos del cambio climático.

GREENPLANT se relaciona con esta meta mediante la **generación de información experimental sobre gases y variables ambientales**, promoviendo el uso de tecnologías de monitoreo y el análisis de fenómenos relacionados con el ambiente y la actividad agrícola.

---

## 🌾 ODS 2 · Hambre Cero

GREENPLANT se relaciona con el **ODS 2: Hambre Cero**, debido a que el proyecto se enfoca en el **cultivo de papa** y busca generar información experimental sobre las condiciones que rodean su desarrollo.

Mediante el monitoreo de **NH₃, CO₂ y variables ambientales y del sustrato**, el proyecto busca obtener datos que permitan analizar y comparar las condiciones del cultivo, contribuyendo al estudio de procesos relacionados con la producción agrícola.

### 🎯 Meta 2.4 · Agricultura sostenible

La **Meta 2.4** busca garantizar sistemas de producción de alimentos sostenibles y promover prácticas agrícolas resilientes que incrementen la productividad, ayuden a mantener los ecosistemas, fortalezcan la adaptación al cambio climático y mejoren progresivamente la calidad del suelo.

GREENPLANT se relaciona con esta meta mediante el **estudio experimental del cultivo de papa**, considerando variables del suelo, condiciones ambientales y gases presentes durante los ensayos. La información obtenida puede contribuir al análisis de las condiciones asociadas al desarrollo del cultivo.

---

## ⚙️ ODS 9 · Industria, Innovación e Infraestructura

GREENPLANT se relaciona con el **ODS 9: Industria, Innovación e Infraestructura**, debido a que propone el desarrollo de una solución tecnológica basada en **IoT, sensores y un ESP32** para el monitoreo experimental del cultivo de papa.

El proyecto integra **hardware, sensores, adquisición y registro de datos** para construir una herramienta tecnológica que permita realizar mediciones de **NH₃, CO₂ y variables ambientales y del sustrato**, fortaleciendo el uso de tecnologías de monitoreo e innovación aplicadas al ámbito agrícola.

### 🎯 Meta 9.5 · Investigación científica e innovación tecnológica

La **Meta 9.5** busca mejorar la investigación científica, fortalecer las capacidades tecnológicas y fomentar la innovación, incluyendo el incremento de las actividades de investigación y desarrollo.

GREENPLANT se relaciona directamente con esta meta al desarrollar un **prototipo experimental basado en sensores, IoT y adquisición de datos**, orientado a la generación de información para el estudio del cultivo de papa.

El proyecto integra conocimientos de **electrónica, programación, sensores, adquisición de datos y análisis experimental**, utilizando estas tecnologías para abordar una problemática relacionada con el monitoreo agrícola.

---

# 🌱 GREENPLANT

> **Una solución experimental orientada al monitoreo del cultivo de papa mediante sensores y adquisición de datos.**

## 🎯 Nuestro enfoque

GREENPLANT busca desarrollar un **prototipo experimental para el cultivo de papa**, utilizando una cámara cerrada, sensores y un sistema de adquisición de datos.

El sistema permitirá registrar información relacionada con:

<pre align="center">
🌱 CULTIVO DE PAPA
        ↓
📦 CÁMARA EXPERIMENTAL
        ↓
📡 SENSORES
        ↓
💾 REGISTRO DE DATOS
        ↓
🧹 PROCESAMIENTO
        ↓
📊 ANÁLISIS Y PATRONES
        ↓
📈 COMPARACIÓN
</pre>


# 📸 Fotografía del Equipo

<p align="center">
  <img width="650" src="/Recursos/Imágenes/equipo.jpg" />
</p>

<p align="center">
  <em>Figura 1. Fotografía del equipo 01</em>
</p>

---

# 👥 Integrantes del Equipo

<div align="center">

| Foto | Nombre | Rol | Intereses |
|------|--------|-----|-----------|
| <img width="180" height="180" alt="Cesar Rodrigo Milla Gómez" src="https://github.com/user-attachments/assets/365b9f4f-e7b6-4e00-9224-4c63955fa9ec" /> | **Cesar Rodrigo Milla Gómez** | Responsable de función general, análisis de información y seguridad | Investigación, tecnología y análisis |
| <img width="180" height="180" alt="Anderson Josue Delerna Infantes" src="https://github.com/user-attachments/assets/cd4f5d69-105e-405f-b197-bf7ede08fc25" /> | **Anderson Josue Delerna Infantes** | Responsable de geometría, energía, control y software | Programación, automatización y desarrollo |
| <img width="180" height="180" alt="Kevin Esty Carvallo Neciosup" src="https://github.com/user-attachments/assets/971ad11e-950f-45ed-a6a2-e6fe3e4e6dbc" /> | **Kevin Esty Carvallo Neciosup** | Líder del equipo y responsable de sensores, hardware y adquisición de datos | Sensores, programación y sistemas |
| <img width="180" height="180" alt="Shedira Lumeris Sihuincha Palacin" src="https://github.com/user-attachments/assets/1861e18f-728a-443d-9060-df34c1079c61" /> | **Shedira Lumeris Sihuincha Palacin** | Responsable de estructura, comunicaciones, ergonomía, calidad y documentación | Procesos, análisis y organización |

</div>

---
# 📌 Resumen del Proyecto

## 🌱 ¿Qué es GREENPLANT?

**GREENPLANT** es un prototipo experimental orientado al **monitoreo del cultivo de papa**, mediante sensores y adquisición de datos.

El sistema utilizará una **cámara experimental cerrada**, en la cual se colocará una planta joven de papa junto con su sustrato.

Dentro de la cámara se realizarán mediciones controladas de gases y variables relacionadas con las condiciones del cultivo.

### 📡 Las mediciones podrán incluir:

- 🌫️ Gases presentes en la cámara
- 🌡️ Temperatura ambiental
- 💧 Humedad ambiental
- 🌡️ Temperatura del suelo
- 💧 Humedad del suelo
- 💡 Iluminación
- ⏱️ Tiempo de experimentación

De acuerdo con el enfoque planteado para el proyecto, se prestará especial atención al monitoreo de **amoniaco gaseoso (NH₃)** y **dióxido de carbono (CO₂)** en el cultivo de papa.

Los datos obtenidos serán almacenados para posteriormente **analizarlos y compararlos**, buscando identificar variaciones y relaciones entre las variables registradas durante los ensayos.

---

## ⚠️ Problemática

La agricultura requiere información que permita comprender el comportamiento de los cultivos y las condiciones que influyen en su desarrollo. En particular, el cultivo de papa presenta diferentes procesos asociados al suelo, la planta y el ambiente que pueden ser estudiados mediante el seguimiento de variables físicas y gaseosas durante condiciones experimentales controladas.

Uno de los aspectos de interés es el comportamiento del **CO₂**, debido a que su concentración puede estar relacionada con procesos de respiración e intercambio gaseoso del sistema suelo-planta. Las cámaras cerradas han sido utilizadas para realizar mediciones relacionadas con los flujos de CO₂ en suelos agrícolas [1], mientras que también se han desarrollado procedimientos mediante cámaras cerradas para estudiar la respiración del suelo a partir de la evolución de la concentración de CO₂ [2].

Por otro lado, la utilización de fertilizantes nitrogenados como la **urea** puede generar pérdidas de nitrógeno hacia la atmósfera mediante la volatilización de **NH₃**. Las propiedades del suelo y las condiciones de aplicación pueden influir en la volatilización de NH₃ proveniente de la urea [3]. Asimismo, se han estudiado diferentes factores relacionados con las emisiones de NH₃ derivadas de la fertilización con urea [4].

Esta problemática también está presente específicamente en el cultivo de papa. Se ha analizado la volatilización de NH₃ en diferentes cultivos, incluyendo papa, bajo condiciones de fertilización con urea, mostrando la importancia de considerar las condiciones del suelo y del cultivo al estudiar estas emisiones [5]. Además, se ha destacado la importancia de evaluar la eficiencia de la fertilización nitrogenada en el cultivo de papa y las pérdidas de nitrógeno asociadas [6].

Asimismo, el CO₂ puede relacionarse con procesos respiratorios de los tejidos de papa, por lo que su comportamiento puede ser considerado como una variable de interés dentro del estudio experimental del cultivo [7].

Sin embargo, estudiar simultáneamente las concentraciones de **NH₃ y CO₂** junto con variables ambientales y del sustrato requiere mantener condiciones experimentales controladas y registrar las mediciones de manera organizada. Una medición aislada de un gas no permite comprender por sí sola cómo se comporta el sistema durante el ensayo.

Por ello, el problema no consiste únicamente en detectar la presencia de NH₃ o CO₂, sino en **obtener información experimental que permita relacionar la concentración de estos gases con las condiciones del cultivo y observar su comportamiento a lo largo del tiempo**.

Ante esta necesidad, GREENPLANT propone una alternativa experimental orientada a:

<div align="center">

🔬 **Medir** → 💾 **Registrar** → 🔍 **Analizar** → 📊 **Comparar**

</div>

las variables obtenidas durante los ensayos.

El sistema busca transformar las lecturas individuales de los sensores en **datos experimentales organizados**, permitiendo identificar tendencias, analizar posibles relaciones entre variables y comparar los resultados obtenidos bajo diferentes condiciones del cultivo.

<div align="center">

| 🔬 Medir | 💾 Registrar | 🧠 Analizar | 📊 Comparar |
|:---:|:---:|:---:|:---:|
| Gases y variables | Datos experimentales | Tendencias y relaciones | Resultados |

</div>

<p>
De esta manera, GREENPLANT busca generar una base tecnológica para el <strong>estudio experimental del cultivo de papa</strong>, permitiendo observar el comportamiento de NH₃ y CO₂ bajo condiciones controladas y generar información que pueda ser utilizada posteriormente para el análisis de los resultados.
</p>

### 📚 Estudios que anteceden

La propuesta se fundamenta en investigaciones relacionadas con la medición de gases en sistemas suelo-planta, el uso de cámaras cerradas y la volatilización de NH₃ asociada a la fertilización con urea.

<div align="center">

| Estudio | Aporte principal | Relación con nuestro proyecto |
|:---|:---|:---|
| **Kusa et al. (2008)** | Compararon métodos de cámara cerrada y gradiente de concentración para medir flujos de CO₂ y N₂O en suelos agrícolas **[1]**. | Sustenta el uso de una **cámara cerrada** como base para realizar mediciones de gases en condiciones controladas. |
| **Baneschi et al. (2023)** | Desarrollaron un protocolo con cámaras cerradas para medir la respiración del suelo mediante CO₂ y analizar la incertidumbre de las mediciones **[2]**. | Sustenta la necesidad de controlar el **volumen de la cámara, el tiempo de medición y la calidad de los datos de CO₂**. |
| **Perez-Trejo et al. (1981)** | Estudiaron el intercambio gaseoso y la respiración de tejidos de papa en relación con el CO₂ **[7]**. | Relaciona el **CO₂ con procesos respiratorios de la papa**, respaldando su inclusión como variable de estudio. |
| **Lee et al. (2024)** | Evaluaron la volatilización de NH₃ en diferentes cultivos, incluyendo papa, bajo fertilización con urea y otras fuentes nitrogenadas **[5]**. | Sustenta el estudio del **NH₃ en papa bajo condiciones de fertilización**, considerando variables del suelo y ambientales. |
| **Sunderlage y Cook (2018)** | Analizaron la influencia de propiedades del suelo sobre la volatilización de NH₃ proveniente de la urea **[3]**. | Sustenta la importancia de controlar las **condiciones del sustrato** durante los ensayos con urea. |
| **Chatzitriantafyllou et al. (2026)** | Revisaron estrategias de fertilización nitrogenada en papa y los problemas relacionados con la eficiencia del uso del nitrógeno y las pérdidas ambientales **[6]**. | Refuerza la importancia de estudiar la **fertilización nitrogenada en el cultivo de papa** y generar información experimental. |

</div>

### 🔎 Conclusión de los antecedentes

Los estudios revisados muestran que existen bases científicas para estudiar los gases mediante cámaras cerradas y que las condiciones del suelo, la fertilización y las características del cultivo pueden influir en las mediciones de NH₃ y CO₂.

<p>
A partir de estos antecedentes, GREENPLANT plantea integrar sensores, adquisición de datos y una cámara experimental para obtener información organizada que permita **medir, registrar, analizar y comparar** el comportamiento de estas variables durante los ensayos.
<p>

# 🎯 Objetivo General

Desarrollar un **prototipo experimental inteligente** capaz de monitorear gases y variables ambientales y del suelo asociadas al cultivo de papa mediante **sensores y IoT**, generando datos que permitan analizar y comparar los resultados obtenidos durante los ensayos.

---

# 🎯 Objetivos Específicos

- Diseñar una cámara experimental cerrada para realizar ensayos con plantas jóvenes de papa.
- Implementar sensores para medir gases y variables ambientales y del sustrato.
- Registrar información relacionada con las concentraciones de gases presentes durante cada ensayo.
- Registrar temperatura, humedad e iluminación asociadas a las condiciones experimentales.
- Utilizar un microcontrolador **ESP32** para adquirir y gestionar los datos obtenidos por los sensores.
- Almacenar las mediciones junto con la identificación del cultivo y el tiempo de experimentación.
- Generar un conjunto de datos para el análisis de las variables registradas.
- Comparar los resultados obtenidos durante diferentes ensayos del cultivo de papa.
- Generar información que facilite el análisis experimental del comportamiento del cultivo.

---
# 👤 Público Objetivo

**GREENPLANT** estará dirigido principalmente a usuarios relacionados con el **estudio, producción y monitoreo agrícola**.

### 👨‍🌾 Agricultores
Interesados en conocer mejor las condiciones de sus cultivos.

### 🔬 Investigadores
Para realizar ensayos y analizar datos relacionados con cultivos.

### 🎓 Estudiantes
Como herramienta experimental para proyectos académicos.

### 🏫 Instituciones educativas
Para actividades de investigación y experimentación.

> El proyecto se plantea inicialmente para el **cultivo de papa**, pudiendo posteriormente adaptarse a otros cultivos.

---

# 🧪 Variables y Gases a Monitorear

GREENPLANT utilizará diferentes sensores para obtener información de los gases, del ambiente y del sustrato presentes dentro de la cámara experimental. La selección de estas variables responde a la necesidad de relacionar las concentraciones de **NH₃ y CO₂** con las condiciones en las que se desarrolla el ensayo.

<div align="center">

| Variable | Función | Justificación y fuente |
|:---|:---|:---|
| 🧪 **NH₃** | Monitoreo de amoníaco gaseoso | Se selecciona debido a que la aplicación de fertilizantes nitrogenados como la urea puede generar volatilización de NH₃, cuya magnitud depende de las condiciones del suelo y del ambiente **[3], [4], [5]**. |
| 🌫️ **CO₂** | Monitoreo de dióxido de carbono gaseoso | Se selecciona porque el CO₂ está relacionado con procesos de respiración e intercambio gaseoso del sistema suelo-planta y puede ser estudiado mediante cámaras cerradas **[1], [2], [7]**. |
| 🌡️ **Temperatura ambiental** | Medición de la temperatura dentro de la cámara | Se considera una variable de control porque la temperatura puede influir en los procesos relacionados con la volatilización de NH₃ y en el comportamiento fisiológico del cultivo **[4], [5]**. |
| 💧 **Humedad ambiental** | Medición de la humedad relativa | Se incluye para caracterizar las condiciones ambientales de la cámara y mantener un registro de las condiciones en las que se realizan las mediciones. |
| 🌡️ **Temperatura del suelo** | Caracterización de las condiciones térmicas del sustrato | Se incluye debido a que la temperatura del suelo puede influir en los procesos de transformación y volatilización asociados al nitrógeno aplicado al sustrato **[4], [5]**. |
| 💧 **Humedad del suelo** | Medición de la humedad del sustrato | Se incluye debido a que el contenido de agua del suelo puede influir en la volatilización de NH₃ y constituye una condición importante para interpretar los resultados del ensayo **[3], [4], [5]**. |
| 💡 **Iluminación** | Medición de la intensidad de luz | Se incluye para caracterizar las condiciones de iluminación de la planta, debido a que la intensidad lumínica influye en la fotosíntesis y el intercambio de CO₂ en el cultivo de papa **[7], [12]**. |
| ⏱️ **Tiempo** | Registro temporal de cada medición | Se incluye para observar la evolución de las concentraciones de NH₃ y CO₂ y de las demás variables durante el ensayo, permitiendo comparar su comportamiento a lo largo del tiempo **[1], [2]**. |

</div>

### 🔧 Selección de los componentes

La selección de los sensores y componentes se realiza considerando su **principio de medición, rango de operación, compatibilidad con el sistema de adquisición y disponibilidad para la implementación del prototipo**.

<div align="center">

| Componente | Variable asociada | Justificación de selección | Fuente |
|:---|:---|:---|:---:|
| **ME3-NH₃** | NH₃ | Sensor electroquímico diseñado específicamente para detectar amoníaco. Presenta un rango de medición de **0–100 ppm**, resolución de **0.5 ppm** y tiempo de respuesta T90 ≤ 90 s, características que permiten utilizarlo para el monitoreo experimental de NH₃ **[8]**. | **[8]** |
| **MH-Z19C** | CO₂ | Sensor NDIR diseñado para la detección de CO₂. Dispone de salida UART/PWM, compensación de temperatura y rangos de medición que incluyen **400–2000, 400–5000 y 400–10000 ppm**, según la configuración **[9]**. | **[9]** |
| **BME280** | Temperatura y humedad ambiental | Permite obtener temperatura y humedad relativa mediante un mismo sensor y dispone de interfaces **I²C y SPI**, facilitando su integración con el sistema de adquisición **[11]**. | **[11]** |
| **ESP32** | Adquisición de datos | Se utiliza como controlador principal debido a que dispone de interfaces de comunicación y periféricos adecuados para integrar sensores y procesar sus lecturas. El ESP32 incorpora ADC, UART, I²C, SPI y conectividad inalámbrica, facilitando la adquisición y transmisión de datos **[10]**. | **[10]** |

</div>

> ⚠️ **Nota importante:**  
> La selección definitiva de sensores para **temperatura del suelo, humedad del suelo e iluminación** dependerá de la **viabilidad técnica, disponibilidad, compatibilidad y validación de los componentes** durante el desarrollo del prototipo.

# 📦 Cámara Experimental

GREENPLANT contará con una **cámara experimental cerrada** destinada a realizar mediciones controladas del cultivo de papa.

La cámara permitirá mantener un volumen de medición definido y facilitar la instalación de los sensores.

### 📏 Diseño aproximado

| Característica | Valor |
|----------------|-------|
| Altura total | 22 – 24 cm |
| Diámetro exterior | 18 – 20 cm |
| Diámetro interior | 16 – 17 cm |
| Altura útil interna | 15 – 18 cm |
| Grosor de paredes | 3 – 4 mm |
| Volumen interno | 2.5 – 3.5 L |
| Planta | Planta joven de papa |

### ⚙️ Características principales

- 📦 Cámara experimental cerrada.
- 🌱 Espacio para una planta joven de papa.
- 🔍 Tapa superior transparente.
- 💡 Sistema de iluminación artificial.
- 🔬 Soportes para sensores.
- 🔌 Entradas organizadas para cables.
- 🚪 Sistema de ventilación.
- 🛠️ Estructura diseñada para facilitar el montaje y desmontaje.
- 🧹 Facilidad de limpieza entre ensayos.

---

# ⚙️ Funcionamiento del Sistema

<details>
<summary>🌱 <strong>Ver cómo funcionará GREENPLANT</strong> ⬇️</summary>

<br>

### 1️⃣ Preparación

Se seleccionará una planta joven de papa y se colocará dentro de la cámara experimental junto con su sustrato.

### 2️⃣ Instalación

Se instalarán los sensores correspondientes dentro de la cámara y en el sustrato.

### 3️⃣ Medición

Los sensores realizarán mediciones de gases y variables ambientales y del suelo.

- 🌫️ NH₃
- 🌫️ CO₂
- 🌡️ Temperatura
- 💧 Humedad
- 💡 Iluminación

### 4️⃣ Adquisición

El **ESP32** recibirá las lecturas generadas por los sensores.

### 5️⃣ Registro

Los datos serán registrados junto con información como:

- Identificación del cultivo.
- Número de ensayo.
- Fecha.
- Tiempo de medición.
- Variables ambientales.
- Variables del sustrato.
- Concentraciones gaseosas.

### 6️⃣ Procesamiento

Los datos serán organizados y preparados para su análisis.

### 7️⃣ Comparación

Los resultados de los ensayos podrán compararse para observar diferencias en el comportamiento de las variables medidas.

<br>

<div align="center">

🌱 **PAPA**  
⬇️  
📦 **CÁMARA EXPERIMENTAL**  
⬇️  
📡 **SENSORES**  
⬇️  
⚙️ **ESP32**  
⬇️  
💾 **DATOS**  
⬇️  
📊 **ANÁLISIS**  
⬇️  
📈 **COMPARACIÓN**

</div>

</details>

---

# 🧠 ¿Dónde está nuestra innovación?

GREENPLANT no busca afirmar que los sensores, el ESP32 o las cámaras experimentales sean tecnologías nuevas.

La propuesta de innovación está en **integrar sensores de gases, variables ambientales y variables del sustrato dentro de una cámara experimental**, generando un conjunto de datos que permita analizar y comparar las condiciones del cultivo.

| Enfoque convencional | GREENPLANT |
|----------------------|---------------|
| 🌫️ Medición individual | 📡 Múltiples variables |
| 🔢 Obtiene valores | 💾 Registra datos |
| 📊 Observación manual | 📊 Análisis de datos |
| 📍 Mediciones aisladas | ⏱️ Registro temporal |
| 🌱 Un ensayo | 📊 Comparación entre ensayos |
| 👨‍🔬 Interpretación manual | 🔎 Comparación de resultados |

Por ello, la propuesta busca pasar de:

> **“¿Qué concentración de gas se obtuvo?”**

a:

> **“¿Cómo varían las concentraciones gaseosas al relacionarlas con las condiciones ambientales y del sustrato del cultivo de papa?”**

---

# 📊 Análisis de Datos

Los datos experimentales generados por GREENPLANT serán organizados para facilitar su análisis y comparación.

### 📋 El conjunto de datos podrá incluir:

| Variable | Información |
|----------|-------------|
| 🌱 Cultivo | Identificación del cultivo |
| 🌫️ NH₃ | Concentración medida |
| 🌫️ CO₂ | Concentración medida |
| 🌡️ Temperatura | Condición ambiental |
| 💧 Humedad | Condición ambiental |
| 🌡️ Temperatura del suelo | Condición del sustrato |
| 💧 Humedad del suelo | Condición del sustrato |
| 💡 Iluminación | Condición experimental |
| ⏱️ Tiempo | Momento de la medición |

### 🔄 Flujo de análisis

```text
📡 ADQUISICIÓN DE DATOS
          ↓
💾 ALMACENAMIENTO
          ↓
🧹 ORGANIZACIÓN DE DATOS
          ↓
📊 ANÁLISIS
          ↓
🔎 COMPARACIÓN
          ↓
📈 RESULTADOS EXPERIMENTALES
```
# 📖 Referencias

[1] K. Kusa, T. Sawamoto, R. Hu, and R. Hatano, “Comparison of the closed-chamber and gas concentration gradient methods for measurement of CO₂ and N₂O fluxes in two upland field soils,” *Soil Science and Plant Nutrition*, vol. 54, no. 5, pp. 777–785, 2008, doi: 10.1111/j.1747-0765.2008.00292.x.

[2] I. Baneschi, B. Raco, M. Magnani, M. Giamberini, M. Lelli, P. Mosca, A. Provenzale, L. Coppo, and M. Guidi, “Non-steady-state closed dynamic chamber to measure soil CO₂ respiration: A protocol to reduce uncertainty,” *Frontiers in Environmental Science*, vol. 10, 1048948, 2023, doi: 10.3389/fenvs.2022.1048948.

[3] B. Sunderlage and R. L. Cook, “Soil Property and Fertilizer Additive Effects on Ammonia Volatilization from Urea,” *Soil Science Society of America Journal*, vol. 82, no. 1, pp. 253–259, 2018, doi: 10.2136/sssaj2017.05.0151.

[4] M. Klimczyk, A. Siczek, and L. Schimmelpfennig, “Improving the efficiency of urea-based fertilization leading to reduction in ammonia emission,” *Science of the Total Environment*, vol. 771, 145483, 2021, doi: 10.1016/j.scitotenv.2021.145483.

[5] Y.-J. Lee, E.-C. Im, G. Lee, S.-C. Hong, C.-G. Lee, and S.-J. Park, “Comparison of ammonia volatilization in paddy and field soils fertilized with urea and ammonium sulfate during rice, potato, and Chinese cabbage cultivation,” *Atmospheric Pollution Research*, vol. 15, no. 4, 102049, 2024, doi: 10.1016/j.apr.2024.102049.

[6] M. Chatzitriantafyllou, P. Stavropoulos, S. Kallergi, M. Mavroeidis, I. Roussis, S. Karydogianni, D. Bilalis, and I. Kakabouki, “Optimizing Nitrogen Fertilization in Potato (Solanum tuberosum L.) Cultivation: A Review Regarding Inhibitor Use, Multifaceted Assessment Indicators, and Pathways to Sustainable Intensification,” *Applied Sciences*, vol. 16, no. 5, 2565, 2026, doi: 10.3390/app16052565.

[7] M. S. Perez-Trejo, H. W. Janes, and C. Frenkel, “Mobilization of Respiratory Metabolism in Potato Tubers by Carbon Dioxide,” *Plant Physiology*, vol. 67, no. 3, pp. 514–517, 1981, doi: 10.1104/pp.67.3.514.

[8] Winsen Electronics, “ME3-NH3 Electrochemical Gas Sensor,” Winsen Electronics, 2026.

[9] Winsen Electronics, “MH-Z19C NDIR CO₂ Sensor for HVAC and IAQ,” Winsen Electronics, 2026.

[10] Espressif Systems, “ESP32 Series Datasheet,” Espressif Systems, 2026.

[11] Bosch Sensortec, “BME280: Combined humidity, pressure and temperature sensor,” Bosch Sensortec, Datasheet.

[12] V. I. Chikov, A. L. Mikhailov, O. A. Timofeeva, and L. A. Khamidullina, “Photosynthetic carbon metabolism in potato leaves under changes in light intensity,” Russian Journal of Plant Physiology, vol. 63, no. 1, pp. 70–76, 2016, doi: 10.1134/S1021443716010040.

