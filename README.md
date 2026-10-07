# Proyecto ETL y Data Warehouse (SSIS & SQL Server)

Repositorio oficial del proyecto académico enfocado en el diseño, desarrollo e implementación de un proceso ETL (Extracción, Transformación y Carga) robusto y la construcción de un modelo multidimensional en esquema estrella utilizando **Microsoft SQL Server**, **Integration Services (SSIS)** y scripts avanzados en **T-SQL**.

---

##  Integrantes
* **Natalia Katterinne Chaparro Cordero**
* **Santiago José Morales Gutiérrez**
* **Semestre:** 7

---

##  Descripción General del Proyecto

El sistema está diseñado para procesar 1000 registros transaccionales en bruto provenientes de un archivo en Excel, aplicando rigurosas reglas de calidad de datos, limpieza, validación de formatos, control de nulos y manejo de duplicados. La arquitectura se divide en dos grandes procesos:

1. **Proceso A (ETL y Limpieza):** 
   * Extracción inicial de la data cruda hacia un área de *Staging*.
   * Implementación de un **cursor en T-SQL (`cur_personas`)** para el recorrido y validación fila por fila.
   * Automatización mediante paquetes SSIS utilizando componentes de limpieza (`Derived Column`, `Data Conversion`, `Conditional Split`) para separar los registros válidos de aquellos enviados a una tabla de trazabilidad de errores (`Rejected_Personas`).

2. **Proceso B (Modelo Multidimensional / Data Warehouse):**
   * Creación de un esquema estrella estructurado con una tabla de hechos central (`Fact_Encuestas_DW`) y cinco dimensiones operativas (`Dim_Tiempo`, `Dim_Ubicacion`, `Dim_Educacion`, `Dim_Laboral` y `Dim_Persona`).
   * Carga masiva automatizada en SSIS mediante una cascada de componentes de búsqueda (*Lookup*) configurados en caché completa (*Full cache*) para inyectar llaves subrogadas y garantizar la integridad referencial sin redundancias.

---

##  Tecnologías y Herramientas Utilizadas
* **Base de Datos:** Microsoft SQL Server / T-SQL (Stored Procedures, Triggers, Cursores).
* **ETL & Integración:** SQL Server Integration Services (SSIS) en Visual Studio.
* **Control de Versiones:** Git & GitHub.
* **Explotación Analítica:** Consultas SQL avanzadas con funciones de agregación (`AVG`, `COUNT`, `SUM`), agrupamientos y uniones (`JOIN`).

---

##  Estructura del Repositorio

```text
├── Scripts_SQL/
│   ├── ETL.sql                # Script de creación de staging, tablas relacionales y cursor cur_personas
│   ├── ETL2.sql               # Script complementario de transformaciones y validaciones
│   ├── PERSONASDW1.sql        # Scripts de creación del esquema estrella y dimensiones
│   └── 4consultas.sql         # Consultas analíticas y de explotación del Data Warehouse
├── SSIS_Projects/             # Paquetes y configuración de Integration Services (.dtsx)
└── README.md                  # Documentación del repositorio
