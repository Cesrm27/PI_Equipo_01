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
|:---:|:---|:---|:---:|
| 03/09/2026 | **Función general** | El sistema debe consistir en una cámara experimental cerrada para el monitoreo de una planta joven de papa y su sustrato, permitiendo registrar principalmente las concentraciones de NH₃ (amoniaco gaseoso) y CO₂ (dióxido de carbono), junto con variables ambientales y del suelo. El sistema deberá registrar la identificación del cultivo, las condiciones experimentales y el tiempo transcurrido. La urea podrá registrarse como una condición experimental para estudiar su relación con la volatilización de NH₃, mientras que el CO₂ permitirá observar el intercambio gaseoso asociado a la respiración de los tejidos vegetales y del sustrato. Fuente: Kusa et al., 2008, “Comparison of the closed-chamber and gas concentration gradient methods for measurement of CO₂ and N₂O fluxes in two upland field soils”; Perez-Trejo et al., 1981, “Mobilization of Respiratory Metabolism in Potato Tubers by Carbon Dioxide”; Lee et al., 2024, “Comparison of ammonia volatilization in paddy and field soils fertilized with urea and ammonium sulfate during rice, potato, and Chinese cabbage cultivation”; Baneschi et al., 2023, “Non-steady-state closed dynamic chamber to measure soil CO₂ respiration”; Winsen Electronics, ME3-NH3 Electrochemical Gas Sensor, 2026; Chatzitriantafyllou et al., 2026, “Optimizing Nitrogen Fertilization in Potato Cultivation”. | K.C. |
| 03/09/2026 | **Geometría** | La cámara experimental deberá tener dimensiones aproximadas de **20 × 18 × 18 cm**, equivalente a un volumen interno aproximado de 6,48 L. Deberá disponer de una tapa transparente y espacio suficiente para instalar los sensores sin interferir con la planta. El recipiente para la planta deberá considerar aproximadamente 10 cm de diámetro y 8 cm de altura. | A.D. |
| 03/09/2026 | **Cinemática** | El sistema será de funcionamiento estático durante cada ensayo. La cámara permanecerá cerrada durante el periodo de medición y el cambio de planta, sustrato o condiciones experimentales se realizará manualmente entre ensayos. | C.M. |
| 03/09/2026 | **Fuerzas** | La estructura deberá soportar el peso de la cámara, la planta, el sustrato y los componentes instalados. La tapa deberá permanecer estable durante el ensayo y los soportes de los sensores deberán evitar movimientos que puedan alterar las mediciones. | L.S. |
| 03/09/2026 | **Energía** | El sistema deberá funcionar con una alimentación eléctrica de baja tensión y compatible con los componentes electrónicos seleccionados. El ESP32-WROOM-32D deberá trabajar dentro de un rango de alimentación de 3,0 a 3,6 V. En caso de utilizar el sensor de CO₂ MH-Z19C, este deberá disponer de una alimentación de 5,0 ± 0,1 V y una interfaz compatible con la lógica del ESP32. Fuente: Espressif Systems, “ESP32 Series Datasheet”, 2026; Winsen Electronics, “MH-Z19C NDIR CO₂ Sensor for HVAC and IAQ”, 2026. | K.C. |
| 03/09/2026 | **Materia** | La cámara deberá utilizar materiales resistentes a la humedad, fáciles de limpiar y que no interfieran significativamente con las condiciones experimentales. La tapa deberá ser transparente para permitir el ingreso de iluminación y facilitar la observación de la planta. | A.D. |
| 03/09/2026 | **Señales (Información)** | El sistema deberá manejar las siguientes señales de entrada y salida:<br><br>• **NH₃:** concentración de amoniaco gaseoso.<br>• **CO₂:** concentración de dióxido de carbono gaseoso.<br>• **Temperatura ambiental:** temperatura dentro o alrededor de la cámara.<br>• **Humedad ambiental:** humedad relativa del ambiente de medición.<br>• **Temperatura del suelo:** temperatura del sustrato.<br>• **Humedad del suelo:** contenido de humedad del sustrato.<br>• **Iluminación:** nivel de iluminación presente durante el ensayo.<br>• **Tiempo:** tiempo transcurrido desde el inicio de la medición.<br>• **Identificación del cultivo:** identificación del ensayo o planta evaluada.<br>• **Condición de urea:** condición experimental utilizada para analizar su relación con la emisión de NH₃.<br>• **Comandos del usuario:** inicio, finalización y configuración del ensayo.<br><br>Las salidas deberán mostrar los valores de los sensores, el estado del sistema, las variaciones de NH₃ y CO₂, alertas cuando corresponda, historial de mediciones, tendencias y comparaciones entre condiciones experimentales. Fuente: Winsen Electronics, ME3-NH3 Electrochemical Gas Sensor, 2026; Kusa et al., 2008; Baneschi et al., 2023. | C.M. |
| 03/09/2026 | **Control** | El sistema deberá controlar la secuencia de medición, validación, almacenamiento, análisis y comparación de los datos obtenidos. Cada medición deberá asociarse con el tiempo y con el cultivo o ensayo correspondiente. El sistema deberá identificar valores fuera de rango o inconsistentes y permitir analizar la variación de NH₃ y CO₂ en función del tiempo. También deberá permitir relacionar las concentraciones de NH₃ con condiciones como la aplicación de urea, humedad y temperatura del suelo. Fuente: Kusa et al., 2008; Baneschi et al., 2023; Lee et al., 2024; Sunderlage y Cook, 2018, “Soil Property and Fertilizer Additive Effects on Ammonia Volatilization from Urea”; Klimczyk et al., 2021, “Improving the efficiency of urea-based fertilization leading to reduction in ammonia emission”; Winsen Electronics, 2026. | L.S. |
| 03/09/2026 | **Electrónico (hardware)** | El controlador principal será un **ESP32**, encargado de adquirir y procesar las señales de los sensores. El sistema deberá incorporar sensores para NH₃, CO₂, temperatura y humedad ambiental, temperatura y humedad del suelo e iluminación. Para NH₃ se considerará como referencia el sensor electroquímico **ME3-NH3 de Winsen**. Para CO₂ se considerará un sensor NDIR compatible, tomando como referencia el **MH-Z19C**, disponible en rangos de 400–2000 ppm, 400–5000 ppm y 400–10000 ppm, con comunicación UART/PWM. Los módulos deberán poder reemplazarse individualmente. Fuente: Winsen Electronics, “ME3-NH3 Electrochemical Gas Sensor”, 2026; Winsen Electronics, “MH-Z19C NDIR CO₂ Sensor for HVAC and IAQ”, 2026; Espressif Systems, “ESP32 Series Datasheet”, 2026. | K.C. |
| 03/09/2026 | **Software** | El software deberá permitir adquirir, procesar, almacenar y visualizar los datos obtenidos durante los ensayos. Deberá identificar el cultivo y mostrar las concentraciones de NH₃ y CO₂ junto con las variables ambientales y del suelo. Se deberán generar series temporales, tendencias, variaciones y comparaciones entre condiciones experimentales, incluyendo condiciones con urea. El análisis se realizará mediante métodos de comparación y procesamiento de datos, sin implementar Machine Learning. Fuente: Baneschi et al., 2023; Lee et al., 2024; Chatzitriantafyllou et al., 2026. | A.D. |
| 03/09/2026 | **Comunicaciones** | El ESP32 deberá comunicarse con los sensores mediante interfaces compatibles, como I²C, SPI o UART, según el sensor utilizado. Se podrá utilizar Wi-Fi o Bluetooth para la transmisión de información. El sistema deberá permitir realizar mediciones básicas sin conexión permanente a Internet y almacenar los datos para su posterior sincronización o consulta. En caso de utilizar el MH-Z19C, se considerará su comunicación mediante UART. Fuente: Espressif Systems, “ESP32 Series Datasheet”, 2026; Winsen Electronics, “MH-Z19C NDIR CO₂ Sensor for HVAC and IAQ”, 2026. | C.M. |
| 03/09/2026 | **Seguridad** | Los componentes electrónicos deberán estar protegidos frente a humedad, polvo y contacto accidental con el sustrato. La alimentación eléctrica deberá contar con condiciones seguras de operación y protección frente a cortocircuitos y polaridad incorrecta. La cámara deberá permanecer cerrada durante las mediciones y, cuando sea necesario, deberá ventilarse antes de abrirla para manipular el cultivo. Se deberán respetar las especificaciones eléctricas y de operación de los fabricantes de los sensores y del ESP32. Fuente: Espressif Systems, “ESP32 Series Datasheet”, 2026; Winsen Electronics, “ME3-NH3 Electrochemical Gas Sensor”, 2026; Winsen Electronics, “MH-Z19C NDIR CO₂ Sensor for HVAC and IAQ”, 2026. | L.S. |
| 03/09/2026 | **Ergonomía** | El sistema deberá poder ser utilizado por una sola persona y contar con una interfaz sencilla para iniciar, detener y consultar los ensayos. Se buscará que el peso total aproximado del sistema sea igual o menor a 3 kg, facilitando su manipulación y traslado. Fuente: Baneschi et al., 2023. | K.C. |
| 03/09/2026 | **Fabricación** | La cámara podrá fabricarse mediante impresión 3D utilizando componentes comerciales disponibles. Se deberá mantener la geometría aproximada de 20 × 18 × 18 cm e incorporar una tapa transparente y soportes para los sensores de NH₃, CO₂ y las variables complementarias. El diseño deberá facilitar el acceso a los componentes y la repetición de los ensayos. Fuente: Kusa et al., 2008; Baneschi et al., 2023. | A.D. |
| 03/09/2026 | **Control de calidad** | Antes de realizar los ensayos se deberán verificar y, cuando corresponda, calibrar los sensores. El sensor de NH₃ deberá verificarse siguiendo las recomendaciones del fabricante. El sensor de CO₂ deberá comprobarse utilizando referencias o condiciones conocidas dentro de su rango de operación. Los sensores ambientales y del suelo deberán ser verificados individualmente. Se deberán realizar mediciones repetidas para evaluar la consistencia de los resultados y pruebas individuales e integradas del sistema. Fuente: Winsen Electronics, “ME3-NH3 Electrochemical Gas Sensor”, 2026; Winsen Electronics, “MH-Z19C NDIR CO₂ Sensor for HVAC and IAQ”, 2026; Baneschi et al., 2023; Kusa et al., 2008; Sunderlage y Cook, 2018; Klimczyk et al., 2021. | C.M. |
| 03/09/2026 | **Montaje** | Los sensores deberán instalarse de forma modular y segura, permitiendo su identificación, conexión y reemplazo. Los sensores de NH₃ y CO₂ deberán ubicarse en el espacio de aire de la cámara para realizar las mediciones gaseosas. El recipiente de la planta deberá poder retirarse para facilitar la preparación y limpieza del sistema. En caso de utilizar el MH-Z19C, deberá considerarse su alimentación de 5 V y comunicación UART. Fuente: Kusa et al., 2008; Baneschi et al., 2023; Winsen Electronics, “MH-Z19C NDIR CO₂ Sensor for HVAC and IAQ”, 2026. | L.S. |
| 03/09/2026 | **Transporte** | El sistema deberá ser portátil y permitir su traslado sin afectar la estructura de la cámara ni las conexiones de los sensores. Los componentes electrónicos y sensores deberán permanecer protegidos durante el transporte y conservar la geometría establecida para los ensayos. | K.C. |
| 03/09/2026 | **Uso** | El sistema deberá permitir realizar ensayos repetibles y controlados con plantas de papa. La secuencia de uso será: colocar la planta y el sustrato → instalar y verificar los sensores → establecer las condiciones experimentales → cerrar la cámara → iniciar la medición → registrar NH₃, CO₂ y las variables complementarias → finalizar el ensayo → analizar y comparar los resultados → limpiar el sistema → preparar el siguiente ensayo. La condición de urea se utilizará principalmente para estudiar la relación con la volatilización de NH₃, mientras que el CO₂ permitirá observar el intercambio gaseoso asociado a la respiración. Fuente: Perez-Trejo et al., 1981; Lee et al., 2024; Baneschi et al., 2023; Sunderlage y Cook, 2018. | A.D. |
| 03/09/2026 | **Mantenimiento** | Los sensores que tengan contacto con el suelo deberán limpiarse después de cada ensayo. Se deberán inspeccionar periódicamente los sensores de gases y ambientales, verificar sus conexiones y realizar calibraciones o reemplazos cuando sea necesario. Los componentes deberán poder desmontarse individualmente para facilitar su mantenimiento. La cámara deberá limpiarse entre ensayos para evitar contaminación cruzada. | C.M. |
| 03/09/2026 | **Costos** | El costo total objetivo del prototipo deberá ser aproximadamente igual o menor a **S/ 1500**, sujeto a la selección final de los sensores de NH₃ y CO₂ y de los demás componentes. Se priorizarán componentes comerciales disponibles y técnicamente compatibles con el sistema. Fuente: Winsen Electronics, “ME3-NH3 Electrochemical Gas Sensor”, 2026; Winsen Electronics, “MH-Z19C NDIR CO₂ Sensor for HVAC and IAQ”, 2026. | L.S. |
| 03/09/2026 | **Plazos** | El desarrollo deberá contemplar las siguientes etapas: definición del proyecto → revisión del estado de la tecnología → identificación de variables relevantes en papa → selección de sensores de NH₃ y CO₂ → selección de sensores complementarios → diseño de la cámara → diseño electrónico → desarrollo del software → fabricación → integración → calibración y pruebas → realización de experimentos → generación del conjunto de datos → análisis y comparación de resultados. Las fechas específicas deberán ajustarse al cronograma establecido en el plan de trabajo. Fuente: Kusa et al., 2008; Baneschi et al., 2023; Lee et al., 2024; Chatzitriantafyllou et al., 2026. | K.C. |

# Bibliografía

[1] Kusa, K., Sawamoto, T., Hu, R., & Hatano, R. (2008). *Comparison of the closed-chamber and gas concentration gradient methods for measurement of CO₂ and N₂O fluxes in two upland field soils*. Soil Science and Plant Nutrition, 54(5), 777–785. https://doi.org/10.1111/j.1747-0765.2008.00292.x

[2] Baneschi, I., Raco, B., Magnani, M., Giamberini, M., Lelli, M., Mosca, P., Provenzale, A., Coppo, L., & Guidi, M. (2023). *Non-steady-state closed dynamic chamber to measure soil CO₂ respiration: A protocol to reduce uncertainty*. Frontiers in Environmental Science, 10, 1048948. https://doi.org/10.3389/fenvs.2022.1048948

[3] Perez-Trejo, M. S., Janes, H. W., & Frenkel, C. (1981). *Mobilization of Respiratory Metabolism in Potato Tubers by Carbon Dioxide*. Plant Physiology, 67(3), 514–517. https://doi.org/10.1104/pp.67.3.514

[4] University of California, Davis, Postharvest Research and Extension Center. *Potato (Early Crop)*. Información técnica sobre respiración y producción de CO₂ en tubérculos de papa.

[5] Lee, Y.-J., Im, E.-C., Lee, G., Hong, S.-C., Lee, C.-G., & Park, S.-J. (2024). *Comparison of ammonia volatilization in paddy and field soils fertilized with urea and ammonium sulfate during rice, potato, and Chinese cabbage cultivation*. Atmospheric Pollution Research, 15(4), 102049. https://doi.org/10.1016/j.apr.2024.102049

[6] Winsen Electronics. (2026). *ME3-NH3 Electrochemical Gas Sensor*. Winsen Electronics.

[7] Winsen Electronics. (2026). *CO₂ Sensor*. Winsen Electronics.

[8] Espressif Systems. (2026). *ESP32 Series Datasheet*. Espressif Systems.

[9] Sunderlage, B., & Cook, R. L. (2018). *Soil Property and Fertilizer Additive Effects on Ammonia Volatilization from Urea*. Soil Science Society of America Journal, 82(1), 253–259. https://doi.org/10.2136/sssaj2017.05.0151

[10] Klimczyk, M., Siczek, A., & Schimmelpfennig, L. (2021). *Improving the efficiency of urea-based fertilization leading to reduction in ammonia emission*. Science of the Total Environment, 771, 145483. https://doi.org/10.1016/j.scitotenv.2021.145483

[11] Chatzitriantafyllou, M., Stavropoulos, P., Kallergi, S., Mavroeidis, M., Roussis, I., Karydogianni, S., Bilalis, D., & Kakabouki, I. (2026). *Optimizing Nitrogen Fertilization in Potato (Solanum tuberosum L.) Cultivation: A Review Regarding Inhibitor Use, Multifaceted Assessment Indicators, and Pathways to Sustainable Intensification*. Applied Sciences, 16(5), 2565. https://doi.org/10.3390/app16052565

[12] Winsen Electronics. (2026). *MH-Z19C NDIR CO₂ Sensor for HVAC and IAQ*. Winsen Electronics.