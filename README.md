# Planta Proceso Pulpas - Sistema de Control Industrial

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![TIA Portal](https://img.shields.io/badge/TIA%20Portal-Compatible-blue.svg)](https://siemens.com)
[![SCL](https://img.shields.io/badge/Language-SCL-green.svg)](https://siemens.com)

## 📋 Descripción del Proyecto

Sistema de control automatizado para una planta de procesamiento de pulpas de frutas desarrollado en **Siemens TIA Portal** utilizando **Structured Control Language (SCL)**. El proyecto implementa un proceso completo de llenado, tapado y túnel de encogido con control de calidad integrado.

## 🚀 Características Principales

### Procesos Automatizados
- **Llenado de Envases**: Control preciso de volumen con detección de nivel
- **Tapado Automático**: Sistema de colocación y ajuste de tapas
- **Túnel de Encogido**: Control de temperatura y tiempo de procesamiento
- **Control de Calidad**: Verificación automática en cada etapa

### Funcionalidades Técnicas
- ✅ Monitoreo en tiempo real de todos los procesos
- ✅ Sistema de alarmas y diagnósticos
- ✅ Control de seguridad integrado
- ✅ Interfaz HMI compatible
- ✅ Registro de datos de producción
- ✅ Modo manual y automático

## 🛠️ Tecnologías Utilizadas

- **PLC**: Siemens S7-1500 series
- **Software**: TIA Portal V16/V17/V18
- **Lenguaje**: SCL (Structured Control Language)
- **Comunicación**: PROFINET
- **HMI**: WinCC Advanced/Comfort

## 📁 Estructura del Proyecto

```
Planta_Proceso_Pulpas/
├── README.md                    # Este archivo
├── LICENSE                      # Licencia MIT
├── .gitignore                  # Archivos ignorados por Git
├── src/                        # Código fuente
│   ├── function_blocks/        # Bloques de función
│   │   ├── FB_FillingProcess.scl
│   │   ├── FB_CappingProcess.scl
│   │   └── FB_ShrinkTunnelProcess.scl
│   ├── data_types/            # Tipos de datos definidos
│   │   └── UDT_ProcessData.udt
│   ├── main/                  # Programa principal
│   │   └── Main_OB1.scl
│   └── variables/             # Variables del proyecto
│       └── Variables_PLC_Planta_Proceso_Pulpas.csv
├── docs/                      # Documentación
│   ├── GUIA_IMPORTACION_MANUAL_COMPLETA.md
│   ├── README_PLANTA_PROCESO_PULPAS.md
│   └── VERIFICACION_ARCHIVOS_CREADOS.md
└── examples/                  # Ejemplos de configuración
    └── configuracion_ejemplo.md
```

## 🔧 Instalación y Configuración

### Prerrequisitos
- TIA Portal V16 o superior
- Licencia de SCL
- PLC Siemens S7-1500 series
- Conocimientos básicos de automatización industrial

### Pasos de Instalación

1. **Clonar el repositorio**
   ```bash
   git clone https://github.com/tu-usuario/Planta_Proceso_Pulpas.git
   cd Planta_Proceso_Pulpas
   ```

2. **Abrir TIA Portal**
   - Crear un nuevo proyecto
   - Configurar el hardware (CPU S7-1500)

3. **Importar archivos SCL**
   - Importar los Function Blocks desde `src/function_blocks/`
   - Importar el UDT desde `src/data_types/`
   - Importar el programa principal desde `src/main/`

4. **Configurar variables**
   - Importar las variables desde `src/variables/Variables_PLC_Planta_Proceso_Pulpas.csv`

5. **Compilar y descargar**
   - Compilar el proyecto completo
   - Descargar al PLC

### Guía Detallada
Para instrucciones paso a paso, consulta: [`docs/GUIA_IMPORTACION_MANUAL_COMPLETA.md`](docs/GUIA_IMPORTACION_MANUAL_COMPLETA.md)

## 📊 Funcionalidades del Sistema

### FB_FillingProcess
- Control de bombas de llenado
- Medición de nivel por ultrasonido
- Control de válvulas de entrada/salida
- Detección de envases

### FB_CappingProcess  
- Posicionamiento de tapas
- Control de torque de apriete
- Verificación de colocación correcta
- Rechazo de productos defectuosos

### FB_ShrinkTunnelProcess
- Control de temperatura del túnel
- Temporización del proceso
- Control de velocidad de banda
- Monitoreo de calidad del encogido

## 🔍 Monitoreo y Diagnóstico

El sistema incluye:
- **Alarmas de proceso**: Detección automática de fallos
- **Diagnóstico de equipos**: Estado de sensores y actuadores  
- **Registro de eventos**: Historial de operaciones
- **Métricas de producción**: Contadores y estadísticas

## 🤝 Contribuciones

Las contribuciones son bienvenidas. Para contribuir:

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

### Estándares de Código
- Seguir las convenciones de nomenclatura de Siemens
- Documentar todas las funciones y variables
- Incluir comentarios explicativos en SCL
- Probar todas las funcionalidades antes del commit

## 📄 Licencia

Este proyecto está bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para más detalles.

## 📞 Soporte y Contacto

- **Documentación**: Revisa la carpeta `docs/` para guías detalladas
- **Issues**: Reporta problemas en la sección Issues de GitHub
- **Discusiones**: Usa la sección Discussions para preguntas generales

## 🏷️ Versiones

- **v1.0.0**: Versión inicial con funcionalidades básicas
- **v1.1.0**: Mejoras en control de calidad
- **v1.2.0**: Optimizaciones de rendimiento

---

**Desarrollado con ❤️ para la industria de procesamiento de alimentos**

*Este proyecto es ideal para estudiantes de automatización, ingenieros de control y profesionales de la industria alimentaria.*
