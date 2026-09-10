[![Ver Matriz Morfológica](https://github.com/Cesrm27/PI_Equipo_01/blob/main/PI_Equipo_01/Entregables/Matriz%20Morfol%C3%B3gica%20GREENPLANT.pdf)]


# 📊 Evaluación de la Matriz Morfológica (Metodología VDI 2206)
### Proyecto GREENPLANT AI — Monitoreo IoT en Cultivo de Papa

A continuación se presentan las tablas de evaluación sistemática para la selección de la arquitectura del prototipo mecatrónico e IoT.

---

### 1. 📌 Instrucciones
*Ruta de trabajo y pasos de evaluación metodológica:*

| Paso | Detalle |
| :---: | :--- |
| **1** | **Matriz:** revisa subfunciones y alternativas; lee 'Notas' para incompatibilidades. |
| **2** | **Conceptos:** combina 1 alternativa por subfunción (A, B, C). |
| **3** | **Criterios:** define pesos (suman 1,0) y justifícalos en tu proyecto. |
| **4** | **Puntajes (1-5):** valora cada concepto por criterio (5 = mejor). |
| **5** | **Pugh:** compara B y C contra A con +/0/-; revisa sumas. |
| **6** | **Ponderado:** calcula Total ponderado = SUMA(peso * puntaje). |
| **7** | **Selecciona** los concepto líderes y registra riesgos/ensayos a planificar. |

---

### 2. 📝 Notas de Interfaz / Compatibilidad
*Restricciones técnicas y de acoplamiento identificadas:*

| # | Notas de interfaz / compatibilidad |
| :-: | :--- |
| **1** | El ESP32 básico no trae ADC de alta resolución ni puerto UART libre de sobra. |
| **2** | El sensor MQ-137 requiere tiempo de precalentamiento (~24-48h la primera vez). |
| **3** | La alimentación por power bank USB no es compatible con una cámara con ventilación continua o calefactores. |
| **4** | El protocolo Wi-Fi + Firebase requiere cobertura de red estable; en parcelas remotas presenta limitaciones. |
| **5** | El gabinete IP65 y la cámara con bomba de muestreo elevan el costo y la complejidad de ensamblaje. |
| **6** | La nueva subfunción 'Liberar gases acumulados' debe ser compatible con la arquitectura de la cámara. |

---

### 3. 🧩 Matriz Morfológica Completa
*Desglose por subsistema, funciones y portadores de solución:*

| Subsistema | Función | Alternativa 1 | Alternativa 2 | Alternativa 3 |
| :--- | :--- | :--- | :--- | :--- |
| **SENSADO** | Detectar concentración de NH3 | MQ-137 | ZE03-NH3 | ME3-NH3 |
| **SENSADO** | Detectar concentración de CO2 | SCD41 | MH-Z19B | SCD30 |
| **SENSADO** | Medir temperatura y humedad ambiental | DHT22 | BME280 | SHT31 |
| **SENSADO** | Medir condiciones del suelo | Humedad capacitiva | Humedad + temperatura | Sensor multiparámetro |
| **PROCESAMIENTO** | Procesar información | ESP32 | ESP32 | Raspberry Pi |
| **MECÁNICO** | Capturar / concentrar gases para medición | Cámara cerrada estática | Cámara ventilada | Cámara con bomba de muestreo |
| **MECÁNICO** | Proteger componentes electrónicos | Caja impresa PLA | Carcasa impresa PETG | Gabinete IP65 |
| **MECÁNICO** | Ubicar sensores en el cultivo | Cerca del suelo | En la cámara | Soporte regulable |
| **MECÁNICO** | Fijar el sistema al terreno | Trípode | Base con púas | Estructura atornillada |
| **MECÁNICO** | Liberar gases acumulados | Tapa desmontable o abatible | Ventilador/extractor con rejilla | Válvula de ventilación |
| **MECÁNICO** | Iluminación | Lámpara | Tira led | Foco |
| **MECÁNICO** | Encendido/apagado - Inicio/Detener | Botón pulsador | Interruptor switch | Interruptor switch |
| **ENERGÍA** | Alimentar el sistema | Power bank USB | Batería Li-ion | Panel solar + batería |
| **ENERGÍA** | Regular y distribuir energía | LM2596 | LM2596 | Módulo BMS |
| **CONTROL** | Gestionar adquisición de datos | Muestreo periódico | Muestreo por umbral | Muestreo adaptativo |
| **SOFTWARE** | Interfaz de usuario | Pantalla OLED | App móvil | Dashboard web |
| **SOFTWARE** | Protocolo de comunicación | Bluetooth | Wi-Fi + MQTT | Wi-Fi + Firebase |
| **SOFTWARE** | Almacenamiento histórico | MicroSD | Nube | Base de datos local |
| **SOFTWARE** | Exportar información | CSV | Excel / Sheets | API para ML |

---

### 4. 💡 Definición de Conceptos
*Combinación de alternativas morfológicas (desliza horizontalmente para ver las 19 subfunciones):*

<div style="overflow-x: auto;">

| Concepto | NH3 | CO2 | Temp/Hum Amb. | Condiciones Suelo | Procesamiento | Captura Gases | Carcasa | Ubicación Sensores | Fijación | Liberar Gases | Iluminación | Encendido/Inicio | Alimentación | Regulación | Muestreo | Interfaz | Comunicación | Almacenamiento | Exportar |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Concepto A (Básica)** | MQ-137 | SCD41 | DHT22 | Humedad capacitiva | ESP32 | Cámara cerrada estática | Caja impresa PLA | Cerca del suelo | Trípode | Tapa abatible | Lámpara | Botón pulsador | Power bank USB | LM2596 | Periódico | Pantalla OLED | Bluetooth | MicroSD | CSV |
| **Concepto B (Equilibrada)** | ZE03-NH3 | MH-Z19B | BME280 | Humedad + temp. | ESP32 | Cámara ventilada | Carcasa PETG | En la cámara | Base con púas | Extractor c/rejilla | Tira led | Interruptor switch | Batería Li-ion | LM2596 | Por umbral | App móvil | Wi-Fi + MQTT | Nube | Excel / Sheets |
| **Concepto C (Avanzada)** | ME3-NH3 | SCD30 | SHT31 | Multiparámetro | Raspberry Pi | Bomba de muestreo | Gabinete IP65 | Soporte regulable | Atornillada | Válvula ventilación | Foco | Interruptor switch | Panel + batería | Módulo BMS | Adaptativo | Dashboard web | Wi-Fi + Firebase | BD local | API para ML |
| **Concepto Seleccionado** | **ZE03-NH3** | **MH-Z19B** | **BME280** | **Humedad + temp.** | **ESP32** | **Cámara ventilada** | **Carcasa PETG** | **En la cámara** | **Base con púas** | **Extractor c/rejilla** | **Tira led** | **Interruptor switch** | **Batería Li-ion** | **LM2596** | **Por umbral** | **App móvil** | **Wi-Fi + MQTT** | **Nube** | **Excel / Sheets** |

</div>

---

### 5. 🎯 Puntajes de Conceptos (Escala 1 al 5)
*(Donde 5 representa la mejor valoración para el proyecto)*

| Criterio | Concepto A (Base) | Concepto B | Concepto C |
| :--- | :---: | :---: | :---: |
| **Precisión de detección de gases (NH3/CO2)** | 2 | 5 | 2 |
| **Costo del sistema (BOM)** | 4 | 1 | 3 |
| **Autonomía energética** | 2 | 4 | 3 |
| **Complejidad de implementación (menor es mejor)** | 5 | 2 | 3 |
| **Escalabilidad y conectividad (IoT)** | 1 | 5 | 4 |
| **Robustez ambiental (campo/intemperie)** | 1 | 5 | 3 |

---

### 6. ⚖️ Criterios y Ponderación

| Criterio | Peso ($W_i$) |
| :--- | :---: |
| **Precisión de detección de gases (NH3/CO2)** | 0.25 |
| **Costo del sistema (BOM)** | 0.20 |
| **Autonomía energética** | 0.15 |
| **Complejidad de implementación (menor es mejor)** | 0.20 |
| **Escalabilidad y conectividad (IoT)** | 0.10 |
| **Robustez ambiental (campo/intemperie)** | 0.10 |
| **TOTAL** | **1.00 (100%)** |

---

### 7. 🥊 Matriz de Pugh
*Evaluación relativa tomando el **Concepto A como Línea Base (0)**:*

| Criterio | Base (A) | B vs A | C vs A |
| :--- | :---: | :---: | :---: |
| **Precisión de detección de gases (NH3/HCN)** | 0 | 1 | 1 |
| **Costo del sistema (BOM)** | 0 | -1 | -1 |
| **Autonomía energética** | 0 | 1 | 1 |
| **Complejidad de implementación (menor es mejor)** | 0 | -1 | -1 |
| **Escalabilidad y conectividad (IoT)** | 0 | 1 | 1 |
| **Robustez ambiental (campo/intemperie)** | 0 | 1 | 1 |
| **Suma Neta** | **0** | **+2** 🏆 | **+2** |

---

### 8. 🏆 Evaluación Ponderada Multicriterio (VDI 2225)
*Cálculo final: $\text{Total Ponderado} = \sum (\text{Peso} \times \text{Puntaje})$*

| Criterio | Peso | Concepto A (Base) | Concepto B | Concepto C | Peso × Conc. A | Peso × Conc. B | Peso × Conc. C |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Precisión de detección de gases** | 0.25 | 2 | 5 | 2 | 0.50 | 1.25 | 0.50 |
| **Costo del sistema (BOM)** | 0.20 | 4 | 1 | 3 | 0.80 | 0.20 | 0.60 |
| **Autonomía energética** | 0.15 | 2 | 4 | 3 | 0.30 | 0.60 | 0.45 |
| **Complejidad de implementación** | 0.20 | 5 | 2 | 3 | 1.00 | 0.40 | 0.60 |
| **Escalabilidad y conectividad (IoT)** | 0.10 | 1 | 5 | 4 | 0.10 | 0.50 | 0.40 |
| **Robustez ambiental (campo)** | 0.10 | 1 | 5 | 3 | 0.10 | 0.50 | 0.30 |
| **TOTAL PONDERADO** | **1.00** | — | — | — | **2.80** | **3.45** 🥇 | **2.85** |

> 📌 **Decisión Final:** El **Concepto B (Solución 2 - Equilibrada)** resulta ganador con un puntaje de **3.45 / 5.00**, destacando principalmente por su alta precisión en gases, conectividad IoT (MQTT) y robustez ambiental para trabajo de campo.