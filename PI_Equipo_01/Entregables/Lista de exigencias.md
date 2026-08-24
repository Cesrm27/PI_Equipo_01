![](./image1.png){width="4.828125546806649in"
height="1.4260673665791777in"}

**FACULTAD DE CIENCIAS E INGENIERÍA**

**DEPARTAMENTO ACADÉMICO DE INGENIERÍA**

**INGENIERÍA INFORMÁTICA E INGENIERÍA INDUSTRIAL**

+-----------------------------------------------------------------------+
| +------------------------------------------------------------------+  |
| | Semestre Académico 2026 II -- VI Ciclo                           |  |
| |                                                                  |  |
| | Semana N° 1 - Tema: "[Lista de exigencias]{.mark}"               |  |
| +==================================================================+  |
| +------------------------------------------------------------------+  |
+=======================================================================+
+-----------------------------------------------------------------------+

**[Docentes:]{.underline}**

Ing. [[Umbert Lewis De La Cruz
Rodriguez]{.underline}](mailto:umbert.de.la.cruz@upch.pe)

Ing. Vanessa Stefanny Stefanny arevalo

  -----------------------------------------------------------------------
  **Integrantes del  **Aporte/s en específico**               **% de
  equipo**                                                    aporte**
  ------------------ ---------------------------------------- -----------
  Cesar Rodrigo      Definió qué debe hacer el sistema en     25%
  Milla Gómez        general, qué información entra y sale de 
                     él, y se encargó de los temas de         
                     seguridad y armado del equipo.           

  Anderson Josue     Diseñó el tamaño y la forma del equipo,  25%
  Delerna Infantes   cómo se alimenta de energía, cómo        
                     funciona el control del sistema, el      
                     software, y organizó el cronograma y el  
                     mantenimiento.                           

  Kevin Esty         Diseñó cómo se colocan las sondas en el  25%
  Carvallo Neciosup  suelo, ayudó con la información que      
                     maneja el sistema, el control, la parte  
                     electrónica (sensores y                  
                     microcontrolador), el software y cómo lo 
                     usará el agricultor.                     

  Shedira Lumeris    Revisó qué tan resistente es el equipo,  25%
  Sihuincha Palacin  la parte electrónica, cómo se conecta    
                     Wi-Fi/Bluetooth, qué tan cómodo es de    
                     usar, calibró los sensores, y se encargó 
                     del transporte y los costos del          
                     prototipo.                               

  **Equipo**         **Informe final**                        **100%**
  -----------------------------------------------------------------------

# 

# **1. Lista de Exigencias** 

**Tabla 1: Lista de Exigencias**

+------+-------+-----------------------------------------+-------------+
| **L  |       |                                         | **Páginas:  |
| ISTA |       |                                         | 5**         |
| DE   |       |                                         |             |
| EXIG |       |                                         |             |
| ENCI |       |                                         |             |
| AS** |       |                                         |             |
+======+=======+=========================================+=============+
|      |       |                                         | **Edición:  |
|      |       |                                         | Rev. 1**    |
+------+-------+-----------------------------------------+-------------+
| *    |       | **AgroMind AI -- Sistema inteligente de | **Fecha:    |
| *PRO |       | diagnóstico y monitoreo del estado del  | 2           |
| YECT |       | suelo**                                 | 5/08/2026** |
| O:** |       |                                         |             |
+------+-------+-----------------------------------------+-------------+
|      |       |                                         | **          |
|      |       |                                         | Revisado:** |
+------+-------+-----------------------------------------+-------------+
| **CL |       | **Universidad Peruana Cayetano Heredia  | **E         |
| IENT |       | (UPCH)**                                | laborado:** |
| E:** |       |                                         |             |
|      |       |                                         | **K.C, A.D, |
|      |       |                                         | C.M, L.S**  |
+------+-------+-----------------------------------------+-------------+
| F    | Deseo | **Descripción**                         | **Re        |
| echa | o     |                                         | sponsable** |
| (    | Exig  |                                         |             |
| camb | encia |                                         |             |
| ios) |       |                                         |             |
+------+-------+-----------------------------------------+-------------+
| **/0 | E     | Función general: El sistema deberá      | C.M, K.C,   |
| 8/20 |       | realizar mediciones de parámetros       | A.D,L.S     |
| 26** |       | físicos y químicos del suelo y del      |             |
|      |       | ambiente, procesar la información       |             |
|      |       | obtenida mediante sensores y generar un |             |
|      |       | diagnóstico comprensible para el        |             |
|      |       | agricultor. Como mínimo deberá          |             |
|      |       | considerar humedad del suelo,           |             |
|      |       | temperatura del suelo, pH del suelo,    |             |
|      |       | temperatura ambiental y humedad         |             |
|      |       | ambiental. A partir de las mediciones y |             |
|      |       | de la información del cultivo y de la   |             |
|      |       | parcela, el sistema deberá identificar  |             |
|      |       | posibles condiciones que puedan afectar |             |
|      |       | el desarrollo del cultivo y generar     |             |
|      |       | recomendaciones de manejo. Además,      |             |
|      |       | deberá registrar las acciones           |             |
|      |       | realizadas por el usuario y permitir    |             |
|      |       | realizar nuevas mediciones para         |             |
|      |       | verificar y comparar la evolución de    |             |
|      |       | las condiciones antes y después de la   |             |
|      |       | intervención. (FAO, 2026; Prity et al., |             |
|      |       | 2024; Sawant et al., 2026; Alawadhi y   |             |
|      |       | Patidar, 2025).                         |             |
+------+-------+-----------------------------------------+-------------+
| **/0 | E     | Geometría: El sistema deberá presentar  | A.D         |
| 8/20 |       | una configuración portátil y compacta   |             |
| 26** |       | que permita su utilización directamente |             |
|      |       | en campo. La unidad principal, sin      |             |
|      |       | considerar las sondas, no deberá        |             |
|      |       | superar aproximadamente 30 cm × 25 cm × |             |
|      |       | 20 cm. Las sondas destinadas a la       |             |
|      |       | medición deberán permitir trabajar en   |             |
|      |       | la zona superficial de raíces, con una  |             |
|      |       | profundidad aproximada de 10 a 20 cm,   |             |
|      |       | dependiendo del cultivo.                |             |
+------+-------+-----------------------------------------+-------------+
| **/0 | E     | Cinemática: El prototipo no requerirá   | K.C         |
| 8/20 |       | mecanismos de movimiento continuo       |             |
| 26** |       | durante la operación. La inserción y    |             |
|      |       | extracción de las sondas se realizará   |             |
|      |       | manualmente. El diseño deberá permitir  |             |
|      |       | que la colocación del sensor en el      |             |
|      |       | suelo pueda realizarse sin movimientos  |             |
|      |       | complejos y sin necesidad de            |             |
|      |       | herramientas adicionales. (FAO, 2020)   |             |
+------+-------+-----------------------------------------+-------------+
| **/0 | E     | Fuerzas: Las sondas de medición deberán | L.S         |
| 8/20 |       | soportar la fuerza de inserción manual  |             |
| 26** |       | necesaria para su utilización en suelo  |             |
|      |       | agrícola sin presentar deformaciones    |             |
|      |       | permanentes durante condiciones         |             |
|      |       | normales de trabajo. La estructura y    |             |
|      |       | carcasa deberán soportar la             |             |
|      |       | manipulación y transporte del           |             |
|      |       | dispositivo sin comprometer los         |             |
|      |       | sensores ni los componentes             |             |
|      |       | electrónicos. (FAO, 2020).              |             |
+------+-------+-----------------------------------------+-------------+
| **/0 | E     | Energía: El sistema deberá funcionar    | A.D         |
| 8/20 |       | mediante una fuente de alimentación     |             |
| 26** |       | portátil de bajo voltaje,               |             |
|      |       | preferentemente mediante una batería    |             |
|      |       | recargable, con una autonomía mínima    |             |
|      |       | objetivo de 8 horas de operación.       |             |
|      |       | Asimismo, deberá permitir conocer el    |             |
|      |       | estado o porcentaje aproximado de carga |             |
|      |       | disponible. (Sawant et al., 2026;       |             |
|      |       | Saxena et al., 2025).                   |             |
|      |       |                                         |             |
|      |       | ● La alimentación de los sensores y     |             |
|      |       | componentes electrónicos deberá ser     |             |
|      |       | compatible con los niveles de tensión   |             |
|      |       | requeridos por cada dispositivo.        |             |
|      |       |                                         |             |
|      |       | ● Se priorizará el uso de una batería   |             |
|      |       | recargable que permita el               |             |
|      |       | funcionamiento del sistema durante las  |             |
|      |       | actividades de medición en campo,       |             |
|      |       | evitando depender de una conexión       |             |
|      |       | eléctrica permanente.                   |             |
|      |       |                                         |             |
|      |       | ● El sistema deberá permitir verificar  |             |
|      |       | el nivel de carga disponible para       |             |
|      |       | evitar interrupciones durante la toma   |             |
|      |       | de datos.                               |             |
+------+-------+-----------------------------------------+-------------+
| **/0 | E     | Materia: El material de entrada al      | L.S         |
| 8/20 |       | sistema será el suelo agrícola, del     |             |
| 26** |       | cual se obtendrán las variables         |             |
|      |       | necesarias para determinar sus          |             |
|      |       | condiciones. Los elementos que entren   |             |
|      |       | directamente en contacto con el suelo   |             |
|      |       | deberán ser resistentes a la humedad y  |             |
|      |       | corrosión. La medición no deberá        |             |
|      |       | incorporar sustancias que alteren       |             |
|      |       | significativamente las características  |             |
|      |       | del suelo analizado. (FAO, 2020)        |             |
+------+-------+-----------------------------------------+-------------+
| **/0 | E     | Señales (Información): El sistema       | K.C,C.M     |
| 8/20 |       | deberá contar con señales de entrada y  |             |
| 26** |       | salida asociadas al proceso de          |             |
|      |       | diagnóstico y seguimiento del suelo.    |             |
|      |       |                                         |             |
|      |       | Señales de entrada:                     |             |
|      |       |                                         |             |
|      |       | -   Humedad del suelo.                  |             |
|      |       |                                         |             |
|      |       | -   Temperatura del suelo.              |             |
|      |       |                                         |             |
|      |       | -   pH del suelo.                       |             |
|      |       |                                         |             |
|      |       | -   Temperatura ambiental.              |             |
|      |       |                                         |             |
|      |       | -   Humedad ambiental.                  |             |
|      |       |                                         |             |
|      |       | -   Identificación de la parcela.       |             |
|      |       |                                         |             |
|      |       | -   Cultivo seleccionado.               |             |
|      |       |                                         |             |
|      |       | -   Etapa del cultivo.                  |             |
|      |       |                                         |             |
|      |       | -   Comandos e información ingresada    |             |
|      |       |     > por el usuario.                   |             |
|      |       |                                         |             |
|      |       | Señales de salida:                      |             |
|      |       |                                         |             |
|      |       | -   Valores obtenidos de los sensores.  |             |
|      |       |                                         |             |
|      |       | -   Estado de funcionamiento de los     |             |
|      |       |     > sensores.                         |             |
|      |       |                                         |             |
|      |       | -   Diagnóstico de las condiciones del  |             |
|      |       |     > suelo.                            |             |
|      |       |                                         |             |
|      |       | -   Alertas ante condiciones anormales  |             |
|      |       |     > o datos no válidos.               |             |
|      |       |                                         |             |
|      |       | -   Recomendaciones de manejo.          |             |
|      |       |                                         |             |
|      |       | -   Registro de las acciones            |             |
|      |       |     > realizadas.                       |             |
|      |       |                                         |             |
|      |       | -   Historial de mediciones.            |             |
|      |       |                                         |             |
|      |       | -   Comparación de la evolución de las  |             |
|      |       |     > condiciones antes y después de la |             |
|      |       |     > intervención.                     |             |
|      |       |                                         |             |
|      |       | Las señales provenientes de los         |             |
|      |       | sensores permitirán obtener información |             |
|      |       | sobre las condiciones del suelo y del   |             |
|      |       | ambiente, mientras que la información   |             |
|      |       | del cultivo y de la parcela permitirá   |             |
|      |       | contextualizar el diagnóstico. Las      |             |
|      |       | señales de salida deberán presentar la  |             |
|      |       | información procesada de manera         |             |
|      |       | comprensible para apoyar la toma de     |             |
|      |       | decisiones del usuario. (Sawant et al., |             |
|      |       | 2026; Thilakarathne et al., 2022; Prity |             |
|      |       | et al., 2024; FAO, 2026).               |             |
+------+-------+-----------------------------------------+-------------+
| **/0 | E     | Control: El sistema de control deberá   | A.D, K.C    |
| 8/20 |       | coordinar la adquisición de datos       |             |
| 26** |       | provenientes de los sensores y          |             |
|      |       | verificar que las mediciones se         |             |
|      |       | encuentren dentro de rangos válidos     |             |
|      |       | antes de procesarlas. El sistema deberá |             |
|      |       | ejecutar la secuencia de medición,      |             |
|      |       | validación, análisis, diagnóstico,      |             |
|      |       | recomendación y almacenamiento.         |             |
|      |       | Asimismo, deberá registrar las acciones |             |
|      |       | realizadas por el usuario y permitir    |             |
|      |       | una nueva medición para evaluar la      |             |
|      |       | evolución de las condiciones del suelo  |             |
|      |       | y del ambiente después de la            |             |
|      |       | intervención. En caso de detectar       |             |
|      |       | valores fuera del rango operativo de un |             |
|      |       | sensor o información insuficiente,      |             |
|      |       | deberá advertir al usuario y evitar la  |             |
|      |       | generación de un diagnóstico basado en  |             |
|      |       | datos no válidos. (Sawant et al., 2026; |             |
|      |       | Kiran et al., 2024).                    |             |
+------+-------+-----------------------------------------+-------------+
| **/0 | E     | Electrónico (hardware): El sistema      | K.C, L.S    |
| 8/20 |       | utilizará un controlador o              |             |
| 26** |       | microcontrolador con capacidad          |             |
|      |       | suficiente para adquirir información de |             |
|      |       | varios sensores y comunicarse con una   |             |
|      |       | interfaz externa. Se considera, como    |             |
|      |       | referencia, un dispositivo tipo ESP32,  |             |
|      |       | sin que ello excluya otras alternativas |             |
|      |       | equivalentes que cumplan el mismo       |             |
|      |       | requisito funcional. El prototipo       |             |
|      |       | deberá integrar sensores para humedad   |             |
|      |       | del suelo, temperatura del suelo, pH    |             |
|      |       | del suelo, temperatura ambiental y      |             |
|      |       | humedad ambiental, además de los        |             |
|      |       | circuitos de acondicionamiento          |             |
|      |       | necesarios. Los módulos deberán ser     |             |
|      |       | reemplazables para facilitar el         |             |
|      |       | mantenimiento y futuras mejoras.        |             |
|      |       | (Sawant et al., 2026; Correa-Quiroz et  |             |
|      |       | al., 2025).                             |             |
+------+-------+-----------------------------------------+-------------+
| **/0 | E     | Software: El software deberá permitir   | A.D, K.C    |
| 8/20 |       | adquirir, procesar, almacenar y         |             |
| 26** |       | visualizar la información obtenida de   |             |
|      |       | los sensores. Deberá incluir una        |             |
|      |       | interfaz amigable para el agricultor,   |             |
|      |       | evitando que sea necesario interpretar  |             |
|      |       | únicamente valores numéricos. El        |             |
|      |       | sistema deberá emplear algoritmos de    |             |
|      |       | procesamiento e inteligencia artificial |             |
|      |       | para analizar simultáneamente las       |             |
|      |       | variables de humedad del suelo,         |             |
|      |       | temperatura del suelo, pH, temperatura  |             |
|      |       | ambiental y humedad ambiental,          |             |
|      |       | determinar el estado de las condiciones |             |
|      |       | evaluadas y generar recomendaciones     |             |
|      |       | según el cultivo seleccionado. (Prity   |             |
|      |       | et al., 2024; Kiran et al., 2024;       |             |
|      |       | Gunasekaran et al., 2025).              |             |
+------+-------+-----------------------------------------+-------------+
| **/0 | E     | Comunicaciones: El controlador deberá   | L,S         |
| 8/20 |       | comunicarse correctamente con todos los |             |
| 26** |       | sensores utilizados. Para la            |             |
|      |       | comunicación con la aplicación o        |             |
|      |       | interfaz de usuario se utilizará Wi-Fi, |             |
|      |       | Bluetooth o ambos, según la             |             |
|      |       | arquitectura seleccionada. La ausencia  |             |
|      |       | temporal de conexión a Internet no      |             |
|      |       | deberá impedir realizar las mediciones  |             |
|      |       | básicas. Los datos podrán almacenarse   |             |
|      |       | localmente y sincronizarse              |             |
|      |       | posteriormente cuando exista            |             |
|      |       | conectividad. (Sawant et al., 2026;     |             |
|      |       | Thilakarathne et al., 2022).            |             |
+------+-------+-----------------------------------------+-------------+
| **/0 | E     | Seguridad: Los componentes electrónicos | C.M         |
| 8/20 |       | deberán encontrarse protegidos frente   |             |
| 26** |       | al contacto directo con humedad, polvo  |             |
|      |       | y tierra. La alimentación eléctrica     |             |
|      |       | deberá trabajar con tensiones seguras   |             |
|      |       | para el usuario. El sistema deberá      |             |
|      |       | incorporar protección frente a          |             |
|      |       | cortocircuitos, polaridad incorrecta o  |             |
|      |       | condiciones eléctricas que puedan       |             |
|      |       | comprometer los componentes. La carcasa |             |
|      |       | no deberá presentar bordes o            |             |
|      |       | superficies que generen riesgo durante  |             |
|      |       | la manipulación. (FAO, 2020) .          |             |
+------+-------+-----------------------------------------+-------------+
| **/0 | E     | Ergonomía: El equipo deberá ser         | L,S         |
| 8/20 |       | manipulable por una sola persona. El    |             |
| 26** |       | peso total objetivo no deberá superar   |             |
|      |       | aproximadamente los 3 kg para facilitar |             |
|      |       | su desplazamiento en campo. La interfaz |             |
|      |       | deberá presentar la información         |             |
|      |       | mediante términos de fácil comprensión, |             |
|      |       | por ejemplo: adecuado, atención y       |             |
|      |       | crítico, acompañados de los valores     |             |
|      |       | medidos y de la recomendación           |             |
|      |       | correspondiente. (FAO, 2026)            |             |
+------+-------+-----------------------------------------+-------------+
| **/0 | E     | Fabricación: El prototipo deberá poder  | K.C, A.D    |
| 8/20 |       | fabricarse utilizando materiales,       |             |
| 26** |       | sensores y componentes electrónicos     |             |
|      |       | disponibles comercialmente. Se          |             |
|      |       | priorizarán componentes de fácil        |             |
|      |       | adquisición y reemplazo. La carcasa     |             |
|      |       | podrá fabricarse mediante impresión 3D, |             |
|      |       | mecanizado o materiales comerciales     |             |
|      |       | adecuados para protección de los        |             |
|      |       | componentes electrónicos. (Sawant et    |             |
|      |       | al., 2026)                              |             |
+------+-------+-----------------------------------------+-------------+
| **/0 | E     | Control de calidad: Antes de las        | L.S         |
| 8/20 |       | pruebas en campo, los sensores deberán  |             |
| 26** |       | ser calibrados utilizando instrumentos  |             |
|      |       | o soluciones de referencia según        |             |
|      |       | corresponda. En particular, el sensor   |             |
|      |       | de pH deberá calibrarse utilizando      |             |
|      |       | soluciones buffer adecuadas. Las        |             |
|      |       | mediciones del prototipo deberán        |             |
|      |       | contrastarse con métodos o instrumentos |             |
|      |       | de referencia para determinar su error. |             |
|      |       | Se deberá comprobar individualmente el  |             |
|      |       | correcto funcionamiento de cada sensor, |             |
|      |       | así como el funcionamiento conjunto del |             |
|      |       | sistema antes de validar las            |             |
|      |       | recomendaciones generadas. (Sawant et   |             |
|      |       | al., 2026; Kiran et al., 2024).         |             |
+------+-------+-----------------------------------------+-------------+
| **/0 | E     | Montaje:. El diseño deberá ser modular  | L.S, C.M    |
| 8/20 |       | para permitir el montaje y desmontaje   |             |
| 26** |       | de sensores, batería, controlador y     |             |
|      |       | demás componentes sin reconstruir       |             |
|      |       | completamente el equipo. Las conexiones |             |
|      |       | deberán estar identificadas y           |             |
|      |       | aseguradas para evitar desconexiones    |             |
|      |       | accidentales durante el trabajo en      |             |
|      |       | campo. (Sawant et al., 2026)            |             |
+------+-------+-----------------------------------------+-------------+
| **/0 | E     | Transporte: El dispositivo deberá ser   | L.S         |
| 8/20 |       | transportable manualmente entre         |             |
| 26** |       | diferentes parcelas. La carcasa deberá  |             |
|      |       | proteger los componentes durante el     |             |
|      |       | traslado. Las sondas deberán contar con |             |
|      |       | un sistema de almacenamiento o          |             |
|      |       | protección que reduzca el riesgo de     |             |
|      |       | daño durante el transporte. (           |             |
+------+-------+-----------------------------------------+-------------+
| **/0 | D     | Uso: Se desea que el sistema pueda      | K,C         |
| 8/20 |       | utilizarse bajo diferentes condiciones  |             |
| 26** |       | ambientales presentes en zonas          |             |
|      |       | agrícolas. La secuencia de utilización  |             |
|      |       | deberá ser sencilla: seleccionar        |             |
|      |       | parcela y cultivo → colocar las sondas  |             |
|      |       | → iniciar medición → obtener            |             |
|      |       | diagnóstico → visualizar recomendación  |             |
|      |       | → registrar la acción realizada →       |             |
|      |       | realizar una medición posterior. (FAO,  |             |
|      |       | 2026; FAO, 2020)                        |             |
+------+-------+-----------------------------------------+-------------+
| **/0 | E     | Mantenimiento:                          | A,D         |
| 8/20 |       |                                         |             |
| 26** |       | Los sensores que estén en contacto con  |             |
|      |       | el suelo deberán poder limpiarse        |             |
|      |       | después de cada medición. Los sensores  |             |
|      |       | que requieran calibración deberán poder |             |
|      |       | ser retirados o calibrados sin          |             |
|      |       | desmontar completamente el prototipo.   |             |
|      |       | Los componentes electrónicos deberán    |             |
|      |       | poder reemplazarse individualmente en   |             |
|      |       | caso de falla                           |             |
+------+-------+-----------------------------------------+-------------+
| **/0 | E     | Costos: Se buscará que el prototipo     | L,S         |
| 8/20 |       | utiliza componentes comerciales de      |             |
| 26** |       | costo accesible. Como meta inicial de   |             |
|      |       | diseño, el costo de los componentes del |             |
|      |       | prototipo no deberá superar             |             |
|      |       | aproximadamente S/ 1500, sujeto a       |             |
|      |       | modificación después de seleccionar y   |             |
|      |       | cotizar los sensores definitivos.       |             |
|      |       | (Sawant et al., 2026)                   |             |
+------+-------+-----------------------------------------+-------------+
| **/0 | E     | Plazos: El proyecto comprenderá las     | A.D, K.C    |
| 8/20 |       | etapas de definición del problema,      |             |
| 26** |       | revisión del estado de la tecnología,   |             |
|      |       | determinación de variables del suelo,   |             |
|      |       | selección de sensores, diseño           |             |
|      |       | electrónico, desarrollo del software,   |             |
|      |       | desarrollo del algoritmo de             |             |
|      |       | inteligencia artificial, fabricación    |             |
|      |       | del prototipo, integración,             |             |
|      |       | calibración, pruebas experimentales y   |             |
|      |       | validación final. Las fechas            |             |
|      |       | específicas deberán establecerse        |             |
|      |       | mediante el plan de trabajo del         |             |
|      |       | proyecto. (Prity et al., 2024; Sawant   |             |
|      |       | et al., 2026)                           |             |
+------+-------+-----------------------------------------+-------------+

# **Bibliografía**

**[Lista de Requerimientos]{.mark}**

\[1\] Food and Agriculture Organization of the United Nations, "FAO
launches CropSuit app to help farmers grow the right crops in the right
places," Jul. 2, 2026. \[Online\]. Available:
[[https://www.fao.org/newsroom/detail/fao-launches-cropsuit-app-to-help-farmers-grow-the-right-crops-in-the-right-places/en]{.underline}](https://www.fao.org/newsroom/detail/fao-launches-cropsuit-app-to-help-farmers-grow-the-right-crops-in-the-right-places/en?utm_source=chatgpt.com).
\[Accessed: Aug. 20, 2026\].

\[2\] F. S. Prity, M. M. Hasan, S. H. Saif, M. M. Hossain, S. H.
Bhuiyan, M. A. Islam, *et al*., "Enhancing agricultural productivity: A
machine learning approach to crop recommendations," *Human-Centric
Intelligent Systems*, vol. 4, pp. 497--510, 2024, doi:
10.1007/s44230-024-00081-3.

\[3\] N. R. Sawant, A. Kumar, S. Pant, and K. Kotecha, "An IoT-driven
machine learning system for real-time smart crop recommendation and
optimization in precision agriculture," *Discover Artificial
Intelligence*, vol. 6, Art. no. 194, 2026, doi:
10.1007/s44163-026-00896-y.

\[4\] N. N. Thilakarathne, M. S. A. Bakar, P. E. Abas, and H. Yassin, "A
cloud enabled crop recommendation platform for machine learning-driven
precision farming," *Sensors*, vol. 22, no. 16, Art. no. 6299, Aug.
2022, doi: 10.3390/s22166299.

\[5\] P. S. Kiran, G. Abhinaya, S. Sruti, and N. Padhy, "A machine
learning-enabled system for crop recommendation," *Engineering
Proceedings*, vol. 67, no. 1, Art. no. 51, 2024, doi:
10.3390/engproc2024067051.

\[6\] H. Gunasekaran, K. Ramalakshmi, S. Debnath, and D. K. Swaminathan,
"Physics-aware ensemble learning for superior crop recommendation in
smart agriculture," *Sensors*, vol. 25, no. 19, Art. no. 6243, Oct.
2025, doi: 10.3390/s25196243.

\[7\] Food and Agriculture Organization of the United Nations, "Crop
suitability assessment," *SoilFER Programme*. \[Online\]. Available:
[[https://www.fao.org/in-action/soilfer/in-action/crop-suitability-assessment/en]{.underline}](https://www.fao.org/in-action/soilfer/in-action/crop-suitability-assessment/en?utm_source=chatgpt.com).
\[Accessed: Aug. 20, 2026\].

\[8\] Food and Agriculture Organization of the United Nations, "SoilFER
Programme---Soil mapping for resilient agrifood systems," FAO.
\[Online\]. Available: https://www.fao.org/in-action/soilfer/.
\[Accessed: Aug. 20, 2026\].

\[9\] Food and Agriculture Organization of the United Nations, "Right
crop, right place: What soil can tell us about the future of farming,"
Jul. 2, 2026. \[Online\]. Available:
[[https://www.fao.org/newsroom/story/right-crop-right-place/en]{.underline}](https://www.fao.org/newsroom/story/right-crop-right-place/en?utm_source=chatgpt.com).
\[Accessed: Aug. 20, 2026\].

\[10\] Food and Agriculture Organization of the United Nations, "SoilFER
CropSuit App," 2026. \[Online\]. Available:
[[https://data.apps.fao.org/soilfer/cropsuit]{.underline}](https://data.apps.fao.org/soilfer/cropsuit?utm_source=chatgpt.com).
\[Accessed: Aug. 20, 2026\].

\[11\] FAO/GSP, *Soil Testing Methods Manual*. Food and Agriculture
Organization of the United Nations, 2020. \[Online\]. Available:
[[https://openknowledge.fao.org/items/08f3bf38-5df7-4c79-b78b-a8a910824969]{.underline}](https://openknowledge.fao.org/items/08f3bf38-5df7-4c79-b78b-a8a910824969)

\[12\] J. J. Correa-Quiroz, M. A. Toribio-Barrueto, and C.
Castro-Vargas, \"IoT system with ESP32 for smart drip irrigation and
climate monitoring in greenhouses,\" *Emerging Science Journal*, vol. 9,
no. 3, pp. 1133-1157, 2025, doi: 10.28991/ESJ-2025-09-03-01.

\[13\] A. Saxena, A. Agarwal, B. Nagrath, C. S. Jayavanth, S.
Thulasidoss, S. Maheswari, and P. Sasikumar, \"Deep learning-driven IoT
solution for smart tomato farming,\" *Scientific Reports*, vol. 15, Art.
no. 15615, 2025, doi: 10.1038/s41598-025-15615-3.

\[14\] A. Alawadhi and S. Patidar, "From Sensors to Insights: A Review
of IoT Applications in Soil Health Monitoring and Precision Farming,"
*International Journal of Applied Mathematics*, vol. 38, no. 10S, 2025,
doi: 10.12732/ijam.v38i10s.1070.
