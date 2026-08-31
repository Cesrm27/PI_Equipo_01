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

#  Lista de Exigencias

<table>
  <tr>
    <td><strong>Edición:</strong></td>
    <td>Rev. 1</td>
  </tr>
  <tr>
    <td><strong>PROYECTO:</strong></td>
    <td>GREENPLANT AI – Sistema inteligente para el monitoreo experimental del cultivo de papa y la detección de NH₃ y HCN.</td>
  </tr>
  <tr>
    <td><strong>Fecha:</strong></td>
    <td>30/08/2026</td>
  </tr>
  <tr>
    <td><strong>Revisado:</strong></td>
    <td></td>
  </tr>
  <tr>
    <td><strong>CLIENTE:</strong></td>
    <td>UNIVERSIDAD PERUANA CAYETANO HEREDIA (UPCH)</td>
  </tr>
  <tr>
    <td><strong>Elaborado:</strong></td>
    <td>K.C., A.D., C.M., L.S.</td>
  </tr>
</table>


---

| Fecha de cambios | Deseo o Exigencia | Descripción | Responsable |
|---|---|---|---|
| 30/08/2026 | **E** | **Función general:** El sistema deberá permitir realizar mediciones experimentales de gases presentes en el interior de una cámara cerrada que contenga una planta joven de papa junto con su sustrato. El sistema deberá monitorear principalmente **amoníaco gaseoso (NH₃)** y **cianuro de hidrógeno (HCN)**, además de registrar variables ambientales y del suelo relacionadas con el experimento. Las mediciones deberán almacenarse junto con la identificación del cultivo, las condiciones experimentales y el tiempo de experimentación, permitiendo analizar la variación de las concentraciones gaseosas bajo condiciones controladas. Cuando corresponda, la aplicación de **urea podrá registrarse como una condición experimental** para estudiar su relación con las variables medidas, sin que la urea sea medida directamente por el sistema. Los datos obtenidos deberán poder utilizarse posteriormente para identificar patrones mediante **Machine Learning**. La utilización de cámaras cerradas permite estudiar cambios de concentración de gases dentro de un volumen conocido durante un periodo determinado. **(de Klein et al., 2020; Bertora et al., 2018; Pavelka et al., 2018; Winsen Electronics, 2026).** | C.M, K.C, A.D, L.S |
| 30/08/2026 | **E** | **Geometría:** El prototipo deberá presentar una cámara experimental cerrada, portátil y de dimensiones aproximadas de **20 cm × 18 cm × 18 cm**, destinada a contener una planta joven de papa y su sustrato durante las mediciones. La cámara deberá disponer de una tapa superior transparente que permita el ingreso de iluminación artificial y facilite la observación del cultivo. En el interior deberá existir espacio suficiente para instalar los sensores sin obstruir significativamente el crecimiento de la planta. La planta deberá colocarse en una maceta o recipiente interno de aproximadamente **10 cm de diámetro y 8 cm de altura**. La geometría deberá permitir mantener un volumen de medición definido y facilitar la limpieza y sustitución del cultivo entre pruebas. | A.D |
| 30/08/2026 | **E** | **Cinemática:** El prototipo no requerirá mecanismos de movimiento continuo durante la operación. La cámara permanecerá estática durante cada medición para evitar variaciones innecesarias del volumen interno y perturbaciones en las concentraciones de **NH₃ y HCN**. La sustitución de la planta o maceta se realizará manualmente entre experimentos. La tapa deberá poder abrirse y cerrarse para permitir la colocación, retiro y limpieza del sistema. | K.C |
| 30/08/2026 | **E** | **Fuerzas:** La estructura de la cámara deberá soportar su propio peso, el peso de la maceta con el sustrato y la manipulación manual durante la instalación y retiro de los cultivos. La tapa deberá permanecer correctamente cerrada durante las mediciones para reducir pérdidas de gases y mantener estable el volumen experimental. Los soportes de los sensores deberán resistir la manipulación y permanecer firmes durante el ensayo sin alterar significativamente la posición de los sensores. | L.S |
| 30/08/2026 | **E** | **Energía:** El sistema deberá funcionar mediante una fuente de alimentación de bajo voltaje compatible con el ESP32 y los sensores utilizados. Se deberá priorizar una fuente estable que permita mantener el funcionamiento durante todo el periodo experimental.<br><br>• La iluminación artificial instalada sobre la tapa transparente deberá contar con una alimentación independiente o compatible con el sistema eléctrico del prototipo, evitando afectar las mediciones de los sensores.<br>• El sistema deberá permitir verificar la disponibilidad de alimentación para evitar interrupciones durante la adquisición de datos.<br>• Los sensores deberán alimentarse respetando sus niveles de tensión especificados por los fabricantes. El **ESP32-WROOM-32D opera con una alimentación de 3,0 a 3,6 V**.<br><br>**(Espressif Systems, 2025).** | A.D |
| 30/08/2026 | **E** | **Materia:** El sistema deberá permitir introducir una planta joven de papa junto con su sustrato dentro de la cámara experimental. Los materiales que estén en contacto con el sustrato y el ambiente húmedo deberán ser resistentes a la humedad y permitir una limpieza adecuada entre experimentos. La cámara deberá utilizar materiales que permitan mantener un volumen cerrado y estable durante las mediciones. La tapa deberá utilizar un material transparente que permita el paso de la iluminación artificial y la observación del cultivo. La elección de los materiales deberá evitar que estos interfieran significativamente con las mediciones de los gases o variables ambientales. | L.S |
| 30/08/2026 | **E** | **Señales (Información):** El sistema deberá contar con señales de entrada y salida asociadas al proceso de medición, análisis y comparación de las variables registradas durante el cultivo experimental de papa.<br><br>**Señales de entrada:**<br>• Concentración de NH₃.<br>• Concentración de HCN.<br>• Temperatura del suelo.<br>• Humedad del suelo.<br>• Temperatura ambiental.<br>• Humedad ambiental.<br>• Conductividad eléctrica del suelo.<br>• Intensidad de iluminación.<br>• Identificación del cultivo.<br>• Tiempo transcurrido desde el inicio de la medición.<br>• Condición experimental relacionada con la aplicación de urea, cuando corresponda.<br>• Comandos e información ingresada por el usuario.<br><br>**Señales de salida:**<br>• Valores obtenidos de los sensores.<br>• Estado de funcionamiento de los sensores.<br>• Variación de las concentraciones de NH₃ y HCN.<br>• Alertas ante lecturas anormales o datos no válidos.<br>• Registro e historial de mediciones.<br>• Resultados del análisis mediante Machine Learning.<br>• Patrones y relaciones identificados entre las variables registradas.<br>• Comparación de resultados entre diferentes condiciones experimentales.<br><br>Los sensores de gases permiten transformar la concentración del gas objetivo en una señal que puede ser procesada por el sistema de adquisición. **(Winsen Electronics, 2026; Pavelka et al., 2018).** | K.C, C.M |
| 30/08/2026 | **E** | **Control:** El sistema de control deberá coordinar la adquisición de datos provenientes de los sensores y verificar que las mediciones se encuentren dentro de rangos operativos antes de procesarlas. El sistema deberá ejecutar la secuencia de **medición, validación, almacenamiento y análisis**. Durante cada experimento deberá registrar el tiempo de medición y asociar las lecturas al cultivo de papa evaluado. El sistema deberá detectar lecturas fuera del rango operativo o inconsistentes y advertir al usuario para evitar que datos no válidos sean utilizados en el análisis. Las series de concentración de **NH₃ y HCN en función del tiempo** podrán utilizarse para analizar la variación de los gases durante el experimento. **(de Klein et al., 2020; Venterea et al., 2020; Winsen Electronics, 2026).** | A.D, K.C |
| 30/08/2026 | **E** | **Electrónico (hardware):** El sistema utilizará un **ESP32** como controlador principal para adquirir información de los sensores y comunicarse con una interfaz externa. El prototipo deberá integrar sensores para **NH₃ y HCN**, además de sensores para temperatura del suelo, humedad del suelo, temperatura y humedad ambiental, conductividad eléctrica e iluminación. Como referencia para los gases objetivo se consideran los sensores electroquímicos **ME3-NH3 y ME3-HCN de Winsen**, sujetos a disponibilidad y validación final de los componentes. Los demás sensores deberán seleccionarse de acuerdo con los requerimientos del experimento. Los módulos deberán ser reemplazables para facilitar el mantenimiento y futuras mejoras. Winsen especifica sensores ME3 para NH₃ y HCN, mientras que el ESP32 dispone de interfaces para integrar diferentes sensores y módulos. **(Winsen Electronics, 2026; Espressif Systems, 2026).** | K.C, L.S |
| 30/08/2026 | **E** | **Software:** El software deberá permitir adquirir, procesar, almacenar y visualizar la información obtenida de los sensores. Deberá incluir una interfaz que permita identificar el cultivo de papa y observar las concentraciones de **NH₃ y HCN** junto con las variables ambientales y del suelo. El sistema deberá procesar series temporales y emplear algoritmos de **Machine Learning** para analizar simultáneamente las variables medidas, identificar patrones y determinar relaciones entre las condiciones experimentales y las concentraciones gaseosas registradas. La selección y validación del modelo deberá realizarse utilizando los datos experimentales obtenidos. El Machine Learning se empleará como herramienta de análisis de los datos y **no como sustituto de la medición directa de los gases**. **(Zhang et al., 2025; Jiang et al., 2023; Giltrap et al., 2020).** | A.D, K.C |
| 30/08/2026 | **E** | **Comunicaciones:** El controlador deberá comunicarse correctamente con todos los sensores utilizados. Para la comunicación con la aplicación o interfaz de usuario se podrá utilizar **Wi-Fi, Bluetooth o ambos**, según la arquitectura seleccionada. La ausencia temporal de conexión a Internet no deberá impedir realizar las mediciones básicas. Los datos podrán almacenarse localmente y sincronizarse posteriormente cuando exista conectividad. El ESP32 integra Wi-Fi y Bluetooth y dispone de interfaces para la conexión con sensores. **(Espressif Systems, 2026).** | L.S |
| 30/08/2026 | **E** | **Seguridad:** Los componentes electrónicos deberán encontrarse protegidos frente al contacto directo con humedad, polvo y sustrato. La alimentación eléctrica deberá trabajar con tensiones seguras para el usuario y deberá evitar el contacto directo con partes energizadas. El sistema deberá incorporar protección frente a cortocircuitos, polaridad incorrecta y condiciones eléctricas que puedan comprometer los componentes. Debido a que el sistema trabajará con **NH₃ y HCN**, los ensayos deberán realizarse bajo condiciones controladas y evitando la exposición directa del usuario a los gases. La cámara deberá permanecer cerrada durante la medición. Los niveles de alimentación y las condiciones eléctricas de los módulos deberán respetar las especificaciones de sus fabricantes. **(Espressif Systems, 2026; Winsen Electronics, 2026).** | C.M |
| 30/08/2026 | **E** | **Ergonomía:** El equipo deberá ser manipulable por una sola persona. El peso total objetivo no deberá superar aproximadamente los **3 kg** para facilitar su desplazamiento y manipulación. La interfaz deberá presentar la información mediante términos de fácil comprensión, acompañados de los valores medidos y de la comparación correspondiente. La presentación de resultados deberá facilitar la interpretación de las mediciones sin exigir conocimientos especializados sobre cada sensor. **(Pavelka et al., 2018; Zhang et al., 2025).** | L.S |
| 30/08/2026 | **E** | **Fabricación:** El prototipo deberá poder fabricarse utilizando materiales, sensores y componentes electrónicos disponibles comercialmente. Se priorizarán componentes de fácil adquisición y reemplazo. La cámara podrá fabricarse mediante **impresión 3D**, utilizando un material resistente para las paredes y una tapa transparente independiente que permita el ingreso de iluminación artificial y la observación del cultivo. La fabricación deberá permitir mantener las dimensiones aproximadas de **20 cm × 18 cm × 18 cm** y facilitar el montaje de los sensores de NH₃, HCN y variables complementarias. **(de Klein et al., 2020; Pavelka et al., 2018).** | K.C, A.D |
| 30/08/2026 | **E** | **Control de calidad:** Antes de las pruebas experimentales, los sensores deberán verificarse y, cuando corresponda, calibrarse utilizando procedimientos o referencias apropiadas. Los sensores de **NH₃ y HCN** deberán comprobarse de acuerdo con las especificaciones y procedimientos recomendados por el fabricante. Los sensores de temperatura, humedad, humedad del suelo, conductividad e iluminación deberán contrastarse con referencias adecuadas. Las mediciones deberán repetirse para evaluar estabilidad y error. Se deberá comprobar individualmente el funcionamiento de cada sensor y posteriormente el funcionamiento conjunto del sistema antes de utilizar los datos en Machine Learning. La calibración y verificación son necesarias para obtener mediciones comparables durante los experimentos. **(Winsen Electronics, 2026; de Klein et al., 2020; Harvey et al., 2020).** | L.S |
| 30/08/2026 | **E** | **Montaje:** El diseño deberá ser modular para permitir el montaje y desmontaje de sensores, fuente de alimentación, controlador y demás componentes sin reconstruir completamente el equipo. Las conexiones deberán estar identificadas y aseguradas para evitar desconexiones accidentales durante el experimento. La cámara deberá permitir retirar la maceta o recipiente interno para facilitar el cambio de la planta de papa y la limpieza entre pruebas. **(de Klein et al., 2020; Pavelka et al., 2018).** | L.S, C.M |
| 30/08/2026 | **E** | **Transporte:** El dispositivo deberá ser transportable manualmente entre diferentes espacios de experimentación. La carcasa deberá proteger los componentes durante el traslado. Los sensores deberán contar con un sistema de almacenamiento o protección que reduzca el riesgo de daño durante el transporte. La estructura deberá conservar su geometría y permitir que la cámara pueda cerrarse adecuadamente antes y después de cada ensayo. | L.S |
| 30/08/2026 | **D** | **Uso:** Se desea que el sistema pueda utilizarse de manera repetible para el cultivo de papa bajo condiciones experimentales controladas. La secuencia de utilización deberá ser sencilla:<br><br>**Colocar la planta de papa y su sustrato → instalar o verificar los sensores → establecer las condiciones experimentales → cerrar la cámara → iniciar la medición → registrar las concentraciones de NH₃ y HCN y las variables complementarias → finalizar el ensayo → limpiar la cámara → preparar el siguiente ensayo → repetir la medición.**<br><br>Cuando corresponda, se deberá registrar la aplicación de **urea como condición experimental**. **(Bertora et al., 2018; Pavelka et al., 2018).** | K.C |
| 30/08/2026 | **E** | **Mantenimiento:** Los sensores que estén en contacto con el sustrato deberán poder limpiarse después de cada medición. Los sensores de gases y ambientales deberán poder revisarse y mantenerse de acuerdo con las recomendaciones del fabricante. Los sensores que requieran calibración deberán poder retirarse o calibrarse sin desmontar completamente el prototipo. Los componentes electrónicos deberán poder reemplazarse individualmente en caso de falla. La limpieza y revisión entre experimentos serán necesarias para reducir la contaminación cruzada y mantener la repetibilidad de las mediciones. | A.D |
| 30/08/2026 | **E** | **Costos:** Se buscará que el prototipo utilice componentes comerciales de costo accesible. Como meta inicial de diseño, el costo de los componentes del prototipo no deberá superar aproximadamente **S/ 1500**, sujeto a modificación después de seleccionar y cotizar los sensores definitivos de NH₃ y HCN. Se priorizarán sensores y módulos disponibles comercialmente y de fácil reemplazo, manteniendo como prioridad la calidad y repetibilidad de las mediciones. **(Winsen Electronics, 2026; DFRobot, 2025).** | L.S |
| 30/08/2026 | **E** | **Plazos:** El proyecto comprenderá las etapas de definición del problema, revisión del estado de la tecnología, definición de las variables del cultivo de papa, selección de sensores de NH₃ y HCN, selección de sensores complementarios, diseño de la cámara experimental, diseño electrónico, desarrollo del software, construcción del prototipo, integración, calibración, pruebas experimentales, generación del conjunto de datos, desarrollo y validación del algoritmo de Machine Learning y análisis final de los resultados. Las fechas específicas deberán establecerse mediante el plan de trabajo del proyecto. **(de Klein et al., 2020; Zhang et al., 2025; Jiang et al., 2023).** | A.D, K.C |

---

#  Bibliografía

[1] C. A. M. de Klein, M. J. Harvey, T. J. Clough, S. O. Petersen, D. R. Chadwick, and R. T. Venterea, “Global Research Alliance N₂O chamber methodology guidelines: Introduction, with health and safety considerations,” *Journal of Environmental Quality*, vol. 49, no. 5, pp. 1073–1080, 2020. doi: 10.1002/jeq2.20131.

[2] T. B. Parkin and R. T. Venterea, “Chamber-based trace gas flux measurements,” in *Sampling Protocols*, USDA-ARS, 2010.

[3] C. Bertora, M. Peyron, S. Pelissetti, C. Grignani, and D. Sacco, “Assessment of methane and nitrous oxide fluxes from paddy field by means of static closed chambers maintaining plants within headspace,” *Journal of Visualized Experiments*, no. 139, 2018. doi: 10.3791/56754.

[4] Q. Zhang, W. Wen, Y. Zhuang, L. Zhang, L. Zhai, S. Li, H. Liu, and Y. Du, “Machine learning-driven method for in-situ high-frequency CH₄ measurement in paddy fields based on water-soil-air factors,” *Journal of Environmental Management*, vol. 393, 2025. doi: 10.1016/j.jenvman.2025.127132.

[5] J. Jiang et al., estudios sobre aplicación de Machine Learning y variables ambientales para el análisis de emisiones agrícolas, 2023.

[6] Espressif Systems, “ESP32 Series Datasheet,” Espressif Systems, 2026.

[7] Winsen Electronics, “Sensores electroquímicos de gas para la detección de gases tóxicos industriales y la monitorización de la seguridad,” Winsen Electronics, 2026. Winsen indica que sus sensores electroquímicos incluyen soluciones para NH₃ y HCN, entre otros gases.

[8] Winsen Electronics, “ME3-NH3 Sensor de gas electroquímico,” Winsen Electronics, 2026. El sensor ME3-NH3 está destinado a la detección de NH₃.

[9] Winsen Electronics, “ME3-HCN Sensor de cianuro de hidrógeno,” Winsen Electronics, 2026. El sensor ME3-HCN está destinado a la detección de HCN y se presenta como sensor electroquímico.

[10] Food and Agriculture Organization of the United Nations (FAO), información técnica sobre agricultura, fertilización y manejo de cultivos.

[11] “Blending controlled-release urea and urea under ridge-furrow with plastic film mulching improves yield while mitigating carbon footprint in rainfed potato,” *Scientific Reports*, 2023. El estudio analiza específicamente el uso de urea en cultivo de papa y sus efectos sobre emisiones y productividad.

[12] “Microbial cyanide production in the rhizosphere in relation to potato yield reduction and *Pseudomonas* spp.-mediated plant growth-stimulation,” *Soil Biology and Biochemistry*, vol. 19, no. 4, pp. 451–457, 1987. El estudio reporta producción microbiana de HCN asociada a la rizosfera de papa.