# 📖 EJEMPLOS DE CONFIGURACIÓN
## Planta Proceso Pulpas - Configuraciones Típicas

### 🎯 PROPÓSITO
Este documento proporciona ejemplos prácticos de configuración para diferentes tipos de productos y escenarios de operación en la planta de procesamiento de pulpas.

---

## 🍎 CONFIGURACIONES POR TIPO DE PRODUCTO

### Producto Tipo 1: Pulpa de Mango Premium
```
// Configuración de Receta
RECIPE_Product_Type := 1;
RECIPE_Volume_SP := 500.0;        // 500 ml
RECIPE_Torque_SP := 2.5;          // 2.5 Nm
RECIPE_Temp_SP := 180.0;          // 180°C
RECIPE_Time_SP := T#45s;          // 45 segundos
RECIPE_Speed_SP := 2.0;           // 2.0 m/min
RECIPE_Quality_Tolerance := 2.0;   // ±2%

// Parámetros Específicos
- Viscosidad: Alta
- Temperatura de llenado: 85°C
- Presión de tapado: Media
- Tiempo de encogido: Estándar
```

### Producto Tipo 2: Pulpa de Guayaba Natural
```
// Configuración de Receta
RECIPE_Product_Type := 2;
RECIPE_Volume_SP := 250.0;        // 250 ml
RECIPE_Torque_SP := 2.0;          // 2.0 Nm
RECIPE_Temp_SP := 175.0;          // 175°C
RECIPE_Time_SP := T#40s;          // 40 segundos
RECIPE_Speed_SP := 2.5;           // 2.5 m/min
RECIPE_Quality_Tolerance := 3.0;   // ±3%

// Parámetros Específicos
- Viscosidad: Media
- Temperatura de llenado: 80°C
- Presión de tapado: Baja
- Tiempo de encogido: Reducido
```

### Producto Tipo 3: Pulpa de Maracuyá Concentrada
```
// Configuración de Receta
RECIPE_Product_Type := 3;
RECIPE_Volume_SP := 200.0;        // 200 ml
RECIPE_Torque_SP := 3.0;          // 3.0 Nm
RECIPE_Temp_SP := 185.0;          // 185°C
RECIPE_Time_SP := T#50s;          // 50 segundos
RECIPE_Speed_SP := 1.8;           // 1.8 m/min
RECIPE_Quality_Tolerance := 1.5;   // ±1.5%

// Parámetros Específicos
- Viscosidad: Muy Alta
- Temperatura de llenado: 90°C
- Presión de tapado: Alta
- Tiempo de encogido: Extendido
```

---

## ⚙️ CONFIGURACIÓN DE HARDWARE

### Configuración de CPU S7-1515-2 PN
```
// Configuración de Red
IP_Address := '192.168.1.10';
Subnet_Mask := '255.255.255.0';
Gateway := '192.168.1.1';

// Configuración de Ciclo
Cycle_Time := T#10ms;           // Tiempo de ciclo OB1
Watchdog_Time := T#500ms;       // Tiempo de vigilancia

// Configuración de Memoria
Work_Memory := 1024;            // 1MB memoria de trabajo
Load_Memory := 8192;            // 8MB memoria de carga
```

### Configuración de Módulos de E/S

#### Módulo de Entradas Digitales (DI 16x24VDC)
```
Slot: 1
Address: %I0.0 - %I1.7

// Asignación de Entradas
%I0.0 := I_Container_Filling;      // Sensor envase llenado
%I0.1 := I_Container_Capping;      // Sensor envase tapado
%I0.2 := I_Container_Tunnel;       // Sensor envase túnel
%I0.3 := I_Cap_Present;            // Sensor presencia tapa
%I0.4 := I_Emergency_Stop;         // Parada de emergencia
%I0.5 := I_Door_Safety;            // Puerta de seguridad
%I0.6 := I_Light_Curtain;          // Cortina de luz
%I0.7 := I_Air_Pressure_OK;        // Presión de aire OK
```

#### Módulo de Entradas Analógicas (AI 8xU/I/RTD/TC)
```
Slot: 2
Address: %IW10 - %IW24

// Configuración de Canales
Canal 0 (%IW10): Sensor de Nivel
  - Tipo: 4-20mA
  - Rango: 0-100%
  - Filtro: 50Hz

Canal 1 (%IW12): Sensor de Flujo
  - Tipo: 4-20mA
  - Rango: 0-50 L/min
  - Filtro: 60Hz

Canal 2 (%IW14): Sensor de Torque
  - Tipo: 0-10V
  - Rango: 0-10 Nm
  - Filtro: Ninguno

Canal 3 (%IW16): Sensor de Posición
  - Tipo: 4-20mA
  - Rango: 0-100 mm
  - Filtro: 50Hz

Canal 4 (%IW20): Temperatura Zona 1
  - Tipo: RTD Pt100
  - Rango: 0-300°C
  - Compensación: Interna

Canal 5 (%IW22): Temperatura Zona 2
  - Tipo: RTD Pt100
  - Rango: 0-300°C
  - Compensación: Interna

Canal 6 (%IW24): Temperatura Zona 3
  - Tipo: RTD Pt100
  - Rango: 0-300°C
  - Compensación: Interna
```

#### Módulo de Salidas Digitales (DQ 16x24VDC)
```
Slot: 3
Address: %Q0.0 - %Q1.7

// Asignación de Salidas
%Q0.0 := Q_Filling_Valve;         // Válvula de llenado
%Q0.1 := Q_Cap_Feeder;            // Alimentador de tapas
%Q0.2 := Q_Capping_Motor;         // Motor de tapado
%Q0.3 := Q_Conveyor_Filling;      // Banda llenado
%Q0.4 := Q_Conveyor_Capping;      // Banda tapado
%Q0.5 := Q_Conveyor_Tunnel;       // Banda túnel
%Q0.6 := Q_Heater_Zone1;          // Calentador zona 1
%Q0.7 := Q_Heater_Zone2;          // Calentador zona 2
%Q1.0 := Q_Heater_Zone3;          // Calentador zona 3
%Q1.1 := Q_Tunnel_Fan;            // Ventilador túnel
%Q1.2 := Q_Process_Active;        // Indicador proceso activo
%Q1.3 := Q_System_Ready;          // Indicador sistema listo
%Q1.4 := Q_Alarm_General;         // Alarma general
```

---

## 🔧 CONFIGURACIÓN DE PARÁMETROS DE PROCESO

### Parámetros de Llenado
```
// Configuración Estándar
SetVolume_Default := 500.0;       // Volumen por defecto (ml)
FlowRate_Max := 30.0;             // Flujo máximo (L/min)
FlowRate_Min := 5.0;              // Flujo mínimo (L/min)
Level_Max := 95.0;                // Nivel máximo seguro (%)
Timeout_Filling := T#30s;         // Timeout de llenado

// Configuración por Producto
CASE ProductType OF
    1: // Mango Premium
        SetVolume := 500.0;
        FlowRate_Target := 20.0;

    2: // Guayaba Natural
        SetVolume := 250.0;
        FlowRate_Target := 25.0;

    3: // Maracuyá Concentrada
        SetVolume := 200.0;
        FlowRate_Target := 15.0;
END_CASE;
```

### Parámetros de Tapado
```
// Configuración Estándar
Torque_Max := 5.0;                // Torque máximo (Nm)
Torque_Min := 1.0;                // Torque mínimo (Nm)
Position_Contact := 5.0;          // Posición de contacto (mm)
Retry_Max := 3;                   // Máximo reintentos
Timeout_Capping := T#10s;         // Timeout de tapado

// Configuración por Producto
CASE ProductType OF
    1: // Mango Premium
        SetTorque := 2.5;
        Tolerance := 0.2;

    2: // Guayaba Natural
        SetTorque := 2.0;
        Tolerance := 0.3;

    3: // Maracuyá Concentrada
        SetTorque := 3.0;
        Tolerance := 0.15;
END_CASE;
```

### Parámetros de Túnel de Encogido
```
// Configuración Estándar
Temp_Max := 250.0;                // Temperatura máxima (°C)
Temp_Min := 150.0;                // Temperatura mínima (°C)
PreHeat_Time := T#5m;             // Tiempo precalentamiento
Process_Time_Max := T#2m;         // Tiempo máximo proceso
Timeout_PreHeat := T#10m;         // Timeout precalentamiento

// Configuración por Producto
CASE ProductType OF
    1: // Mango Premium
        SetTemperature := 180.0;
        ProcessTime := T#45s;
        ConveyorSpeed := 2.0;

    2: // Guayaba Natural
        SetTemperature := 175.0;
        ProcessTime := T#40s;
        ConveyorSpeed := 2.5;

    3: // Maracuyá Concentrada
        SetTemperature := 185.0;
        ProcessTime := T#50s;
        ConveyorSpeed := 1.8;
END_CASE;
```

---

## 🖥️ CONFIGURACIÓN DE HMI

### Pantalla Principal - Configuración
```
// Elementos de Visualización
- Estado del Sistema: Indicador LED
- Modo de Operación: Selector (Auto/Manual)
- Contador de Producción: Display numérico
- Eficiencia: Barra de progreso
- Alarmas Activas: Lista dinámica

// Elementos de Control
- Botón Start/Stop: Control general
- Selector de Producto: Dropdown (1-10)
- Parada de Emergencia: Botón rojo grande
```

### Pantalla de Proceso - Configuración
```
// Estación de Llenado
- Volumen Actual: Display con unidades (ml)
- Flujo Actual: Display con unidades (L/min)
- Nivel: Barra de progreso (0-100%)
- Estado: Indicador de texto

// Estación de Tapado
- Torque Actual: Display con unidades (Nm)
- Posición: Display con unidades (mm)
- Calidad: Indicador OK/NOK
- Reintentos: Contador

// Túnel de Encogido
- Temperaturas: 3 displays (Zona 1, 2, 3)
- Tiempo Proceso: Display con formato mm:ss
- Velocidad Banda: Display con unidades (m/min)
- Estado Precalentamiento: Indicador
```

### Pantalla de Recetas - Configuración
```
// Campos Editables
- Tipo de Producto: Selector numérico (1-10)
- Volumen Objetivo: Campo numérico (50-1000 ml)
- Torque Objetivo: Campo numérico (1.0-5.0 Nm)
- Temperatura: Campo numérico (150-250°C)
- Tiempo Proceso: Campo tiempo (10s-2m)
- Velocidad Banda: Campo numérico (0.5-5.0 m/min)
- Tolerancia Calidad: Campo numérico (0.5-5.0%)

// Botones de Control
- Cargar Receta: Botón de acción
- Guardar Receta: Botón de acción
- Receta por Defecto: Botón de acción
```

---

## 🔍 CONFIGURACIÓN DE DIAGNÓSTICO

### Configuración de Alarmas
```
// Niveles de Alarma
Level_1_Critical := TRUE;         // Parada inmediata
Level_2_Important := TRUE;        // Afecta calidad
Level_3_Info := FALSE;            // Solo información

// Configuración de Registro
Alarm_Buffer_Size := 100;         // Tamaño buffer alarmas
Alarm_Archive := TRUE;            // Archivar alarmas
Alarm_Print := FALSE;             // Imprimir alarmas

// Códigos de Alarma Personalizados
User_Alarm_1000 := "Falla sistema llenado";
User_Alarm_2000 := "Falla sistema tapado";
User_Alarm_3000 := "Falla sistema túnel";
```

### Configuración de Tendencias
```
// Variables a Registrar
Trend_Volume := TRUE;             // Volumen de llenado
Trend_Torque := TRUE;             // Torque de tapado
Trend_Temperature := TRUE;        // Temperaturas túnel
Trend_Efficiency := TRUE;         // Eficiencia proceso

// Configuración de Muestreo
Sample_Rate := T#1s;              // Frecuencia muestreo
Buffer_Size := 3600;              // 1 hora de datos
Archive_Enable := TRUE;           // Archivar datos
```

---

## 🛠️ CONFIGURACIÓN DE MANTENIMIENTO

### Configuración de Contadores
```
// Contadores de Operación
Counter_Filling_Cycles := 0;      // Ciclos de llenado
Counter_Capping_Cycles := 0;      // Ciclos de tapado
Counter_Tunnel_Cycles := 0;       // Ciclos de túnel
Counter_Total_Production := 0;    // Producción total

// Límites de Mantenimiento
Maint_Filling_Limit := 10000;     // Ciclos para mantenimiento
Maint_Capping_Limit := 8000;      // Ciclos para mantenimiento
Maint_Tunnel_Limit := 5000;       // Ciclos para mantenimiento

// Configuración de Alertas
Maint_Warning_Percent := 80;      // Alerta al 80% del límite
Maint_Critical_Percent := 95;     // Crítico al 95% del límite
```

### Configuración de Horas de Operación
```
// Contadores de Tiempo
Operating_Hours_Total := T#0s;    // Horas totales
Operating_Hours_Filling := T#0s;  // Horas llenado
Operating_Hours_Capping := T#0s;  // Horas tapado
Operating_Hours_Tunnel := T#0s;   // Horas túnel

// Intervalos de Mantenimiento
Maint_Interval_Daily := T#24h;    // Mantenimiento diario
Maint_Interval_Weekly := T#168h;  // Mantenimiento semanal
Maint_Interval_Monthly := T#720h; // Mantenimiento mensual
```

---

## 🔒 CONFIGURACIÓN DE SEGURIDAD

### Configuración de Usuarios
```
// Niveles de Acceso
Level_Operator := 1;              // Operador básico
Level_Supervisor := 2;            // Supervisor
Level_Engineer := 3;              // Ingeniero
Level_Administrator := 4;         // Administrador

// Permisos por Nivel
Operator_Rights := [View_Process, Start_Stop];
Supervisor_Rights := [View_Process, Start_Stop, Change_Recipe];
Engineer_Rights := [All_Operations, Diagnostics];
Admin_Rights := [Full_Access];
```

### Configuración de Backup
```
// Configuración de Respaldo
Backup_Enable := TRUE;            // Habilitar backup
Backup_Interval := T#24h;         // Intervalo de backup
Backup_Location := "\Server\Backup\";
Backup_Retention := 30;           // Días de retención

// Elementos a Respaldar
Backup_Recipes := TRUE;           // Respaldar recetas
Backup_Alarms := TRUE;            // Respaldar alarmas
Backup_Trends := TRUE;            // Respaldar tendencias
Backup_Config := TRUE;            // Respaldar configuración
```

---

## 📊 CONFIGURACIÓN DE REPORTES

### Configuración de Reportes de Producción
```
// Frecuencia de Reportes
Report_Hourly := TRUE;            // Reporte cada hora
Report_Daily := TRUE;             // Reporte diario
Report_Weekly := TRUE;            // Reporte semanal
Report_Monthly := FALSE;          // Reporte mensual

// Contenido de Reportes
Report_Production_Count := TRUE;   // Contador producción
Report_Efficiency := TRUE;        // Eficiencia
Report_Alarms := TRUE;            // Resumen alarmas
Report_Quality := TRUE;           // Datos de calidad
```

### Configuración de Exportación
```
// Formato de Exportación
Export_Format := "CSV";           // Formato CSV
Export_Separator := ",";          // Separador coma
Export_Encoding := "UTF-8";       // Codificación UTF-8

// Destino de Exportación
Export_Path := "\Server\Reports\";
Export_Filename_Pattern := "Report_YYYYMMDD_HHMMSS.csv";
```

---

## 🧪 CONFIGURACIÓN DE PRUEBAS

### Configuración de Modo de Prueba
```
// Parámetros de Prueba
Test_Mode_Enable := FALSE;        // Modo prueba deshabilitado
Test_Cycle_Time := T#5s;          // Ciclo rápido para pruebas
Test_Skip_Delays := TRUE;         // Saltar delays en pruebas
Test_Simulate_Sensors := FALSE;   // Simular sensores

// Valores de Simulación
Sim_Container_Present := TRUE;    // Simular envase presente
Sim_Level_Value := 50.0;          // Valor simulado nivel
Sim_Flow_Value := 20.0;           // Valor simulado flujo
Sim_Torque_Value := 2.5;          // Valor simulado torque
Sim_Temp_Values := [180.0, 180.0, 180.0]; // Temperaturas simuladas
```

---

## 📞 SOPORTE DE CONFIGURACIÓN

### Información de Contacto
- **Equipo de Configuración**: config@plantapulpas.com
- **Soporte Técnico**: soporte@plantapulpas.com
- **Documentación**: docs@plantapulpas.com

### Recursos Adicionales
- Manual de configuración avanzada
- Videos tutoriales de configuración
- Base de conocimientos online
- Foro de usuarios

---

**📖 Fin de ejemplos de configuración**

*Estos ejemplos deben adaptarse según las necesidades específicas de cada instalación*
