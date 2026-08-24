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
| Cesar Rodrigo Milla Gómez | Definió qué debe hacer el sistema en general, qué información entra y sale de él, y se encargó de los temas de seguridad y armado del equipo. | 25% |
| Anderson Josue Delerna Infantes | Diseñó el tamaño y la forma del equipo, cómo se alimenta de energía, cómo funciona el control del sistema, el software, y organizó el cronograma y el mantenimiento. | 25% |
| Kevin Esty Carvallo Neciosup | Diseñó cómo se colocan las sondas en el suelo, ayudó con la información que maneja el sistema, el control, la parte electrónica (sensores y microcontrolador), el software y cómo lo usará el agricultor. | 25% |
| Shedira Lumeris Sihuincha Palacin | Revisó qué tan resistente es el equipo, la parte electrónica, cómo se conecta Wi-Fi/Bluetooth, qué tan cómodo es de usar, calibró los sensores, y se encargó del transporte y los costos del prototipo. | 25% |
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
    <td colspan="2"><strong>AgroMind AI – Sistema inteligente de diagnóstico y monitoreo del estado del suelo</strong></td>
    <td><strong>Fecha:</strong> 25/08/2026<br><strong>Revisado:</strong></td>
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
    <td>/08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Función general:</strong> El sistema deberá realizar mediciones de parámetros físicos y químicos del suelo y del ambiente, procesar la información obtenida mediante sensores y generar un diagnóstico comprensible para el agricultor. Como mínimo deberá considerar humedad del suelo, temperatura del suelo, pH del suelo, temperatura ambiental y humedad ambiental. A partir de las mediciones y de la información del cultivo y de la parcela, el sistema deberá identificar posibles condiciones que puedan afectar el desarrollo del cultivo y generar recomendaciones de manejo. Además, deberá registrar las acciones realizadas por el usuario y permitir realizar nuevas mediciones para verificar y comparar la evolución de las condiciones antes y después de la intervención. (FAO, 2026; Prity et al., 2024; Sawant et al., 2026; Alawadhi y Patidar, 2025).
    </td>
    <td align="center">C.M, K.C, A.D, L.S</td>
  </tr>

  <tr>
    <td>/08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Geometría:</strong> El sistema deberá presentar una configuración portátil y compacta que permita su utilización directamente en campo. La unidad principal, sin considerar las sondas, no deberá superar aproximadamente 30 cm × 25 cm × 20 cm. Las sondas destinadas a la medición deberán permitir trabajar en la zona superficial de raíces, con una profundidad aproximada de 10 a 20 cm, dependiendo del cultivo.
    </td>
    <td align="center">A.D</td>
  </tr>

  <tr>
    <td>/08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Cinemática:</strong> El prototipo no requerirá mecanismos de movimiento continuo durante la operación. La inserción y extracción de las sondas se realizará manualmente. El diseño deberá permitir que la colocación del sensor en el suelo pueda realizarse sin movimientos complejos y sin necesidad de herramientas adicionales. (FAO, 2020)
    </td>
    <td align="center">K.C</td>
  </tr>

  <tr>
    <td>/08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Fuerzas:</strong> Las sondas de medición deberán soportar la fuerza de inserción manual necesaria para su utilización en suelo agrícola sin presentar deformaciones permanentes durante condiciones normales de trabajo. La estructura y carcasa deberán soportar la manipulación y transporte del dispositivo sin comprometer los sensores ni los componentes electrónicos. (FAO, 2020).
    </td>
    <td align="center">L.S</td>
  </tr>

  <tr>
    <td>/08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Energía:</strong> El sistema deberá funcionar mediante una fuente de alimentación portátil de bajo voltaje, preferentemente mediante una batería recargable, con una autonomía mínima objetivo de 8 horas de operación. Asimismo, deberá permitir conocer el estado o porcentaje aproximado de carga disponible. (Sawant et al., 2026; Saxena et al., 2025).
      <ul>
        <li>La alimentación de los sensores y componentes electrónicos deberá ser compatible con los niveles de tensión requeridos por cada dispositivo.</li>
        <li>Se priorizará el uso de una batería recargable que permita el funcionamiento del sistema durante las actividades de medición en campo, evitando depender de una conexión eléctrica permanente.</li>
        <li>El sistema deberá permitir verificar el nivel de carga disponible para evitar interrupciones durante la toma de datos.</li>
      </ul>
    </td>
    <td align="center">A.D</td>
  </tr>

  <tr>
    <td>/08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Materia:</strong> El material de entrada al sistema será el suelo agrícola, del cual se obtendrán las variables necesarias para determinar sus condiciones. Los elementos que entren directamente en contacto con el suelo deberán ser resistentes a la humedad y corrosión. La medición no deberá incorporar sustancias que alteren significativamente las características del suelo analizado. (FAO, 2020)
    </td>
    <td align="center">L.S</td>
  </tr>

  <tr>
    <td>/08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Señales (Información):</strong> El sistema deberá contar con señales de entrada y salida asociadas al proceso de diagnóstico y seguimiento del suelo.
      <br><br>
      <strong>Señales de entrada:</strong>
      <ul>
        <li>Humedad del suelo.</li>
        <li>Temperatura del suelo.</li>
        <li>pH del suelo.</li>
        <li>Temperatura ambiental.</li>
        <li>Humedad ambiental.</li>
        <li>Identificación de la parcela.</li>
        <li>Cultivo seleccionado.</li>
        <li>Etapa del cultivo.</li>
        <li>Comandos e información ingresada por el usuario.</li>
      </ul>
      <strong>Señales de salida:</strong>
      <ul>
        <li>Valores obtenidos de los sensores.</li>
        <li>Estado de funcionamiento de los sensores.</li>
        <li>Diagnóstico de las condiciones del suelo.</li>
        <li>Alertas ante condiciones anormales o datos no válidos.</li>
        <li>Recomendaciones de manejo.</li>
        <li>Registro de las acciones realizadas.</li>
        <li>Historial de mediciones.</li>
        <li>Comparación de la evolución de las condiciones antes y después de la intervención.</li>
      </ul>
      Las señales provenientes de los sensores permitirán obtener información sobre las condiciones del suelo y del ambiente, mientras que la información del cultivo y de la parcela permitirá contextualizar el diagnóstico. Las señales de salida deberán presentar la información procesada de manera comprensible para apoyar la toma de decisiones del usuario. (Sawant et al., 2026; Thilakarathne et al., 2022; Prity et al., 2024; FAO, 2026).
    </td>
    <td align="center">K.C, C.M</td>
  </tr>

  <tr>
    <td>/08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Control:</strong> El sistema de control deberá coordinar la adquisición de datos provenientes de los sensores y verificar que las mediciones se encuentren dentro de rangos válidos antes de procesarlas. El sistema deberá ejecutar la secuencia de medición, validación, análisis, diagnóstico, recomendación y almacenamiento. Asimismo, deberá registrar las acciones realizadas por el usuario y permitir una nueva medición para evaluar la evolución de las condiciones del suelo y del ambiente después de la intervención. En caso de detectar valores fuera del rango operativo de un sensor o información insuficiente, deberá advertir al usuario y evitar la generación de un diagnóstico basado en datos no válidos. (Sawant et al., 2026; Kiran et al., 2024).
    </td>
    <td align="center">A.D, K.C</td>
  </tr>

  <tr>
    <td>/08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Electrónico (hardware):</strong> El sistema utilizará un controlador o microcontrolador con capacidad suficiente para adquirir información de varios sensores y comunicarse con una interfaz externa. Se considera, como referencia, un dispositivo tipo ESP32, sin que ello excluya otras alternativas equivalentes que cumplan el mismo requisito funcional. El prototipo deberá integrar sensores para humedad del suelo, temperatura del suelo, pH del suelo, temperatura ambiental y humedad ambiental, además de los circuitos de acondicionamiento necesarios. Los módulos deberán ser reemplazables para facilitar el mantenimiento y futuras mejoras. (Sawant et al., 2026; Correa-Quiroz et al., 2025).
    </td>
    <td align="center">K.C, L.S</td>
  </tr>

  <tr>
    <td>/08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Software:</strong> El software deberá permitir adquirir, procesar, almacenar y visualizar la información obtenida de los sensores. Deberá incluir una interfaz amigable para el agricultor, evitando que sea necesario interpretar únicamente valores numéricos. El sistema deberá emplear algoritmos de procesamiento e inteligencia artificial para analizar simultáneamente las variables de humedad del suelo, temperatura del suelo, pH, temperatura ambiental y humedad ambiental, determinar el estado de las condiciones evaluadas y generar recomendaciones según el cultivo seleccionado. (Prity et al., 2024; Kiran et al., 2024; Gunasekaran et al., 2025).
    </td>
    <td align="center">A.D, K.C</td>
  </tr>

  <tr>
    <td>/08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Comunicaciones:</strong> El controlador deberá comunicarse correctamente con todos los sensores utilizados. Para la comunicación con la aplicación o interfaz de usuario se utilizará Wi-Fi, Bluetooth o ambos, según la arquitectura seleccionada. La ausencia temporal de conexión a Internet no deberá impedir realizar las mediciones básicas. Los datos podrán almacenarse localmente y sincronizarse posteriormente cuando exista conectividad. (Sawant et al., 2026; Thilakarathne et al., 2022).
    </td>
    <td align="center">L.S</td>
  </tr>

  <tr>
    <td>/08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Seguridad:</strong> Los componentes electrónicos deberán encontrarse protegidos frente al contacto directo con humedad, polvo y tierra. La alimentación eléctrica deberá trabajar con tensiones seguras para el usuario. El sistema deberá incorporar protección frente a cortocircuitos, polaridad incorrecta o condiciones eléctricas que puedan comprometer los componentes. La carcasa no deberá presentar bordes o superficies que generen riesgo durante la manipulación. (FAO, 2020).
    </td>
    <td align="center">C.M</td>
  </tr>

  <tr>
    <td>/08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Ergonomía:</strong> El equipo deberá ser manipulable por una sola persona. El peso total objetivo no deberá superar aproximadamente los 3 kg para facilitar su desplazamiento en campo. La interfaz deberá presentar la información mediante términos de fácil comprensión, por ejemplo: adecuado, atención y crítico, acompañados de los valores medidos y de la recomendación correspondiente. (FAO, 2026)
    </td>
    <td align="center">L.S</td>
  </tr>

  <tr>
    <td>/08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Fabricación:</strong> El prototipo deberá poder fabricarse utilizando materiales, sensores y componentes electrónicos disponibles comercialmente. Se priorizarán componentes de fácil adquisición y reemplazo. La carcasa podrá fabricarse mediante impresión 3D, mecanizado o materiales comerciales adecuados para protección de los componentes electrónicos. (Sawant et al., 2026)
    </td>
    <td align="center">K.C, A.D</td>
  </tr>

  <tr>
    <td>/08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Control de calidad:</strong> Antes de las pruebas en campo, los sensores deberán ser calibrados utilizando instrumentos o soluciones de referencia según corresponda. En particular, el sensor de pH deberá calibrarse utilizando soluciones buffer adecuadas. Las mediciones del prototipo deberán contrastarse con métodos o instrumentos de referencia para determinar su error. Se deberá comprobar individualmente el correcto funcionamiento de cada sensor, así como el funcionamiento conjunto del sistema antes de validar las recomendaciones generadas. (Sawant et al., 2026; Kiran et al., 2024).
    </td>
    <td align="center">L.S</td>
  </tr>

  <tr>
    <td>/08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Montaje:</strong> El diseño deberá ser modular para permitir el montaje y desmontaje de sensores, batería, controlador y demás componentes sin reconstruir completamente el equipo. Las conexiones deberán estar identificadas y aseguradas para evitar desconexiones accidentales durante el trabajo en campo. (Sawant et al., 2026)
    </td>
    <td align="center">L.S, C.M</td>
  </tr>

  <tr>
    <td>/08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Transporte:</strong> El dispositivo deberá ser transportable manualmente entre diferentes parcelas. La carcasa deberá proteger los componentes durante el traslado. Las sondas deberán contar con un sistema de almacenamiento o protección que reduzca el riesgo de daño durante el transporte.
    </td>
    <td align="center">L.S</td>
  </tr>

  <tr>
    <td>/08/2026</td>
    <td align="center">D</td>
    <td>
      <strong>Uso:</strong> Se desea que el sistema pueda utilizarse bajo diferentes condiciones ambientales presentes en zonas agrícolas. La secuencia de utilización deberá ser sencilla:<br><br>
      seleccionar parcela y cultivo → colocar las sondas → iniciar medición → obtener diagnóstico → visualizar recomendación → registrar la acción realizada → realizar una medición posterior. (FAO, 2026; FAO, 2020)
    </td>
    <td align="center">K.C</td>
  </tr>

  <tr>
    <td>/08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Mantenimiento:</strong> Los sensores que estén en contacto con el suelo deberán poder limpiarse después de cada medición. Los sensores que requieran calibración deberán poder ser retirados o calibrados sin desmontar completamente el prototipo. Los componentes electrónicos deberán poder reemplazarse individualmente en caso de falla.
    </td>
    <td align="center">A.D</td>
  </tr>

  <tr>
    <td>/08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Costos:</strong> Se buscará que el prototipo utiliza componentes comerciales de costo accesible. Como meta inicial de diseño, el costo de los componentes del prototipo no deberá superar aproximadamente S/ 1500, sujeto a modificación después de seleccionar y cotizar los sensores definitivos. (Sawant et al., 2026)
    </td>
    <td align="center">L.S</td>
  </tr>

  <tr>
    <td>/08/2026</td>
    <td align="center">E</td>
    <td>
      <strong>Plazos:</strong> El proyecto comprenderá las etapas de definición del problema, revisión del estado de la tecnología, determinación de variables del suelo, selección de sensores, diseño electrónico, desarrollo del software, desarrollo del algoritmo de inteligencia artificial, fabricación del prototipo, integración, calibración, pruebas experimentales y validación final. Las fechas específicas deberán establecerse mediante el plan de trabajo del proyecto. (Prity et al., 2024; Sawant et al., 2026)
    </td>
    <td align="center">A.D, K.C</td>
  </tr>

  </tbody>
</table>

---

# Bibliografía

## Lista de Requerimientos

[1] Food and Agriculture Organization of the United Nations, “FAO launches CropSuit app to help farmers grow the right crops in the right places,” Jul. 2, 2026. [Online]. Available:  
https://www.fao.org/newsroom/detail/fao-launches-cropsuit-app-to-help-farmers-grow-the-right-crops-in-the-right-places/en.  
[Accessed: Aug. 20, 2026].

[2] F. S. Prity, M. M. Hasan, S. H. Saif, M. M. Hossain, S. H. Bhuiyan, M. A. Islam, et al., “Enhancing agricultural productivity: A machine learning approach to crop recommendations,” *Human-Centric Intelligent Systems*, vol. 4, pp. 497–510, 2024, doi: 10.1007/s44230-024-00081-3.

[3] N. R. Sawant, A. Kumar, S. Pant, and K. Kotecha, “An IoT-driven machine learning system for real-time smart crop recommendation and optimization in precision agriculture,” *Discover Artificial Intelligence*, vol. 6, Art. no. 194, 2026, doi: 10.1007/s44163-026-00896-y.

[4] N. N. Thilakarathne, M. S. A. Bakar, P. E. Abas, and H. Yassin, “A cloud enabled crop recommendation platform for machine learning-driven precision farming,” *Sensors*, vol. 22, no. 16, Art. no. 6299, Aug. 2022, doi: 10.3390/s22166299.

[5] P. S. Kiran, G. Abhinaya, S. Sruti, and N. Padhy, “A machine learning-enabled system for crop recommendation,” *Engineering Proceedings*, vol. 67, no. 1, Art. no. 51, 2024, doi: 10.3390/engproc2024067051.

[6] H. Gunasekaran, K. Ramalakshmi, S. Debnath, and D. K. Swaminathan, “Physics-aware ensemble learning for superior crop recommendation in smart agriculture,” *Sensors*, vol. 25, no. 19, Art. no. 6243, Oct. 2025, doi: 10.3390/s25196243.

[7] Food and Agriculture Organization of the United Nations, “Crop suitability assessment,” *SoilFER Programme*. [Online]. Available:  
https://www.fao.org/in-action/soilfer/in-action/crop-suitability-assessment/en.  
[Accessed: Aug. 20, 2026].

[8] Food and Agriculture Organization of the United Nations, “SoilFER Programme—Soil mapping for resilient agrifood systems,” FAO. [Online]. Available:  
https://www.fao.org/in-action/soilfer/.  
[Accessed: Aug. 20, 2026].

[9] Food and Agriculture Organization of the United Nations, “Right crop, right place: What soil can tell us about the future of farming,” Jul. 2, 2026. [Online]. Available:  
https://www.fao.org/newsroom/story/right-crop-right-place/en.  
[Accessed: Aug. 20, 2026].

[10] Food and Agriculture Organization of the United Nations, “SoilFER CropSuit App,” 2026. [Online]. Available:  
https://data.apps.fao.org/soilfer/cropsuit.  
[Accessed: Aug. 20, 2026].

[11] FAO/GSP, *Soil Testing Methods Manual*. Food and Agriculture Organization of the United Nations, 2020. [Online]. Available:  
https://openknowledge.fao.org/items/08f3bf38-5df7-4c79-b78b-a8a910824969

[12] J. J. Correa-Quiroz, M. A. Toribio-Barrueto, and C. Castro-Vargas, “IoT system with ESP32 for smart drip irrigation and climate monitoring in greenhouses,” *Emerging Science Journal*, vol. 9, no. 3, pp. 1133–1157, 2025, doi: 10.28991/ESJ-2025-09-03-01.

[13] A. Saxena, A. Agarwal, B. Nagrath, C. S. Jayavanth, S. Thulasidoss, S. Maheswari, and P. Sasikumar, “Deep learning-driven IoT solution for smart tomato farming,” *Scientific Reports*, vol. 15, Art. no. 15615, 2025, doi: 10.1038/s41598-025-15615-3.

[14] A. Alawadhi and S. Patidar, “From Sensors to Insights: A Review of IoT Applications in Soil Health Monitoring and Precision Farming,” *International Journal of Applied Mathematics*, vol. 38, no. 10S, 2025, doi: 10.12732/ijam.v38i10s.1070.
