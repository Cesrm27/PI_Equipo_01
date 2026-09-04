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
    <td>GREENPLANT AI – Sistema inteligente para el monitoreo experimental del cultivo de papa y la detección de NH₃ y CO₂.</td>
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
| 30/08/2026 | **E** | **Función general:** El sistema deberá permitir realizar mediciones experimentales de gases presentes en el interior de una cámara cerrada que contenga una planta joven de papa junto con su sustrato. El sistema deberá monitorear principalmente **amoníaco gaseoso (NH₃)** y **dióxido de carbono (CO₂)**, además de registrar variables ambientales y del suelo relacionadas con el experimento. Las mediciones deberán almacenarse junto con la identificación del cultivo, las condiciones experimentales y el tiempo de experimentación, permitiendo analizar la variación de las concentraciones gaseosas bajo condiciones controladas. Cuando corresponda, la aplicación de **urea podrá registrarse como una condición experimental** para estudiar su relación con la concentración de NH₃, sin que la urea sea medida directamente por el sistema. El CO₂ constituye una variable de interés debido a que la respiración de los tejidos vegetales y del sustrato contribuye al intercambio de este gas, pudiendo monitorearse su variación dentro de una cámara de volumen conocido. **(Kusa et al., 2008; Perez-Trejo et al., 1981; Lee et al., 2024; Baneschi et al., 2023; Winsen Electronics, 2026; Chatzitriantafyllou et al., 2026).** | C.M, K.C, A.D, L.S |
| 30/08/2026 | **E** | **Geometría:** El prototipo deberá presentar una cámara experimental cerrada, portátil y de dimensiones aproximadas de **20 cm × 18 cm × 18 cm**, destinada a contener una planta joven de papa y su sustrato durante las mediciones. La cámara deberá disponer de una tapa superior transparente que permita el ingreso de iluminación artificial y facilite la observación del cultivo. En el interior deberá existir espacio suficiente para instalar los sensores sin obstruir significativamente el crecimiento de la planta. La planta deberá colocarse en una maceta o recipiente interno de aproximadamente **10 cm de diámetro y 8 cm de altura**. La geometría deberá permitir mantener un volumen de medición definido y facilitar la limpieza y sustitución del cultivo entre pruebas. | A.D |
| 30/08/2026 | **E** | **Cinemática:** El prototipo no requerirá mecanismos de movimiento continuo durante la operación. La cámara permanecerá estática durante cada medición para evitar variaciones innecesarias del volumen interno y perturbaciones en las concentraciones de **NH₃ y CO₂**. La sustitución de la planta o maceta se realizará manualmente entre experimentos. La tapa deberá poder abrirse y cerrarse para permitir la colocación, retiro y limpieza del sistema. | K.C |
| 30/08/2026 | **E** | **Fuerzas:** La estructura de la cámara deberá soportar su propio peso, el peso de la maceta con el sustrato y la manipulación manual durante la instalación y retiro de los cultivos. La tapa deberá permanecer correctamente cerrada durante las mediciones para reducir pérdidas de gases y mantener estable el volumen experimental. Los soportes de los sensores deberán resistir la manipulación y permanecer firmes durante el ensayo sin alterar significativamente la posición de los sensores. | L.S |
| 30/08/2026 | **E** | **Energía:** El sistema deberá funcionar mediante una fuente de alimentación de bajo voltaje compatible con el ESP32 y los sensores utilizados. Se deberá priorizar una fuente estable que permita mantener el funcionamiento durante todo el periodo experimental.<br><br>• La iluminación artificial instalada sobre la tapa transparente deberá contar con una alimentación independiente o compatible con el sistema eléctrico del prototipo, evitando afectar las mediciones de los sensores.<br>• El sistema deberá permitir verificar la disponibilidad de alimentación para evitar interrupciones durante la adquisición de datos.<br>• Los sensores deberán alimentarse respetando sus niveles de tensión especificados por los fabricantes. El **ESP32-WROOM-32D opera con una alimentación de 3,0 a 3,6 V**. En caso de utilizar un sensor de CO₂ como el **MH-Z19C**, deberá considerarse su alimentación de **5,0 ± 0,1 V** y su interfaz de comunicación de nivel lógico compatible con 3,3 V.<br><br>**(Espressif Systems, 2026; Winsen Electronics, 2026).** | A.D |
| 30/08/2026 | **E** | **Materia:** El sistema deberá permitir introducir una planta joven de papa junto con su sustrato dentro de la cámara experimental. Los materiales que estén en contacto con el sustrato y el ambiente húmedo deberán ser resistentes a la humedad y permitir una limpieza adecuada entre experimentos. La cámara deberá utilizar materiales que permitan mantener un volumen cerrado y estable durante las mediciones. La tapa deberá utilizar un material transparente que permita el paso de la iluminación artificial y la observación del cultivo. La elección de los materiales deberá evitar que estos interfieran significativamente con las mediciones de los gases o variables ambientales. | L.S |
| 30/08/2026 | **E** | **Señales (Información):** El sistema deberá contar con señales de entrada y salida asociadas al proceso de medición, registro, análisis y comparación de las variables registradas durante el cultivo experimental de papa.<br><br>**Señales de entrada:**<br>• Concentración de NH₃.<br>• Concentración de CO₂.<br>• Temperatura del suelo.<br>• Humedad del suelo.<br>• Temperatura ambiental.<br>• Humedad ambiental.<br>• Conductividad eléctrica del suelo.<br>• Intensidad de iluminación.<br>• Identificación del cultivo.<br>• Tiempo transcurrido desde el inicio de la medición.<br>• Condición experimental relacionada con la aplicación de urea, cuando corresponda.<br>• Comandos e información ingresada por el usuario.<br><br>**Señales de salida:**<br>• Valores obtenidos de los sensores.<br>• Estado de funcionamiento de los sensores.<br>• Variación de las concentraciones de NH₃ y CO₂.<br>• Alertas ante lecturas anormales o datos no válidos.<br>• Registro e historial de mediciones.<br>• Tendencias identificadas entre las variables registradas.<br>• Relaciones entre las variables medidas.<br>• Comparación de resultados entre diferentes condiciones experimentales.<br><br>Los sensores de gases permiten transformar la concentración del gas objetivo en una señal que puede ser procesada por el sistema de adquisición. Los sistemas de cámara cerrada han sido utilizados para evaluar la variación de CO₂ y otros gases mediante el seguimiento de su concentración en función del tiempo. **(Winsen Electronics, 2026; Kusa et al., 2008; Baneschi et al., 2023).** | K.C, C.M |
| 30/08/2026 | **E** | **Control:** El sistema de control deberá coordinar la adquisición de datos provenientes de los sensores y verificar que las mediciones se encuentren dentro de rangos operativos antes de registrarlas. El sistema deberá ejecutar la secuencia de **medición, validación, almacenamiento, análisis y comparación**. Durante cada experimento deberá registrar el tiempo de medición y asociar las lecturas al cultivo de papa evaluado. El sistema deberá detectar lecturas fuera del rango operativo o inconsistentes y advertir al usuario para evitar que datos no válidos sean utilizados en el análisis. Las series de concentración de **NH₃ y CO₂ en función del tiempo** podrán utilizarse para analizar la variación de los gases durante el experimento. En el caso del NH₃, la concentración podrá analizarse en relación con condiciones como la aplicación de urea, humedad, temperatura y propiedades del suelo. **(Kusa et al., 2008; Baneschi et al., 2023; Lee et al., 2024; Sunderlage & Cook, 2018; Klimczyk et al., 2021; Winsen Electronics, 2026).** | A.D, K.C |
| 30/08/2026 | **E** | **Electrónico (hardware):** El sistema utilizará un **ESP32** como controlador principal para adquirir información de los sensores y comunicarse con una interfaz externa. El prototipo deberá integrar sensores para **NH₃ y CO₂**, además de sensores para temperatura del suelo, humedad del suelo, temperatura y humedad ambiental, conductividad eléctrica e iluminación. Para la detección de NH₃ se considera como referencia un sensor electroquímico de la familia **ME3-NH3 de Winsen**, sujeto a disponibilidad y validación final del componente. Para CO₂ se podrá utilizar un sensor NDIR compatible con el ESP32, como referencia el **MH-Z19C**, que permite medir CO₂ en rangos de 400 a 2000 ppm, 400 a 5000 ppm o 400 a 10000 ppm, según la configuración seleccionada, y dispone de comunicación UART y PWM. Los demás sensores deberán seleccionarse de acuerdo con los requerimientos del experimento. Los módulos deberán ser reemplazables para facilitar el mantenimiento y futuras mejoras. **(Winsen Electronics, 2026; Espressif Systems, 2026).** | K.C, L.S |
| 30/08/2026 | **E** | **Software:** El software deberá permitir adquirir, procesar, almacenar y visualizar la información obtenida de los sensores. Deberá incluir una interfaz que permita identificar el cultivo de papa y observar las concentraciones de **NH₃ y CO₂** junto con las variables ambientales y del suelo. El sistema deberá procesar las mediciones como series temporales, permitiendo identificar **tendencias, variaciones y relaciones entre las variables registradas**. Los resultados deberán poder compararse entre diferentes condiciones experimentales, incluyendo, cuando corresponda, diferentes condiciones de aplicación de urea. El análisis deberá basarse en los datos experimentales obtenidos y no requerirá el uso de algoritmos de Machine Learning. **(Baneschi et al., 2023; Lee et al., 2024; Chatzitriantafyllou et al., 2026).** | A.D, K.C |
| 30/08/2026 | **E** | **Comunicaciones:** El controlador deberá comunicarse correctamente con todos los sensores utilizados. Para la comunicación con la aplicación o interfaz de usuario se podrá utilizar **Wi-Fi, Bluetooth o ambos**, según la arquitectura seleccionada. La ausencia temporal de conexión a Internet no deberá impedir realizar las mediciones básicas. Los datos podrán almacenarse localmente y sincronizarse posteriormente cuando exista conectividad. El ESP32 integra Wi-Fi y Bluetooth y dispone de interfaces como **I²C, SPI y UART** para la conexión con diferentes sensores y módulos. En caso de utilizar el sensor MH-Z19C, la comunicación con el ESP32 podrá realizarse mediante UART, utilizando su interfaz de nivel lógico compatible con 3,3 V. **(Espressif Systems, 2026; Winsen Electronics, 2026).** | L.S |
| 30/08/2026 | **E** | **Seguridad:** Los componentes electrónicos deberán encontrarse protegidos frente al contacto directo con humedad, polvo y sustrato. La alimentación eléctrica deberá trabajar con tensiones adecuadas para el usuario y deberá evitar el contacto directo con partes energizadas. El sistema deberá incorporar protección frente a cortocircuitos, polaridad incorrecta y condiciones eléctricas que puedan comprometer los componentes. Debido a que el sistema trabajará con **NH₃ y CO₂**, los ensayos deberán realizarse bajo condiciones controladas, evitando la exposición directa del usuario a concentraciones elevadas de gases. La cámara deberá permanecer cerrada durante la medición y deberá realizarse una adecuada ventilación antes de abrirla cuando las condiciones experimentales lo requieran. Los niveles de alimentación y las condiciones eléctricas de los módulos deberán respetar las especificaciones de sus fabricantes. **(Espressif Systems, 2026; Winsen Electronics, 2026).** | C.M |
| 30/08/2026 | **E** | **Ergonomía:** El equipo deberá ser manipulable por una sola persona. El peso total objetivo no deberá superar aproximadamente los **3 kg** para facilitar su desplazamiento y manipulación. La interfaz deberá presentar la información mediante términos de fácil comprensión, acompañados de los valores medidos y de la comparación correspondiente. La presentación de resultados deberá facilitar la interpretación de las mediciones sin exigir conocimientos especializados sobre cada sensor. **(Baneschi et al., 2023).** | L.S |
| 30/08/2026 | **E** | **Fabricación:** El prototipo deberá poder fabricarse utilizando materiales, sensores y componentes electrónicos disponibles comercialmente. Se priorizarán componentes de fácil adquisición y reemplazo. La cámara podrá fabricarse mediante **impresión 3D**, utilizando un material resistente para las paredes y una tapa transparente independiente que permita el ingreso de iluminación artificial y la observación del cultivo. La fabricación deberá permitir mantener las dimensiones aproximadas de **20 cm × 18 cm × 18 cm** y facilitar el montaje de los sensores de NH₃, CO₂ y variables complementarias. El diseño de cámaras cerradas para medición de gases debe considerar aspectos como dimensiones, materiales, estanqueidad y condiciones que permitan obtener mediciones reproducibles. **(Kusa et al., 2008; Baneschi et al., 2023).** | K.C, A.D |
| 30/08/2026 | **E** | **Control de calidad:** Antes de las pruebas experimentales, los sensores deberán verificarse y, cuando corresponda, calibrarse utilizando procedimientos o referencias apropiadas. El sensor de **NH₃** deberá comprobarse de acuerdo con las especificaciones y procedimientos recomendados por el fabricante. El sensor de **CO₂** deberá verificarse utilizando referencias o concentraciones conocidas apropiadas para el rango de medición seleccionado. Los sensores de temperatura, humedad, humedad del suelo, conductividad e iluminación deberán contrastarse con referencias adecuadas. Las mediciones deberán repetirse para evaluar estabilidad y error. Se deberá comprobar individualmente el funcionamiento de cada sensor y posteriormente el funcionamiento conjunto del sistema antes de utilizar los datos en el análisis. En las mediciones de CO₂ mediante cámaras cerradas resulta importante considerar la calibración, la repetición de las mediciones y la selección adecuada del intervalo temporal de análisis. Las condiciones del suelo también pueden influir en la volatilización de NH₃ cuando se utiliza urea, por lo que deberán mantenerse controladas o registrarse durante los ensayos. **(Winsen Electronics, 2026; Baneschi et al., 2023; Kusa et al., 2008; Sunderlage & Cook, 2018; Klimczyk et al., 2021).** | L.S |
| 30/08/2026 | **E** | **Montaje:** El diseño deberá ser modular para permitir el montaje y desmontaje de sensores, fuente de alimentación, controlador y demás componentes sin reconstruir completamente el equipo. Las conexiones deberán estar identificadas y aseguradas para evitar desconexiones accidentales durante el experimento. La cámara deberá permitir retirar la maceta o recipiente interno para facilitar el cambio de la planta de papa y la limpieza entre pruebas. Los sensores de NH₃ y CO₂ deberán ubicarse dentro del espacio de medición de forma que puedan registrar el aire del interior de la cámara sin interferir con el crecimiento de la planta. En caso de utilizar un sensor MH-Z19C, deberá considerarse su alimentación de 5 V y su conexión de comunicación UART con el ESP32. **(Kusa et al., 2008; Baneschi et al., 2023; Winsen Electronics, 2026).** | L.S, C.M |
| 30/08/2026 | **E** | **Transporte:** El dispositivo deberá ser transportable manualmente entre diferentes espacios de experimentación. La carcasa deberá proteger los componentes durante el traslado. Los sensores deberán contar con un sistema de almacenamiento o protección que reduzca el riesgo de daño durante el transporte. La estructura deberá conservar su geometría y permitir que la cámara pueda cerrarse adecuadamente antes y después de cada ensayo. | L.S |
| 30/08/2026 | **D** | **Uso:** Se desea que el sistema pueda utilizarse de manera repetible para el cultivo de papa bajo condiciones experimentales controladas. La secuencia de utilización deberá ser sencilla:<br><br>**Colocar la planta de papa y su sustrato → instalar o verificar los sensores → establecer las condiciones experimentales → cerrar la cámara → iniciar la medición → registrar las concentraciones de NH₃ y CO₂ y las variables complementarias → finalizar el ensayo → analizar y comparar los resultados → limpiar la cámara → preparar el siguiente ensayo → repetir la medición.**<br><br>Cuando corresponda, se deberá registrar la aplicación de **urea como condición experimental**, principalmente para analizar su relación con la concentración de NH₃. La concentración de CO₂ podrá utilizarse como indicador de la actividad respiratoria dentro de la cámara. **(Perez-Trejo et al., 1981; Lee et al., 2024; Baneschi et al., 2023; Sunderlage & Cook, 2018).** | K.C |
| 30/08/2026 | **E** | **Mantenimiento:** Los sensores que estén en contacto con el sustrato deberán poder limpiarse después de cada medición. Los sensores de gases y ambientales deberán poder revisarse y mantenerse de acuerdo con las recomendaciones del fabricante. Los sensores que requieran calibración deberán poder retirarse o calibrarse sin desmontar completamente el prototipo. Los componentes electrónicos deberán poder reemplazarse individualmente en caso de falla. La limpieza y revisión entre experimentos serán necesarias para reducir la contaminación cruzada y mantener la repetibilidad de las mediciones. | A.D |
| 30/08/2026 | **E** | **Costos:** Se buscará que el prototipo utilice componentes comerciales de costo accesible. Como meta inicial de diseño, el costo de los componentes del prototipo no deberá superar aproximadamente **S/ 1500**, sujeto a modificación después de seleccionar y cotizar los sensores definitivos de NH₃ y CO₂. Se priorizarán sensores y módulos disponibles comercialmente y de fácil reemplazo, manteniendo como prioridad la calidad y repetibilidad de las mediciones. **(Winsen Electronics, 2026).** | L.S |
| 30/08/2026 | **E** | **Plazos:** El proyecto comprenderá las etapas de definición del problema, revisión del estado de la tecnología, definición de las variables del cultivo de papa, selección de sensores de NH₃ y CO₂, selección de sensores complementarios, diseño de la cámara experimental, diseño electrónico, desarrollo del software, construcción del prototipo, integración, calibración, pruebas experimentales, generación del conjunto de datos, análisis y comparación de los resultados. Las fechas específicas deberán establecerse mediante el plan de trabajo del proyecto. **(Kusa et al., 2008; Baneschi et al., 2023; Lee et al., 2024; Chatzitriantafyllou et al., 2026).** | A.D, K.C |

---

# BIBLIOGRAFÍA

[1] K. Kusa, T. Sawamoto, R. Hu, and R. Hatano, “Comparison of the closed-chamber and gas concentration gradient methods for measurement of CO₂ and N₂O fluxes in two upland field soils,” *Soil Science and Plant Nutrition*, vol. 54, no. 5, pp. 777–785, 2008. doi: 10.1111/j.1747-0765.2008.00292.x.

[2] I. Baneschi, B. Raco, M. Magnani, M. Giamberini, M. Lelli, P. Mosca, A. Provenzale, L. Coppo, and M. Guidi, “Non-steady-state closed dynamic chamber to measure soil CO₂ respiration: A protocol to reduce uncertainty,” *Frontiers in Environmental Science*, vol. 10, 1048948, 2023. doi: 10.3389/fenvs.2022.1048948.

[3] M. S. Perez-Trejo, H. W. Janes, and C. Frenkel, “Mobilization of Respiratory Metabolism in Potato Tubers by Carbon Dioxide,” *Plant Physiology*, vol. 67, no. 3, pp. 514–517, 1981. doi: 10.1104/pp.67.3.514.

[4] University of California, Davis, Postharvest Research and Extension Center, “Potato (Early Crop),” información técnica sobre tasas de respiración y producción de CO₂ de tubérculos de papa.

[5] Y.-J. Lee, E.-C. Im, G. Lee, S.-C. Hong, C.-G. Lee, and S.-J. Park, “Comparison of ammonia volatilization in paddy and field soils fertilized with urea and ammonium sulfate during rice, potato, and Chinese cabbage cultivation,” *Atmospheric Pollution Research*, vol. 15, no. 4, 102049, 2024. doi: 10.1016/j.apr.2024.102049.

[6] Winsen Electronics, “ME3-NH3 Electrochemical Gas Sensor,” Winsen Electronics, 2026.

[7] Winsen Electronics, “CO₂ Sensor,” Winsen Electronics, 2026. La familia de sensores de CO₂ de Winsen incluye dispositivos basados en tecnología NDIR, con diferentes rangos de medición y métodos de salida.

[8] Espressif Systems, “ESP32 Series Datasheet,” Espressif Systems, 2026.

[9] B. Sunderlage and R. L. Cook, “Soil Property and Fertilizer Additive Effects on Ammonia Volatilization from Urea,” *Soil Science Society of America Journal*, vol. 82, no. 1, pp. 253–259, 2018. doi: 10.2136/sssaj2017.05.0151.

[10] M. Klimczyk, A. Siczek, and L. Schimmelpfennig, “Improving the efficiency of urea-based fertilization leading to reduction in ammonia emission,” *Science of the Total Environment*, vol. 771, 145483, 2021. doi: 10.1016/j.scitotenv.2021.145483.

[11] M. Chatzitriantafyllou, P. Stavropoulos, S. Kallergi, M. Mavroeidis, I. Roussis, S. Karydogianni, D. Bilalis, and I. Kakabouki, “Optimizing Nitrogen Fertilization in Potato (*Solanum tuberosum* L.) Cultivation: A Review Regarding Inhibitor Use, Multifaceted Assessment Indicators, and Pathways to Sustainable Intensification,” *Applied Sciences*, vol. 16, no. 5, 2565, 2026. doi: 10.3390/app16052565.

[12] Winsen Electronics, “MH-Z19C NDIR CO₂ Sensor for HVAC and IAQ,” Winsen Electronics, 2026. Sensor NDIR para CO₂ con rangos de detección configurables de 400–2000 ppm, 400–5000 ppm y 400–10000 ppm, salida UART/PWM y alimentación de 5,0 ± 0,1 V.