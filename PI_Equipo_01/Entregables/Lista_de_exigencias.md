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
|:---:|---|---|:---:|
| 2026 | **Función general** | El sistema debe funcionar como una cámara experimental cerrada para el monitoreo de una planta joven de papa y su sustrato. Debe permitir registrar las concentraciones de **NH₃ y CO₂**, junto con las condiciones ambientales y del suelo. También debe registrar la identificación del cultivo, las condiciones experimentales y el tiempo de experimentación. La **urea se considerará como una condición experimental** para estudiar su relación con la generación de NH₃, pero no será medida directamente por el sistema. El CO₂ se considerará debido al intercambio gaseoso asociado con la respiración de los tejidos vegetales y del sustrato. [1][2][3][5][6][7] | K.C. |
| 2026 | **Geometría** | La cámara experimental debe tener dimensiones aproximadas de **20 × 18 × 18 cm**, con un volumen interno aproximado de 6.48 L. Debe disponer de una tapa transparente y espacio suficiente para instalar los sensores y permitir la colocación de una maceta de aproximadamente **10 cm de diámetro y 8 cm de altura**. | A.D. |
| 2026 | **Cinemática** | El sistema será de funcionamiento estático. La cámara permanecerá fija durante cada ensayo y el reemplazo o cambio de la muestra se realizará manualmente. | C.M. |
| 2026 | **Fuerzas** | La estructura debe soportar el peso de la cámara, la maceta, el sustrato y la planta. La tapa debe permanecer cerrada durante el ensayo y los soportes de los sensores deben mantenerse estables para evitar desplazamientos durante las mediciones. | L.S. |
| 2026 | **Energía** | El sistema debe utilizar una alimentación compatible con los componentes electrónicos. El ESP32-WROOM-32D debe operar dentro de su rango de alimentación de **3.0 a 3.6 V**. Si se utiliza un sensor de CO₂ MH-Z19C, este requiere una alimentación de aproximadamente **5.0 V** y comunicación compatible con el ESP32. La alimentación y distribución de energía deben verificarse antes de realizar los ensayos. [8][12] | K.C. |
| 2026 | **Materia** | Los materiales de la cámara deben ser resistentes a la humedad, fáciles de limpiar y adecuados para trabajar con sustrato. La tapa transparente debe permitir observar el cultivo y los materiales utilizados no deben interferir significativamente con las mediciones de gases. | A.D. |
| 2026 | **Señales (Información)** | El sistema debe recibir como entradas la identificación del cultivo, condiciones del sustrato, temperatura ambiental, humedad ambiental, temperatura del suelo, humedad del suelo, iluminación, concentración de NH₃, concentración de CO₂, tiempo de experimentación, configuración del ensayo y comandos del usuario. Como salidas debe proporcionar los valores medidos, estado de los sensores, variaciones de NH₃ y CO₂, alertas, historial, tendencias, relaciones entre variables y comparación de resultados. [1][2][5][6][7] | C.M. |
| 2026 | **Control** | El sistema debe controlar la secuencia de adquisición, validación, almacenamiento, análisis y comparación de los datos. Cada medición debe asociarse con el cultivo, las condiciones experimentales y el tiempo. Debe permitir detectar valores fuera de rango o inconsistentes, analizar la variación de NH₃ y CO₂ respecto al tiempo y estudiar la relación del NH₃ con condiciones como la aplicación de urea, humedad y temperatura del suelo. [1][5][9][10][11][12] | L.S. |
| 2026 | **Electrónico (hardware)** | El **ESP32-WROOM-32D** será el controlador principal. El sistema debe integrar sensores para NH₃, CO₂, temperatura y humedad del suelo, temperatura y humedad ambiental e iluminación. Para NH₃ se considera el sensor electroquímico **ME3-NH3 de Winsen**. Para CO₂ se considera un sensor NDIR compatible, tomando como referencia el **MH-Z19C**, con rangos disponibles de 400–2000 ppm, 400–5000 ppm o 400–10000 ppm y comunicación UART/PWM. Los módulos deben ser reemplazables para facilitar mantenimiento y pruebas. [6][7][8][12] | K.C. |
| 2026 | **Software** | El software debe permitir adquirir, procesar, almacenar y visualizar los datos obtenidos por los sensores. Debe identificar el cultivo y mostrar las concentraciones de NH₃ y CO₂ junto con las variables ambientales y del suelo. Debe generar series temporales, tendencias, variaciones, relaciones entre variables y permitir comparar diferentes condiciones experimentales, incluyendo condiciones relacionadas con la aplicación de urea. **No se utilizará Machine Learning.** [2][5][11] | A.D. |
| 2026 | **Comunicaciones** | El ESP32 debe comunicarse con los sensores mediante las interfaces disponibles, como I²C, SPI y UART. El sistema podrá utilizar Wi-Fi o Bluetooth para comunicación inalámbrica. Debe contemplarse un funcionamiento básico de adquisición aun cuando no exista conexión a Internet y permitir el almacenamiento local y posterior sincronización de los datos. Si se utiliza el MH-Z19C, se empleará su comunicación UART. [8][12] | C.M. |
| 2026 | **Seguridad** | Los componentes electrónicos deben estar protegidos frente a humedad, polvo y contacto accidental con el sustrato. La alimentación eléctrica debe contar con medidas de protección frente a cortocircuitos y polaridad incorrecta. La cámara debe mantenerse cerrada durante los ensayos para controlar las condiciones experimentales. Cuando sea necesario abrir la cámara después de una prueba, se debe considerar la ventilación previa del sistema. Las conexiones eléctricas deben respetar las especificaciones de los fabricantes de los sensores y del ESP32. [6][8][12] | L.S. |
| 2026 | **Ergonomía** | El sistema debe poder ser operado por una persona. La manipulación de la cámara, instalación del cultivo, colocación de sensores y acceso a los componentes deben realizarse de manera sencilla. Se establece como objetivo un peso total aproximado de **3 kg o menos** y una interfaz de usuario simple para iniciar, detener y consultar los ensayos. [2] | K.C. |
| 2026 | **Fabricación** | La cámara será fabricada utilizando componentes comerciales y elementos impresos en 3D. Debe conservar las dimensiones aproximadas de **20 × 18 × 18 cm**, incluir una tapa transparente y disponer de soportes para los sensores de NH₃, CO₂ y las variables complementarias. El diseño debe facilitar la instalación y retiro de los componentes. [1][2] | A.D. |
| 2026 | **Control de calidad** | Antes de realizar los experimentos se deben verificar y, cuando corresponda, calibrar los sensores. El sensor de NH₃ debe verificarse según las indicaciones del fabricante y el sensor de CO₂ debe comprobarse utilizando referencias o rangos conocidos. Los sensores complementarios de temperatura y humedad deben verificarse antes de su integración. Se deben realizar mediciones repetidas y pruebas individuales e integradas para comprobar el funcionamiento del sistema. Las pruebas de CO₂ deben considerar la calibración de la cámara, intervalos de medición y repetición de ensayos. Para NH₃ se deben controlar las condiciones del suelo y de la aplicación de urea. [1][2][6][9][10][12] | C.M. |
| 2026 | **Montaje** | Los sensores y componentes electrónicos deben instalarse de forma modular y segura. Las conexiones deben estar correctamente identificadas. La maceta debe poder retirarse de la cámara. Los sensores de NH₃ y CO₂ deben ubicarse en el espacio gaseoso de la cámara para realizar el monitoreo de las concentraciones. Si se utiliza el MH-Z19C, su alimentación y comunicación UART deben realizarse de acuerdo con sus especificaciones. [1][2][12] | L.S. |
| 2026 | **Transporte** | La cámara debe ser transportable sin comprometer la integridad de la estructura, los sensores ni las conexiones eléctricas. Durante el traslado deben mantenerse las dimensiones y configuración del sistema. | K.C. |
| 2026 | **Uso** | El sistema debe permitir realizar ensayos repetibles y controlados con plantas de papa. La secuencia de uso será: colocar la planta y el sustrato → instalar y verificar los sensores → establecer las condiciones experimentales → cerrar la cámara → iniciar el ensayo → registrar NH₃, CO₂ y las variables complementarias → finalizar la medición → analizar y comparar los resultados → limpiar la cámara → preparar el siguiente ensayo. La aplicación de urea será considerada principalmente para estudiar su relación con el NH₃. El CO₂ se utilizará como indicador del intercambio gaseoso y respiración dentro del sistema experimental. [3][5][2][9] | A.D. |
| 2026 | **Mantenimiento** | Los sensores que tengan contacto con el suelo deben limpiarse después de los ensayos. Los sensores de gases y ambientales deben inspeccionarse periódicamente. Se debe realizar calibración cuando corresponda y permitir el retiro y reemplazo individual de los sensores. La cámara debe limpiarse entre experimentos para evitar contaminación o interferencias entre pruebas. | C.M. |
| 2026 | **Costos** | El costo total objetivo del sistema debe mantenerse en aproximadamente **S/ 1500 o menos**, sujeto a la selección final de los sensores de NH₃ y CO₂ y de los componentes complementarios. Se priorizarán componentes comerciales, disponibles y accesibles. [6][7][12] | L.S. |
| 2026 | **Plazos** | El desarrollo debe considerar las siguientes etapas: definición del proyecto → revisión del estado de la tecnología → identificación de variables del cultivo de papa → selección de sensores de NH₃ y CO₂ → selección de sensores complementarios → diseño de la cámara → diseño electrónico → desarrollo del software → fabricación → integración → calibración → realización de experimentos → generación del conjunto de datos → análisis y comparación de resultados. Las fechas específicas serán establecidas de acuerdo con el cronograma de trabajo del equipo. [1][2][5][11] | K.C. |

</div>


# BIBLIOGRAFÍA

**[1]** K. Kusa, T. Sawamoto, R. Hu, and R. Hatano, “Comparison of the closed-chamber and gas concentration gradient methods for measurement of CO₂ and N₂O fluxes in two upland field soils,” *Soil Science and Plant Nutrition*, vol. 54, no. 5, pp. 777–785, 2008. doi: 10.1111/j.1747-0765.2008.00292.x.

**[2]** I. Baneschi, B. Raco, M. Magnani, M. Giamberini, M. Lelli, P. Mosca, A. Provenzale, L. Coppo, and M. Guidi, “Non-steady-state closed dynamic chamber to measure soil CO₂ respiration: A protocol to reduce uncertainty,” *Frontiers in Environmental Science*, vol. 10, 1048948, 2023. doi: 10.3389/fenvs.2022.1048948.

**[3]** M. S. Perez-Trejo, H. W. Janes, and C. Frenkel, “Mobilization of Respiratory Metabolism in Potato Tubers by Carbon Dioxide,” *Plant Physiology*, vol. 67, no. 3, pp. 514–517, 1981. doi: 10.1104/pp.67.3.514.

**[4]** University of California, Davis, Postharvest Research and Extension Center, “Potato (Early Crop),” technical information on respiration rates and CO₂ production of potato tubers.

**[5]** Y.-J. Lee, E.-C. Im, G. Lee, S.-C. Hong, C.-G. Lee, and S.-J. Park, “Comparison of ammonia volatilization in paddy and field soils fertilized with urea and ammonium sulfate during rice, potato, and Chinese cabbage cultivation,” *Atmospheric Pollution Research*, vol. 15, no. 4, 102049, 2024. doi: 10.1016/j.apr.2024.102049.

**[6]** Winsen Electronics, “ME3-NH3 Electrochemical Gas Sensor,” Winsen Electronics, 2026.

**[7]** Winsen Electronics, “CO₂ Sensor,” Winsen Electronics, 2026.

**[8]** Espressif Systems, “ESP32 Series Datasheet,” Espressif Systems, 2026.

**[9]** B. Sunderlage and R. L. Cook, “Soil Property and Fertilizer Additive Effects on Ammonia Volatilization from Urea,” *Soil Science Society of America Journal*, vol. 82, no. 1, pp. 253–259, 2018. doi: 10.2136/sssaj2017.05.0151.

**[10]** M. Klimczyk, A. Siczek, and L. Schimmelpfennig, “Improving the efficiency of urea-based fertilization leading to reduction in ammonia emission,” *Science of the Total Environment*, vol. 771, 145483, 2021. doi: 10.1016/j.scitotenv.2021.145483.

**[11]** M. Chatzitriantafyllou, P. Stavropoulos, S. Kallergi, M. Mavroeidis, I. Roussis, S. Karydogianni, D. Bilalis, and I. Kakabouki, “Optimizing Nitrogen Fertilization in Potato (*Solanum tuberosum* L.) Cultivation: A Review Regarding Inhibitor Use, Multifaceted Assessment Indicators, and Pathways to Sustainable Intensification,” *Applied Sciences*, vol. 16, no. 5, 2565, 2026. doi: 10.3390/app16052565.

**[12]** Winsen Electronics, “MH-Z19C NDIR CO₂ Sensor for HVAC and IAQ,” Winsen Electronics, 2026.