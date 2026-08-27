# Universidad Peruana Cayetano Heredia

## Facultad de Ciencias e Ingeniería

### Departamento Académico de Ingeniería

### Ingeniería Informática e Ingeniería Industrial

**Semestre Académico:** 2026 II – VI Ciclo  
**Semana N.° 1**  
**Tema:** “Lista de exigencias”  
**Curso:** Proyecto Integrador – Práctica N.° 1  
**Año:** 2026  
**Lugar:** Lima – Perú

---

## Docentes

- Ing. [Umbert Lewis De La Cruz Rodriguez](#)
- Ing. Vanessa Stefanny Stefanny Arevalo

---

## Integrantes del equipo

| Integrante | Aporte/s en específico | % de aporte |
|---|---|:---:|
| Cesar Rodrigo Milla Gómez | Definió la función general del sistema, las señales de entrada y salida, y se encargó de los aspectos relacionados con la seguridad del prototipo y el manejo de los gases durante los ensayos. | 25% |
| Anderson Josue Delerna Infantes | Diseñó el tamaño y la forma de la cámara experimental, la alimentación de energía, el sistema de control, el software, la fabricación y la planificación de las etapas del proyecto. | 25% |
| Kevin Esty Carvallo Neciosup | Trabajó en la integración de los sensores de gases, suelo y ambiente, el hardware y microcontrolador, el control de las mediciones, el software y el procedimiento de uso del prototipo. | 25% |
| Shedira Lumeris Sihuincha Palacin | Revisó la resistencia y estructura del equipo, la integración electrónica, las comunicaciones, la ergonomía, la calibración y control de calidad de los sensores, además del transporte, mantenimiento y costos del prototipo. | 25% |
| **Equipo** | **Informe final** | **100%** |

---

# 1. Lista de Exigencias

**Tabla 1: Lista de Exigencias**

<table>
  <tr>
    <th colspan="3">LISTA DE EXIGENCIAS</th>
    <th>Páginas: 5</th>
  </tr>
  <tr>
    <td colspan="3"></td>
    <td><strong>Edición:</strong> Rev. 1</td>
  </tr>
  <tr>
    <th>PROYECTO:</th>
    <td colspan="2"><strong>GREENPLANT AI – Sistema inteligente para detectar y comparar emisiones de gases de efecto invernadero asociadas a diferentes cultivos mediante sensores y Machine Learning</strong></td>
    <td><strong>Fecha:</strong> 08/2026<br><strong>Revisado:</strong></td>
  </tr>
  <tr>
    <th>CLIENTE:</th>
    <td colspan="2"><strong>Universidad Peruana Cayetano Heredia (UPCH)</strong></td>
    <td><strong>Elaborado:</strong><br>K.C, A.D, C.M, L.S</td>
  </tr>
</table>

<br>

<table>
  <thead>
    <tr>
      <th>Fecha (cambios)</th>
      <th>Deseo o Exigencia</th>
      <th>Descripción</th>
      <th>Responsable</th>
    </tr>
  </thead>
  <tbody>

  <tr>
    <td>08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Función general:</strong> El sistema deberá permitir realizar mediciones experimentales de gases de efecto invernadero asociados a diferentes cultivos dentro de una cámara cerrada de volumen controlado. Deberá registrar principalmente la concentración de <strong>CH₄ y CO₂</strong>, además de variables ambientales y del sustrato, procesar la información obtenida y permitir comparar los resultados entre diferentes cultivos bajo condiciones experimentales similares. Los datos deberán almacenarse junto con la identificación del cultivo, tiempo de medición y condiciones del ensayo para posteriormente aplicar técnicas de Machine Learning e identificar patrones relacionados con las emisiones. Las cámaras cerradas permiten estudiar cambios en la concentración de gases dentro de un volumen definido y durante un periodo determinado. (de Klein et al., 2020; Parkin y Venterea, 2010; Pavelka et al., 2018).
    </td>
    <td align="center">C.M, K.C, A.D, L.S</td>
  </tr>

  <tr>
    <td>08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Geometría:</strong> El prototipo deberá presentar una cámara experimental cerrada, portátil y de dimensiones aproximadas de <strong>20 cm × 18 cm × 18 cm</strong>, con un volumen interno aproximado de <strong>6,48 L</strong>. Deberá permitir colocar una maceta de aproximadamente <strong>10 cm de diámetro y 8 cm de altura</strong>, junto con una planta joven. La tapa superior deberá ser transparente para permitir la observación del cultivo y el ingreso de iluminación artificial. El interior deberá disponer de espacio suficiente para instalar los sensores sin interferir significativamente con la planta. Las dimensiones deberán facilitar la limpieza, el cambio de cultivo y la repetición de los ensayos. (de Klein et al., 2020; Pavelka et al., 2018).
    </td>
    <td align="center">A.D</td>
  </tr>

  <tr>
    <td>08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Cinemática:</strong> El prototipo no requerirá mecanismos de movimiento durante la medición. La cámara deberá permanecer estática durante cada ensayo para mantener estable el volumen experimental y reducir perturbaciones en las mediciones. La colocación y retiro de la maceta con el cultivo se realizará manualmente entre ensayos. La tapa deberá permitir una apertura y cierre sencillo para facilitar la instalación, retiro y limpieza del cultivo. (de Klein et al., 2020; Parkin y Venterea, 2010).
    </td>
    <td align="center">K.C</td>
  </tr>

  <tr>
    <td>08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Fuerzas:</strong> La estructura de la cámara, la tapa y los soportes deberán resistir la manipulación manual, el peso de la maceta con el sustrato y las aperturas y cierres repetidos durante los ensayos. Los soportes de los sensores deberán mantenerse firmes durante la medición y evitar desplazamientos accidentales. La estructura deberá conservar su estabilidad durante la manipulación y transporte del prototipo. (de Klein et al., 2020).
    </td>
    <td align="center">L.S</td>
  </tr>

  <tr>
    <td>08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Energía:</strong> El sistema deberá funcionar mediante una fuente de alimentación de bajo voltaje compatible con el controlador, los sensores y los demás componentes electrónicos. La alimentación deberá ser estable durante todo el periodo experimental para evitar interrupciones durante la adquisición de datos.
      <ul>
        <li>La iluminación artificial instalada sobre la tapa transparente deberá disponer de una alimentación adecuada y mantenerse estable durante los ensayos.</li>
        <li>Los sensores y componentes electrónicos deberán recibir niveles de tensión compatibles con sus especificaciones de funcionamiento.</li>
        <li>El sistema deberá permitir verificar la disponibilidad de alimentación antes y durante la medición.</li>
      </ul>
      (Espressif Systems, 2026; Sensirion AG, 2020).
    </td>
    <td align="center">A.D</td>
  </tr>

  <tr>
    <td>08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Materia:</strong> El elemento experimental estará constituido por una planta joven colocada en una maceta o recipiente con sustrato agrícola. El sistema deberá permitir retirar y reemplazar el cultivo entre ensayos para realizar comparaciones entre diferentes especies vegetales. La cámara podrá fabricarse mediante materiales adecuados para impresión 3D y una tapa transparente. Los materiales utilizados deberán soportar las condiciones de humedad presentes durante los experimentos y permitir una limpieza adecuada después de cada ensayo para reducir la contaminación cruzada. (de Klein et al., 2020; Pavelka et al., 2018).
    </td>
    <td align="center">L.S</td>
  </tr>

  <tr>
    <td>08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Señales (Información):</strong> El sistema deberá contar con señales de entrada y salida asociadas al proceso de medición y comparación de emisiones.
      <br><br>
      <strong>Señales de entrada:</strong>
      <ul>
        <li>Concentración de CH₄.</li>
        <li>Concentración de CO₂.</li>
        <li>Temperatura del suelo.</li>
        <li>Humedad del suelo.</li>
        <li>Temperatura ambiental.</li>
        <li>Humedad ambiental.</li>
        <li>Conductividad eléctrica del sustrato.</li>
        <li>Intensidad de iluminación.</li>
        <li>Identificación del cultivo.</li>
        <li>Número de ensayo.</li>
        <li>Tiempo de medición.</li>
        <li>Comandos e información ingresada por el usuario.</li>
      </ul>
      <strong>Señales de salida:</strong>
      <ul>
        <li>Valores obtenidos de los sensores.</li>
        <li>Estado de funcionamiento de los sensores.</li>
        <li>Variación de CH₄ y CO₂ durante el ensayo.</li>
        <li>Alertas ante lecturas anormales o inválidas.</li>
        <li>Historial de mediciones.</li>
        <li>Resultados del procesamiento de datos.</li>
        <li>Resultados del análisis mediante Machine Learning.</li>
        <li>Comparación de emisiones entre cultivos.</li>
      </ul>
      Las variables ambientales y del sustrato permitirán contextualizar las concentraciones gaseosas y analizar su relación con las emisiones observadas. (Zhang et al., 2025; Jiang et al., 2023; Pavelka et al., 2018).
    </td>
    <td align="center">K.C, C.M</td>
  </tr>

  <tr>
    <td>08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Control:</strong> El sistema de control deberá coordinar la adquisición de información proveniente de los sensores y verificar que las mediciones se encuentren dentro de rangos operativos antes de almacenarlas. Durante cada ensayo deberá registrar el tiempo transcurrido y asociar las lecturas al cultivo correspondiente. El sistema deberá ejecutar la secuencia de <strong>inicio, medición, validación, almacenamiento y finalización del ensayo</strong>. En caso de detectar valores fuera del rango operativo o información insuficiente, deberá identificar la condición para evitar que datos no válidos sean utilizados posteriormente en el análisis. (de Klein et al., 2020; Parkin y Venterea, 2010).
    </td>
    <td align="center">A.D, K.C</td>
  </tr>

  <tr>
    <td>08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Electrónico (hardware):</strong> El sistema utilizará un controlador o microcontrolador con capacidad suficiente para adquirir información de varios sensores y comunicarse con una interfaz externa. Se considera, como referencia, un dispositivo tipo <strong>ESP32</strong>, sin que ello excluya otras alternativas equivalentes que cumplan con los requisitos funcionales.
      <br><br>
      El prototipo deberá integrar sensores destinados a detectar <strong>CH₄ y CO₂</strong>, además de sensores para registrar temperatura del suelo, humedad del suelo, temperatura ambiental, humedad ambiental, conductividad eléctrica e iluminación. Los módulos deberán ser reemplazables para facilitar el mantenimiento y futuras mejoras. El controlador deberá disponer de interfaces adecuadas para la adquisición y comunicación de las diferentes señales. (Winsen Electronics, 2018; Sensirion AG, 2020; Analog Devices, 2019; Espressif Systems, 2026).
    </td>
    <td align="center">K.C, L.S</td>
  </tr>

  <tr>
    <td>08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Software:</strong> El software deberá permitir adquirir, procesar, almacenar y visualizar la información obtenida durante los ensayos. Deberá registrar la identificación del cultivo, número de ensayo, fecha, hora, tiempo de medición y valores obtenidos por los sensores.
      <br><br>
      La interfaz deberá permitir visualizar las concentraciones de <strong>CH₄ y CO₂</strong> junto con las variables ambientales y del sustrato mediante tablas y gráficos. El sistema deberá conservar el historial de las mediciones para facilitar la comparación entre cultivos.
      <br><br>
      Posteriormente, los datos podrán utilizarse para entrenar y validar modelos de <strong>Machine Learning</strong> destinados a identificar patrones y comparar los niveles de emisión entre los cultivos evaluados. (Zhang et al., 2025; Jiang et al., 2023).
    </td>
    <td align="center">A.D, K.C</td>
  </tr>

  <tr>
    <td>08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Comunicaciones:</strong> El controlador deberá comunicarse correctamente con los sensores utilizados y permitir el envío de los datos hacia una interfaz de visualización o sistema de almacenamiento. La comunicación entre el controlador y los sensores deberá realizarse mediante interfaces y protocolos compatibles con los componentes utilizados.
      <br><br>
      Cuando exista conectividad disponible, los datos podrán enviarse a una plataforma externa para su almacenamiento y visualización. En caso de no existir conexión, el sistema deberá permitir almacenar temporalmente las mediciones para su posterior transferencia. (Espressif Systems, 2026; Sensirion AG, 2020).
    </td>
    <td align="center">L.S</td>
  </tr>

  <tr>
    <td>08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Seguridad:</strong> Los componentes electrónicos deberán encontrarse protegidos frente al contacto accidental con humedad, sustrato y otros elementos presentes durante el experimento. Las conexiones eléctricas deberán estar aisladas y protegidas frente a cortocircuitos y conexiones incorrectas.
      <br><br>
      La estructura deberá evitar bordes cortantes o superficies que puedan generar riesgos durante la manipulación. La alimentación eléctrica deberá utilizar niveles seguros para el usuario y respetar las especificaciones de los componentes utilizados. La cámara deberá poder <strong>ventilarse adecuadamente entre ensayos</strong> para evitar la acumulación de gases y garantizar condiciones seguras de manipulación. (de Klein et al., 2020; Espressif Systems, 2026).
    </td>
    <td align="center">C.M</td>
  </tr>

  <tr>
    <td>08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Ergonomía:</strong> El equipo deberá ser manipulable por una sola persona y permitir la colocación y retiro de la maceta sin procedimientos complejos. La tapa transparente deberá permitir observar el cultivo sin necesidad de abrir la cámara durante la medición.
      <br><br>
      La interfaz deberá presentar la información mediante valores, gráficos e indicadores comprensibles. Los resultados obtenidos directamente de los sensores deberán diferenciarse de los resultados generados mediante Machine Learning para facilitar su interpretación. (Pavelka et al., 2018; Zhang et al., 2025).
    </td>
    <td align="center">L.S</td>
  </tr>

  <tr>
    <td>08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Fabricación:</strong> El prototipo deberá poder fabricarse utilizando materiales y componentes disponibles comercialmente. El cuerpo principal de la cámara podrá fabricarse mediante impresión 3D utilizando un material adecuado para su estructura, mientras que la tapa deberá utilizar un material transparente que permita observar el cultivo y recibir iluminación artificial.
      <br><br>
      El diseño deberá incorporar espacios para la instalación de sensores, paso de cables, fijación de la tapa y ubicación de los componentes electrónicos. La fabricación deberá mantener aproximadamente las dimensiones de <strong>20 cm × 18 cm × 18 cm</strong> y permitir retirar fácilmente la maceta para realizar el cambio de cultivo y la limpieza. (de Klein et al., 2020; Pavelka et al., 2018).
    </td>
    <td align="center">K.C, A.D</td>
  </tr>

  <tr>
    <td>08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Control de calidad:</strong> Antes de realizar los experimentos comparativos, los sensores deberán verificarse y, cuando corresponda, calibrarse de acuerdo con las recomendaciones de sus fabricantes o procedimientos de referencia.
      <br><br>
      Se deberán realizar mediciones de prueba para evaluar la estabilidad y consistencia de los resultados. También deberá comprobarse individualmente el funcionamiento de cada sensor y posteriormente el funcionamiento conjunto del sistema.
      <br><br>
      Las mediciones deberán revisarse antes de incorporarse al conjunto de datos utilizado para el análisis mediante Machine Learning. (de Klein et al., 2020; Parkin y Venterea, 2010; Sensirion AG, 2020; Winsen Electronics, 2018).
    </td>
    <td align="center">L.S</td>
  </tr>

  <tr>
    <td>08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Montaje:</strong> El diseño deberá ser modular para permitir el montaje y desmontaje de los sensores, controlador, fuente de alimentación, iluminación y demás componentes sin reconstruir completamente la cámara.
      <br><br>
      Las conexiones deberán encontrarse identificadas y aseguradas para evitar desconexiones accidentales durante el ensayo. La cámara deberá permitir retirar fácilmente la maceta para realizar el cambio de cultivo y facilitar la limpieza. Los sensores deberán mantenerse en posiciones similares durante los diferentes ensayos para favorecer la comparabilidad de las mediciones. (de Klein et al., 2020; Pavelka et al., 2018).
    </td>
    <td align="center">L.S, C.M</td>
  </tr>

  <tr>
    <td>08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Transporte:</strong> El dispositivo deberá poder trasladarse manualmente sin desprender sensores, cables o componentes electrónicos. La estructura deberá proteger los componentes y mantener la geometría de la cámara durante el traslado.
      <br><br>
      La tapa transparente deberá contar con una fijación adecuada para reducir el riesgo de daños durante el transporte. Los sensores y accesorios desmontables deberán poder almacenarse de manera segura cuando no estén instalados. (de Klein et al., 2020).
    </td>
    <td align="center">L.S</td>
  </tr>

  <tr>
    <td>08/2026</td>
    <td align="center">D</td>
    <td>
      <strong>Uso:</strong> Se desea que el sistema pueda utilizarse de manera repetible para diferentes cultivos jóvenes bajo condiciones experimentales controladas. La secuencia de utilización deberá ser sencilla:
      <br><br>
      <strong>Seleccionar cultivo → colocar maceta y planta → verificar sensores → cerrar cámara → encender iluminación → iniciar medición → registrar datos → finalizar ensayo → ventilar y limpiar → retirar cultivo → colocar nuevo cultivo → repetir.</strong>
      <br><br>
      Cada ensayo deberá registrar el cultivo evaluado y las condiciones experimentales para posteriormente comparar los resultados obtenidos. (Parkin y Venterea, 2010; Pavelka et al., 2018).
    </td>
    <td align="center">K.C</td>
  </tr>

  <tr>
    <td>08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Mantenimiento:</strong> Los sensores que estén en contacto con el sustrato deberán poder limpiarse después de cada medición. Los sensores de gases y ambientales deberán revisarse y mantenerse de acuerdo con las recomendaciones de sus fabricantes.
      <br><br>
      Los sensores que requieran calibración deberán poder retirarse sin desmontar completamente la cámara. Los componentes electrónicos deberán poder reemplazarse individualmente en caso de falla.
      <br><br>
      La cámara deberá limpiarse y secarse entre experimentos para reducir la contaminación cruzada y mantener condiciones comparables entre los diferentes cultivos. (de Klein et al., 2020; Sensirion AG, 2020; Winsen Electronics, 2018).
    </td>
    <td align="center">A.D, L.S</td>
  </tr>

  <tr>
    <td>08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Costos:</strong> Se buscará que el prototipo utilice componentes comerciales de costo accesible y fácil adquisición. Como objetivo inicial, el costo total de los componentes no deberá superar aproximadamente <strong>S/ 1500</strong>, sujeto a modificación después de seleccionar y cotizar definitivamente los sensores, controlador, cámara, iluminación y demás componentes.
      <br><br>
      Se priorizarán componentes reutilizables y reemplazables, manteniendo como criterios principales la estabilidad, disponibilidad y calidad de las mediciones. (Winsen Electronics, 2018; Sensirion AG, 2020).
    </td>
    <td align="center">L.S</td>
  </tr>

  <tr>
    <td>08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Plazos:</strong> El proyecto comprenderá las etapas de definición del problema, revisión del estado de la tecnología, selección de cultivos y variables, selección de sensores, diseño de la cámara experimental, diseño electrónico, desarrollo del software, fabricación del prototipo, integración de sensores, calibración, realización de ensayos experimentales, generación del conjunto de datos, desarrollo y validación del algoritmo de Machine Learning y comparación final de los cultivos.
      <br><br>
      Las fechas específicas de cada etapa deberán establecerse mediante el plan de trabajo del proyecto. (de Klein et al., 2020; Zhang et al., 2025; Jiang et al., 2023).
    </td>
    <td align="center">A.D, K.C</td>
  </tr>

  </tbody>
</table>

---

# Bibliografía

[1] C. A. M. de Klein et al., “Global Research Alliance N2O chamber methodology guidelines: Introduction, with health and safety considerations,” *Journal of Environmental Quality*, vol. 49, 2020, doi: 10.1002/jeq2.20131.

[2] A. R. Parkin and T. C. Venterea, “Measurement of Greenhouse Gas Flux from Agricultural Soils Using Static Chambers,” *Methods in Molecular Biology*, 2010.

[3] P. Pavelka et al., “Assessment of methane and nitrous oxide fluxes from paddy field by means of static closed chambers maintaining plants within headspace,” *Methods and Protocols*, 2018.

[4] Food and Agriculture Organization of the United Nations, “Emissions from crops (Global, National - Annual),” FAOSTAT, 2026.

[5] Q. Zhang, W. Wen, Y. Zhuang, L. Zhang, L. Zhai, S. Li, H. Liu, and Y. Du, “Machine learning-driven method for in-situ high-frequency CH₄ measurement in paddy fields based on water-soil-air factors: A case study of the Yangtze River Basin,” *Journal of Environmental Management*, vol. 393, p. 127132, 2025, doi: 10.1016/j.jenvman.2025.127132.

[6] Z. Jiang, S. Yang, P. Smith, and Q. Pang, “Ensemble machine learning for modeling greenhouse gas emissions at different time scales from irrigated paddy fields,” *Field Crops Research*, vol. 292, p. 108821, 2023, doi: 10.1016/j.fcr.2023.108821.

[7] Sensirion AG, “SCD30 CO₂ Sensor Datasheet,” Sensirion AG, 2020. El SCD30 utiliza tecnología NDIR para CO₂ e integra medición de temperatura y humedad.

[8] Sensirion AG, “SHT3x-DIS Digital Humidity and Temperature Sensor Datasheet,” Sensirion AG.

[9] Analog Devices, “DS18B20 Programmable Resolution 1-Wire Digital Thermometer,” Datasheet.

[10] Espressif Systems, “ESP32-WROOM-32 Datasheet,” Espressif Systems, 2026. El módulo dispone de GPIO, I²C, UART, ADC, Wi-Fi y Bluetooth para la integración del sistema.

[11] Winsen Electronics, “MQ-4 Semiconductor Sensor for Flammable Gas,” Datasheet, 2018. El sensor está diseñado para detectar metano (CH₄) y presenta un rango especificado de 300–10 000 ppm.

[12] ROHM Semiconductor, “BH1750FVI Digital 16bit Serial Output Type Ambient Light Sensor IC,” Datasheet.

[13] DFRobot, “Analog Electrical Conductivity Sensor / Soil Conductivity Sensor,” DFRobot, 2025.
