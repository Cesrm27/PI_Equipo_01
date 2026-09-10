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
| Shedira Lumeris Sihuincha Palacin | Apoyo en la integración, pruebas, documentación y validación del prototipo. | 25% |

---

# Lista de Exigencias

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
| 03/09/2026 | **Función general** | **REQ-001:** El sistema deberá implementar una cámara experimental cerrada para el monitoreo de una planta joven de papa y su sustrato, permitiendo registrar principalmente las concentraciones de NH₃ (amoniaco gaseoso) y CO₂ (dióxido de carbono), junto con variables ambientales y del suelo. El sistema deberá registrar la identificación del cultivo, las condiciones experimentales y el tiempo transcurrido durante cada ensayo. La condición de aplicación de urea podrá registrarse como variable experimental para analizar su relación con la volatilización de NH₃. Asimismo, la medición de CO₂ permitirá observar el intercambio gaseoso asociado a la respiración vegetal y del sustrato. Fuente: Kusa et al., 2008; Perez-Trejo et al., 1981; Lee et al., 2024; Baneschi et al., 2023; Winsen Electronics, 2026. | K.C. |
| 03/09/2026 | **Geometría** | **REQ-002:** La cámara experimental deberá presentar dimensiones aproximadas de 20 × 18 × 18 cm, equivalente a un volumen interno aproximado de 6,48 L. Deberá disponer de una tapa transparente y espacio suficiente para instalar los sensores sin interferir con el crecimiento de la planta. El recipiente destinado al cultivo deberá considerar aproximadamente 10 cm de diámetro y 8 cm de altura para contener el sustrato y la planta de papa. | A.D. |
| 03/09/2026 | **Cinemática** | **REQ-003:** El sistema deberá funcionar bajo una condición estática durante cada ensayo. La cámara permanecerá cerrada durante la etapa de medición, mientras que el cambio de planta, sustrato o condiciones experimentales se realizará manualmente entre ensayos. No se requerirá movimiento automático de componentes durante la adquisición de datos. | C.M. |
| 03/09/2026 | **Fuerzas** | **REQ-004:** La estructura deberá soportar el peso de la cámara experimental, la planta, el sustrato y los componentes electrónicos instalados. La tapa deberá permanecer estable durante el ensayo y los soportes de sensores deberán evitar desplazamientos que alteren las mediciones. Para el diseño mecánico se considerará una carga máxima aproximada de 3 kg. La fuerza generada por el peso será calculada mediante: F = m × g. Considerando una masa de 3 kg y una gravedad de 9,81 m/s²: F = 3 kg × 9,81 m/s² = 29,43 N. La estructura deberá soportar como mínimo esta fuerza considerando un factor de seguridad para evitar deformaciones. | L.S. |
| 03/09/2026 | **Energía** | **REQ-005:** El sistema deberá funcionar mediante una alimentación eléctrica de baja tensión compatible con los componentes seleccionados. El ESP32-WROOM-32D deberá operar dentro de un rango de alimentación de 3,0 a 3,6 V. En caso de utilizar el sensor de CO₂ MH-Z19C, este deberá contar con una alimentación de 5,0 ± 0,1 V y comunicación compatible con la lógica del ESP32. La alimentación deberá garantizar un funcionamiento continuo durante los ensayos experimentales. Fuente: Espressif Systems, “ESP32 Series Datasheet”, 2026; Winsen Electronics, “MH-Z19C NDIR CO₂ Sensor”, 2026. | K.C. |
| 03/09/2026 | **Materia** | **REQ-006:** La cámara experimental deberá utilizar materiales resistentes a la humedad, fáciles de limpiar y que no interfieran significativamente con las condiciones experimentales del cultivo. La estructura principal podrá fabricarse utilizando acrílico transparente para permitir la observación de la planta y mantener condiciones visuales adecuadas durante el ensayo. Los soportes internos y elementos de fijación podrán fabricarse mediante impresión 3D utilizando PLA o PETG debido a su facilidad de fabricación, disponibilidad comercial y resistencia mecánica. El recipiente destinado al cultivo deberá utilizar un material plástico resistente a humedad y contacto con el sustrato, como polipropileno (PP) o equivalente. Los elementos de sellado podrán elaborarse mediante silicona o juntas de goma para reducir pérdidas de aire durante las mediciones. | A.D. |
| 03/09/2026 | **Señales (Información)** | **REQ-007:** El sistema deberá adquirir, procesar, almacenar y mostrar las siguientes señales de entrada y salida:<br><br>**Entradas:**<br>• Concentración de NH₃: medición del amoniaco gaseoso presente dentro de la cámara.<br>• Concentración de CO₂: medición del dióxido de carbono generado durante el ensayo.<br>• Temperatura ambiental: temperatura dentro o alrededor de la cámara experimental.<br>• Humedad ambiental: humedad relativa durante la medición.<br>• Temperatura del suelo: temperatura del sustrato donde se encuentra la planta.<br>• Humedad del suelo: contenido de humedad del sustrato.<br>• Iluminación: nivel de iluminación presente durante el ensayo.<br>• Tiempo: duración transcurrida desde el inicio de la medición.<br>• Identificación del cultivo: identificación del ensayo o planta evaluada.<br>• Condición experimental de urea: variable utilizada para estudiar su relación con la volatilización de NH₃.<br>• Comandos del usuario: inicio, finalización y configuración del ensayo.<br><br>**Salidas:**<br>• Visualización de valores medidos por los sensores.<br>• Registro histórico de datos.<br>• Variaciones de NH₃ y CO₂ en función del tiempo.<br>• Tendencias y comparaciones entre condiciones experimentales.<br>• Alertas cuando se detecten valores fuera de los rangos establecidos.<br><br>Fuente: Winsen Electronics, ME3-NH3 Electrochemical Gas Sensor, 2026; Kusa et al., 2008; Baneschi et al., 2023. | C.M. |
| 03/09/2026 | **Control** | **REQ-008:** El sistema deberá controlar la secuencia de adquisición, validación, almacenamiento y análisis de los datos obtenidos durante los ensayos. Cada medición deberá estar asociada al tiempo transcurrido y al cultivo o condición experimental correspondiente. El sistema deberá identificar datos inconsistentes o valores fuera del rango esperado y permitir analizar la variación de NH₃ y CO₂ respecto a variables como la aplicación de urea, humedad y temperatura del suelo. El procesamiento permitirá realizar comparaciones entre ensayos sin implementar algoritmos de Machine Learning. Fuente: Kusa et al., 2008; Baneschi et al., 2023; Lee et al., 2024. | L.S. |
| 03/09/2026 | **Electrónico (hardware)** | **REQ-009:** El controlador principal del sistema deberá ser un ESP32 encargado de adquirir y procesar las señales provenientes de los sensores. El sistema deberá incorporar sensores para NH₃, CO₂, temperatura y humedad ambiental, temperatura y humedad del suelo e iluminación.<br><br>Para la medición de NH₃ se considerará como referencia el sensor electroquímico ME3-NH3 de Winsen. Para la medición de CO₂ se considerará un sensor NDIR compatible, tomando como referencia el MH-Z19C con rangos de medición disponibles de 400–2000 ppm, 400–5000 ppm y 400–10000 ppm, utilizando comunicación UART/PWM.<br><br>Los módulos deberán instalarse de forma modular para permitir su reemplazo individual en caso de mantenimiento o actualización. Fuente: Winsen Electronics, ME3-NH3 Electrochemical Gas Sensor, 2026; Winsen Electronics, MH-Z19C NDIR CO₂ Sensor, 2026; Espressif Systems, ESP32 Series Datasheet, 2026. | K.C. |
| 03/09/2026 | **Software** | **REQ-010:** El software deberá permitir la adquisición, procesamiento, almacenamiento y visualización de los datos obtenidos durante los ensayos experimentales. El sistema deberá identificar cada cultivo o ensayo y mostrar las concentraciones de NH₃ y CO₂ junto con las variables ambientales y del suelo registradas.<br><br>El software deberá generar series temporales, tendencias, variaciones y comparaciones entre diferentes condiciones experimentales, incluyendo ensayos con presencia de urea. El procesamiento de datos se realizará mediante métodos estadísticos y de comparación, sin implementar Machine Learning. Fuente: Baneschi et al., 2023; Lee et al., 2024; Chatzitriantafyllou et al., 2026. | A.D. |
| 03/09/2026 | **Comunicaciones** | **REQ-011:** El ESP32 deberá comunicarse con los sensores mediante interfaces compatibles según el modelo seleccionado, pudiendo utilizar protocolos como I²C, SPI o UART. El sistema podrá utilizar comunicación inalámbrica mediante Wi-Fi o Bluetooth para la transmisión de información.<br><br>El funcionamiento básico del sistema no deberá depender de una conexión permanente a Internet, permitiendo almacenar datos localmente para su posterior consulta o sincronización. En caso de utilizar el sensor MH-Z19C, se considerará la comunicación mediante UART. Fuente: Espressif Systems, ESP32 Series Datasheet, 2026; Winsen Electronics, MH-Z19C NDIR CO₂ Sensor, 2026. | C.M. |
| 03/09/2026 | **Seguridad** | **REQ-012:** El sistema deberá proteger los componentes electrónicos frente a humedad, polvo y contacto accidental con el sustrato. La alimentación eléctrica deberá contar con condiciones seguras de operación, incluyendo protección frente a cortocircuitos y conexión incorrecta de polaridad.<br><br>Durante los ensayos, la cámara deberá permanecer cerrada para mantener condiciones controladas de medición. Cuando sea necesario manipular la planta o el interior de la cámara, se deberá realizar una ventilación previa para evitar acumulación de gases antes de abrir el sistema.<br><br>Los sensores y componentes electrónicos deberán operar respetando las especificaciones técnicas proporcionadas por los fabricantes. Fuente: Espressif Systems, ESP32 Series Datasheet, 2026; Winsen Electronics, ME3-NH3 Electrochemical Gas Sensor, 2026; Winsen Electronics, MH-Z19C NDIR CO₂ Sensor, 2026. | L.S. |
| 03/09/2026 | **Ergonomía** | **REQ-013:** El sistema deberá estar diseñado para ser utilizado por una sola persona, permitiendo realizar las operaciones de instalación, configuración, medición y consulta de resultados mediante una interfaz sencilla.<br><br>El peso total aproximado del prototipo deberá ser igual o menor a 3 kg con el objetivo de facilitar su manipulación y traslado. La ubicación de los sensores y componentes deberá permitir un acceso sencillo para instalación, mantenimiento y verificación. Fuente: Baneschi et al., 2023. | K.C. |
| 03/09/2026 | **Fabricación** | **REQ-014:** La cámara experimental deberá fabricarse utilizando procesos accesibles y componentes comerciales disponibles. La geometría principal deberá mantener dimensiones aproximadas de 20 × 18 × 18 cm e incorporar una tapa transparente, soportes para sensores y espacio suficiente para el recipiente de cultivo.<br><br>La estructura podrá fabricarse mediante impresión 3D utilizando PLA o PETG para los soportes y piezas auxiliares, mientras que la cubierta transparente podrá elaborarse mediante acrílico. El diseño deberá facilitar el montaje, desmontaje y repetición de los ensayos experimentales. Fuente: Kusa et al., 2008; Baneschi et al., 2023. | A.D. |
| 03/09/2026 | **Control de calidad** | **REQ-015:** Antes de realizar los ensayos experimentales se deberá verificar el correcto funcionamiento y respuesta de cada sensor instalado en el sistema.<br><br>El sensor de NH₃ deberá ser evaluado siguiendo las recomendaciones del fabricante. El sensor de CO₂ deberá comprobarse utilizando condiciones conocidas dentro de su rango de operación. Los sensores ambientales y del suelo deberán verificarse individualmente antes de integrarlos al sistema completo.<br><br>Se deberán realizar pruebas individuales e integradas del prototipo, incluyendo mediciones repetidas para evaluar la consistencia y estabilidad de los resultados obtenidos. Fuente: Winsen Electronics, ME3-NH3 Electrochemical Gas Sensor, 2026; Winsen Electronics, MH-Z19C NDIR CO₂ Sensor, 2026; Baneschi et al., 2023; Kusa et al., 2008. | C.M. |
| 03/09/2026 | **Montaje** | **REQ-016:** Los sensores deberán instalarse de forma modular y segura, permitiendo su identificación, conexión y reemplazo individual. Los sensores destinados a la medición de NH₃ y CO₂ deberán ubicarse en el espacio de aire interno de la cámara para registrar correctamente las concentraciones gaseosas.<br><br>El recipiente de la planta deberá poder retirarse para facilitar la preparación del ensayo, limpieza y mantenimiento del sistema. Las conexiones eléctricas deberán estar organizadas para evitar interferencias entre componentes y facilitar la inspección del prototipo. En caso de utilizar el MH-Z19C, se deberá considerar su alimentación de 5 V y comunicación UART. Fuente: Kusa et al., 2008; Baneschi et al., 2023; Winsen Electronics, MH-Z19C NDIR CO₂ Sensor, 2026. | L.S. |
| 03/09/2026 | **Transporte** | **REQ-017:** El sistema deberá permitir su traslado sin afectar la estructura de la cámara ni las conexiones de los sensores. Los componentes electrónicos deberán permanecer protegidos durante el transporte y la estructura deberá conservar sus dimensiones y estabilidad mecánica establecidas.<br><br>El diseño deberá considerar elementos que faciliten el movimiento del prototipo y reduzcan el riesgo de daños en sensores, conexiones o componentes internos. | K.C. |
| 03/09/2026 | **Uso** | **REQ-018:** El sistema deberá permitir realizar ensayos repetibles y controlados utilizando plantas de papa bajo diferentes condiciones experimentales. La secuencia de operación deberá ser la siguiente:<br><br>1. Colocar la planta y el sustrato dentro de la cámara experimental.<br>2. Instalar y verificar el funcionamiento de los sensores.<br>3. Establecer las condiciones experimentales del ensayo.<br>4. Cerrar la cámara para iniciar la medición.<br>5. Registrar las concentraciones de NH₃, CO₂ y variables complementarias.<br>6. Finalizar el ensayo y almacenar los datos obtenidos.<br>7. Analizar y comparar los resultados obtenidos entre diferentes condiciones experimentales.<br>8. Limpiar el sistema y prepararlo para un nuevo ensayo.<br><br>La condición de aplicación de urea será utilizada principalmente para estudiar su relación con la volatilización de NH₃, mientras que la medición de CO₂ permitirá analizar el intercambio gaseoso asociado a la respiración de la planta y el sustrato. Fuente: Perez-Trejo et al., 1981; Lee et al., 2024; Baneschi et al., 2023; Sunderlage y Cook, 2018. | A.D. |
| 03/09/2026 | **Mantenimiento** | **REQ-019:** El sistema deberá permitir realizar actividades de mantenimiento preventivo y correctivo sobre sus componentes principales.<br><br>Los sensores que tengan contacto con el suelo deberán limpiarse después de cada ensayo para evitar acumulación de residuos que afecten las mediciones. Los sensores de gases y variables ambientales deberán inspeccionarse periódicamente, verificando sus conexiones, estado físico y necesidad de calibración o reemplazo.<br><br>La cámara experimental deberá limpiarse después de cada ensayo para evitar contaminación cruzada entre experimentos. Los componentes deberán poder desmontarse individualmente para facilitar las actividades de mantenimiento. | C.M. |
| 03/09/2026 | **Costos** | **REQ-020:** El costo total del prototipo deberá mantenerse aproximadamente igual o menor a **S/ 1500**, considerando la adquisición de sensores, componentes electrónicos, materiales de fabricación y elementos complementarios necesarios para la construcción del sistema.<br><br>Se priorizará el uso de componentes comerciales disponibles y compatibles técnicamente con el sistema, buscando mantener una relación adecuada entre costo, funcionalidad y precisión de medición. Fuente: Winsen Electronics, ME3-NH3 Electrochemical Gas Sensor, 2026; Winsen Electronics, MH-Z19C NDIR CO₂ Sensor, 2026. | L.S. |
| 03/09/2026 | **Plazos** | **REQ-021:** El desarrollo del prototipo deberá ejecutarse mediante un cronograma dividido en etapas de diseño, fabricación, integración y validación experimental.<br><br>| Etapa | Fecha estimada |<br>|---|---|<br>| Definición del proyecto y elaboración de lista de exigencias | 01/09/2026 – 07/09/2026 |<br>| Revisión del estado de la tecnología y selección de sensores | 08/09/2026 – 20/09/2026 |<br>| Diseño mecánico de la cámara experimental | 15/09/2026 – 30/09/2026 |<br>| Selección de componentes electrónicos y diseño del sistema de control | 25/09/2026 – 10/10/2026 |<br>| Desarrollo del software de adquisición y almacenamiento de datos | 01/10/2026 – 20/10/2026 |<br>| Fabricación de la cámara e integración del hardware | 21/10/2026 – 05/11/2026 |<br>| Calibración de sensores y pruebas iniciales del sistema | 06/11/2026 – 15/11/2026 |<br>| Realización de ensayos experimentales y generación del conjunto de datos | 16/11/2026 – 30/11/2026 |<br>| Análisis de resultados y elaboración de documentación final | 01/12/2026 – 10/12/2026 |<br><br>Las fechas podrán ajustarse según la disponibilidad de componentes, pruebas realizadas y avances del equipo de trabajo. Fuente: Kusa et al., 2008; Baneschi et al., 2023; Lee et al., 2024; Chatzitriantafyllou et al., 2026. | K.C. |
# Bibliografía

[1] Kusa, K., Sawamoto, T., Hu, R., & Hatano, R. (2008). *Comparison of the closed-chamber and gas concentration gradient methods for measurement of CO₂ and N₂O fluxes in two upland field soils*. Soil Science and Plant Nutrition, 54(5), 777–785.  
https://doi.org/10.1111/j.1747-0765.2008.00292.x

[2] Baneschi, I., Raco, B., Magnani, M., Giamberini, M., Lelli, M., Mosca, P., Provenzale, A., Coppo, L., & Guidi, M. (2023). *Non-steady-state closed dynamic chamber to measure soil CO₂ respiration: A protocol to reduce uncertainty*. Frontiers in Environmental Science, 10, 1048948.  
https://doi.org/10.3389/fenvs.2022.1048948

[3] Perez-Trejo, M. S., Janes, H. W., & Frenkel, C. (1981). *Mobilization of Respiratory Metabolism in Potato Tubers by Carbon Dioxide*. Plant Physiology, 67(3), 514–517.  
https://doi.org/10.1104/pp.67.3.514

[4] University of California, Davis, Postharvest Research and Extension Center. *Potato (Early Crop)*. Información técnica sobre respiración y producción de CO₂ en tubérculos de papa.

[5] Lee, Y.-J., Im, E.-C., Lee, G., Hong, S.-C., Lee, C.-G., & Park, S.-J. (2024). *Comparison of ammonia volatilization in paddy and field soils fertilized with urea and ammonium sulfate during rice, potato, and Chinese cabbage cultivation*. Atmospheric Pollution Research, 15(4), 102049.  
https://doi.org/10.1016/j.apr.2024.102049

[6] Winsen Electronics. (2026). *ME3-NH3 Electrochemical Gas Sensor*. Winsen Electronics.

[7] Winsen Electronics. (2026). *CO₂ Sensor*. Winsen Electronics.

[8] Winsen Electronics. (2026). *MH-Z19C NDIR CO₂ Sensor for HVAC and IAQ*. Winsen Electronics.

[9] Espressif Systems. (2026). *ESP32 Series Datasheet*. Espressif Systems.

[10] Sunderlage, B., & Cook, R. L. (2018). *Soil Property and Fertilizer Additive Effects on Ammonia Volatilization from Urea*. Soil Science Society of America Journal, 82(1), 253–259.  
https://doi.org/10.2136/sssaj2017.05.0151

[11] Klimczyk, M., Siczek, A., & Schimmelpfennig, L. (2021). *Improving the efficiency of urea-based fertilization leading to reduction in ammonia emission*. Science of the Total Environment, 771, 145483.  
https://doi.org/10.1016/j.scitotenv.2021.145483

[12] Chatzitriantafyllou, M., Stavropoulos, P., Kallergi, S., Mavroeidis, M., Roussis, I., Karydogianni, S., Bilalis, D., & Kakabouki, I. (2026). *Optimizing Nitrogen Fertilization in Potato (Solanum tuberosum L.) Cultivation: A Review Regarding Inhibitor Use, Multifaceted Assessment Indicators, and Pathways to Sustainable Intensification*. Applied Sciences, 16(5), 2565.  
https://doi.org/10.3390/app16052565
