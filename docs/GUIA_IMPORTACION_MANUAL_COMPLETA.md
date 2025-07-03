# 📋 GUÍA DE IMPORTACIÓN MANUAL COMPLETA
## Planta Proceso Pulpas - TIA Portal

### 🎯 OBJETIVO
Esta guía proporciona instrucciones detalladas paso a paso para importar manualmente todos los archivos del proyecto "Planta Proceso Pulpas" en TIA Portal.

---

## 📋 PRERREQUISITOS

### Software Requerido
- **TIA Portal V16, V17 o V18** (con licencia SCL)
- **Windows 10/11** (64-bit)
- **Mínimo 8GB RAM** recomendado
- **5GB espacio libre** en disco

### Hardware Compatible
- **CPU S7-1500 series** (1511, 1512, 1513, 1515, 1516, 1518)
- **Módulos de E/S** según configuración
- **HMI** (opcional): KTP700, KTP1200, TP1500

---

## 🚀 PASO 1: CREAR NUEVO PROYECTO

### 1.1 Iniciar TIA Portal
1. Abrir **TIA Portal**
2. Seleccionar **"Crear nuevo proyecto"**
3. Configurar:
   - **Nombre**: `Planta_Proceso_Pulpas`
   - **Ruta**: Seleccionar carpeta de trabajo
   - **Autor**: Tu nombre
   - **Comentario**: `Sistema de control para planta de procesamiento de pulpas`

### 1.2 Configurar Hardware
1. En **Vista del proyecto**, expandir **"Dispositivos y redes"**
2. Hacer clic en **"Agregar dispositivo"**
3. Seleccionar:
   - **Controlador PLC**: `SIMATIC S7-1500`
   - **CPU**: `CPU 1515-2 PN` (o similar)
   - **Versión de firmware**: Más reciente disponible
4. Hacer clic en **"Agregar"**

### 1.3 Configurar CPU
1. Seleccionar la **CPU** en la vista de dispositivos
2. En **"Propiedades"** configurar:
   - **Nombre**: `PLC_Planta_Pulpas`
   - **Dirección IP**: `192.168.1.10` (ajustar según red)
   - **Máscara de subred**: `255.255.255.0`

---

## 🔧 PASO 2: IMPORTAR TIPOS DE DATOS (UDT)

### 2.1 Crear UDT_ProcessData
1. En **Árbol del proyecto**, expandir **"Tipos de datos PLC"**
2. Hacer clic derecho en **"Tipos de datos definidos por el usuario"**
3. Seleccionar **"Agregar nuevo tipo de datos"**
4. Configurar:
   - **Nombre**: `UDT_ProcessData`
   - **Tipo**: `Estructura`
5. Hacer clic en **"Agregar"**

### 2.2 Importar estructura UDT
1. Abrir el archivo **`UDT_ProcessData.udt`**
2. **Copiar todo el contenido**
3. En TIA Portal, hacer clic derecho en **`UDT_ProcessData`**
4. Seleccionar **"Abrir"**
5. Cambiar a **vista de código** (SCL)
6. **Pegar el contenido** copiado
7. **Compilar** (Ctrl+Shift+F7)

---

## 📦 PASO 3: IMPORTAR BLOQUES DE FUNCIÓN

### 3.1 Importar FB_FillingProcess
1. En **Árbol del proyecto**, expandir **"Bloques de programa"**
2. Hacer clic derecho en **"Bloques de función"**
3. Seleccionar **"Agregar nuevo bloque"**
4. Configurar:
   - **Nombre**: `FB_FillingProcess`
   - **Tipo**: `Bloque de función (FB)`
   - **Lenguaje**: `SCL`
   - **Numeración**: `Automática`
5. Hacer clic en **"Aceptar"**

### 3.2 Importar código SCL
1. Abrir el archivo **`FB_FillingProcess.scl`**
2. **Copiar todo el contenido**
3. En TIA Portal, abrir **`FB_FillingProcess`**
4. **Pegar el contenido** en el editor SCL
5. **Compilar** el bloque

### 3.3 Repetir para otros FB
Repetir los pasos 3.1 y 3.2 para:
- **`FB_CappingProcess`** (usar archivo `FB_CappingProcess.scl`)
- **`FB_ShrinkTunnelProcess`** (usar archivo `FB_ShrinkTunnelProcess.scl`)

---

## 🏠 PASO 4: IMPORTAR PROGRAMA PRINCIPAL

### 4.1 Configurar OB1
1. En **Árbol del proyecto**, expandir **"Bloques de programa"**
2. Hacer doble clic en **"Main [OB1]"**
3. Cambiar lenguaje a **SCL** si es necesario

### 4.2 Importar código principal
1. Abrir el archivo **`Main_OB1.scl`**
2. **Copiar todo el contenido**
3. En TIA Portal, en el editor de **OB1**
4. **Pegar el contenido**
5. **Compilar** el programa

---

## 📊 PASO 5: CREAR VARIABLES

### 5.1 Crear variable ProcessData
1. En **Árbol del proyecto**, expandir **"Variables PLC"**
2. Hacer doble clic en **"Variables por defecto"**
3. Agregar nueva variable:
   - **Nombre**: `ProcessData`
   - **Tipo de datos**: `UDT_ProcessData`
   - **Dirección**: Dejar automática
   - **Comentario**: `Estructura principal de datos del proceso`

### 5.2 Importar variables desde CSV
1. En **Variables PLC**, hacer clic derecho
2. Seleccionar **"Importar..."**
3. Navegar al archivo **`Variables_PLC_Planta_Proceso_Pulpas.csv`**
4. Configurar opciones de importación:
   - **Separador**: Coma
   - **Primera fila contiene encabezados**: ✓
5. Hacer clic en **"Importar"**

### 5.3 Verificar importación
1. Revisar que todas las variables se hayan importado correctamente
2. Verificar direcciones de memoria
3. Corregir cualquier error de importación

---

## 🔧 PASO 6: CREAR INSTANCIAS DE FB

### 6.1 Crear instancias globales
1. En **Variables PLC**, agregar las siguientes variables:

```
Nombre: FB_Filling_Instance
Tipo: FB_FillingProcess
Comentario: Instancia del bloque de llenado

Nombre: FB_Capping_Instance  
Tipo: FB_CappingProcess
Comentario: Instancia del bloque de tapado

Nombre: FB_ShrinkTunnel_Instance
Tipo: FB_ShrinkTunnelProcess
Comentario: Instancia del bloque de túnel
```

---

## ⚙️ PASO 7: CONFIGURAR HARDWARE DE E/S

### 7.1 Agregar módulos de entrada
1. En **Vista de dispositivos**, seleccionar el **rack**
2. Agregar **módulo de entrada digital**:
   - Tipo: `DI 16x24VDC BA`
   - Slot: 1
3. Agregar **módulo de entrada analógica**:
   - Tipo: `AI 8xU/I/RTD/TC ST`
   - Slot: 2

### 7.2 Agregar módulos de salida
1. Agregar **módulo de salida digital**:
   - Tipo: `DQ 16x24VDC/0.5A BA`
   - Slot: 3
2. Agregar **módulo de salida analógica** (opcional):
   - Tipo: `AQ 4xU/I ST`
   - Slot: 4

### 7.3 Asignar direcciones
1. Verificar que las direcciones coincidan con las del CSV
2. Ajustar si es necesario en **"Configuración de dispositivos"**

---

## 🔍 PASO 8: COMPILACIÓN Y VERIFICACIÓN

### 8.1 Compilar proyecto completo
1. En **Árbol del proyecto**, hacer clic derecho en el **PLC**
2. Seleccionar **"Compilar" > "Software (compilación completa)"**
3. Revisar **ventana de información** para errores
4. Corregir errores si los hay

### 8.2 Verificar consistencia
1. Verificar que todos los bloques compilen sin errores
2. Verificar que todas las variables estén definidas
3. Verificar direcciones de E/S

---

## 📡 PASO 9: DESCARGA AL PLC

### 9.1 Establecer conexión
1. Conectar PC al PLC via **Ethernet**
2. En TIA Portal, hacer clic en **"Conexión en línea"**
3. Seleccionar **interfaz de red** correcta
4. Hacer clic en **"Iniciar búsqueda"**
5. Seleccionar el **PLC** encontrado

### 9.2 Descargar proyecto
1. Hacer clic derecho en el **PLC** en árbol del proyecto
2. Seleccionar **"Descargar al dispositivo"**
3. Configurar opciones de descarga:
   - **Sobrescribir todo**: ✓
   - **Iniciar módulos después de descarga**: ✓
4. Hacer clic en **"Descargar"**

### 9.3 Verificar descarga
1. Verificar que el PLC esté en **RUN**
2. Verificar estado de **LEDs** en CPU
3. Probar algunas **entradas/salidas** básicas

---

## 🧪 PASO 10: PRUEBAS INICIALES

### 10.1 Modo manual
1. Activar **modo manual** desde HMI o forzado
2. Probar **actuadores individuales**:
   - Válvula de llenado
   - Motor de banda
   - Calentadores
3. Verificar **respuesta de sensores**

### 10.2 Modo automático
1. Configurar **parámetros de receta**
2. Activar **modo automático**
3. Ejecutar **ciclo de prueba** completo
4. Monitorear **variables de proceso**

### 10.3 Pruebas de alarma
1. Simular **condiciones de alarma**
2. Verificar **respuesta del sistema**
3. Probar **función de reset**

---

## 🔧 PASO 11: CONFIGURACIÓN HMI (OPCIONAL)

### 11.1 Agregar HMI
1. En **Vista del proyecto**, agregar **dispositivo HMI**
2. Seleccionar modelo apropiado
3. Configurar **conexión con PLC**

### 11.2 Crear pantallas básicas
1. **Pantalla principal**: Estado general del sistema
2. **Pantalla de proceso**: Monitoreo en tiempo real
3. **Pantalla de alarmas**: Gestión de alarmas
4. **Pantalla de recetas**: Configuración de parámetros

---

## ✅ VERIFICACIÓN FINAL

### Lista de verificación:
- [ ] Todos los bloques SCL compilados sin errores
- [ ] Variables importadas correctamente
- [ ] Hardware configurado y direcciones asignadas
- [ ] Proyecto descargado al PLC exitosamente
- [ ] PLC en modo RUN
- [ ] Pruebas básicas completadas
- [ ] Documentación actualizada

---

## 🆘 SOLUCIÓN DE PROBLEMAS

### Errores comunes:

**Error de compilación SCL:**
- Verificar sintaxis del código
- Verificar que todos los tipos de datos estén definidos
- Verificar nombres de variables

**Error de importación CSV:**
- Verificar formato del archivo CSV
- Verificar separadores (coma vs punto y coma)
- Verificar codificación del archivo (UTF-8)

**Error de descarga:**
- Verificar conexión de red
- Verificar dirección IP del PLC
- Verificar que el PLC esté en STOP antes de descargar

**Variables no encontradas:**
- Verificar que las variables estén declaradas
- Verificar nombres exactos (case-sensitive)
- Verificar ámbito de las variables (global vs local)

---

## 📞 SOPORTE TÉCNICO

Para soporte adicional:
1. Consultar documentación de TIA Portal
2. Revisar archivos de ejemplo en carpeta `examples/`
3. Verificar logs de compilación
4. Contactar soporte técnico de Siemens si es necesario

---

**✅ ¡Importación completada exitosamente!**

*Tiempo estimado de importación: 2-4 horas (dependiendo de experiencia)*
