## 💻 Pseudocódigo de Control del Firmware

```pascal
ALGORITMO Monitoreo_Cultivo_GreenPlant

INICIO
    // ===================================================
    // 1. CONFIGURACIÓN E INICIALIZACIÓN DE HARDWARE
    // ===================================================
    Configurar ESP32-S3
    Configurar sensor ZE03-NH3
    Configurar sensor SCD30
    Configurar sensor BME280
    Configurar sensor de humedad y temperatura del suelo

    // ===================================================
    // 2. CONFIGURACIÓN DE RED Y ALMACENAMIENTO
    // ===================================================
    Configurar comunicación Wi-Fi + MQTT
    Configurar almacenamiento de datos

    // Conectar a la infraestructura de red
    Conectar el sistema a Wi-Fi

    // ===================================================
    // 3. CICLO PRINCIPAL DE OPERACIÓN (LOOP)
    // ===================================================
    MIENTRAS el sistema esté encendido HACER

        // --- Adquisición de Variables ---
        Leer concentración de NH3
        Leer concentración de CO2
        Leer temperatura ambiental
        Leer humedad ambiental
        Leer temperatura del suelo
        Leer humedad del suelo

        // --- Despliegue de Datos ---
        Mostrar los valores obtenidos

        // --- Evaluación de Umbrales y Alertas ---
        SI (¿Los valores superan los umbrales establecidos?) ENTONCES
            Generar alerta
            Registrar los datos
            Enviar datos mediante MQTT
        SINO
            Registrar los datos
            Enviar datos mediante MQTT
        FIN SI

        // --- Persistencia Histórica ---
        Actualizar el almacenamiento histórico

    FIN MIENTRAS

FIN