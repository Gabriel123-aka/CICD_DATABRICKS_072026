# Arquitectura Medallion para Análisis de Ventas e Inventario en Azure Databricks

> **Proyecto de Ingeniería de Datos** desarrollado con Azure Databricks, Apache Spark, Delta Lake, Unity Catalog, Delta Sharing y Power BI.

---

# 📖 Tabla de contenido

- Descripción
- Objetivo
- Arquitectura de la solución
- Infraestructura en Azure
- Arquitectura Medallion
- Datasets
- Estructura del proyecto
- Flujo ETL
- Notebooks
- Unity Catalog
- Seguridad
- GitHub Actions (CI/CD)
- Delta Sharing
- Dashboard en Power BI
- Tecnologías
- Futuras mejoras
- Autor

---

# 🎯 Descripción

Este proyecto implementa una solución completa de Ingeniería de Datos sobre Azure Databricks para una empresa del sector Retail.

La arquitectura sigue el patrón **Medallion**, utilizando las capas **Bronze**, **Silver** y **Golden** para transformar cinco conjuntos de datos relacionados con clientes, productos, órdenes, detalle de órdenes e inventario.

El objetivo es disponer de información gobernada, consistente y lista para análisis, compartiéndola mediante **Delta Sharing** para ser consumida desde **Power BI**.

---

# 🚀 Objetivos

- Automatizar el proceso ETL.
- Implementar una arquitectura Medallion.
- Centralizar el gobierno de datos con Unity Catalog.
- Compartir datos de forma segura mediante Delta Sharing.
- Automatizar el despliegue mediante GitHub Actions.
- Construir dashboards analíticos en Power BI.

---

# 🏛 Arquitectura

```text
Datasets
   │
   ▼
Azure Data Lake Storage Gen2
   │
   ▼
Bronze
   │
   ▼
Silver
   │
   ▼
Golden
   │
   ▼
Delta Sharing
   │
   ▼
Power BI
```

> Inserta aquí `Arquitectura.png`.

---

# ☁ Infraestructura en Azure

La solución utiliza:

| Servicio | Descripción |
|----------|-------------|
| Azure Databricks | Procesamiento distribuido |
| Azure Data Lake Storage Gen2 | Almacenamiento |
| Unity Catalog | Gobierno de datos |
| Metastore | Administración centralizada |
| Azure Key Vault | Secretos |
| Access Connector | Managed Identity |
| GitHub | Versionado |
| GitHub Actions | CI/CD |
| Power BI | Visualización |

> Inserta aquí las capturas del Resource Group, Storage Account y Contenedores.

---

# 📂 Datasets

Se procesan cinco archivos:

- Clientes
- Productos
- Órdenes
- Detalle de Órdenes
- Inventario

---

# 🥉 Bronze

La capa Bronze realiza la ingesta sin modificar la estructura de los datos.

Notebooks:

- 1_ingest_clientes
- 1_ingest_productos
- 1_ingest_ordenes
- 1_ingest_detalle_ordenes
- 1_ingest_inventario

Funciones:

- Lectura desde ADLS Gen2.
- Conversión a Delta.
- Registro en Unity Catalog.

---

# 🥈 Silver

Transformaciones principales:

- Limpieza.
- Conversión de tipos.
- Validaciones.
- Integración de tablas.
- Estandarización.

Notebooks:

- 2_transform_inventario
- 2_transform_ventas_detalle

---

# 🥇 Golden

Notebook:

- 3_load_resumen_retail

Genera tablas optimizadas para consumo analítico mediante Delta Sharing.

---

# 📁 Estructura del proyecto

```text
.github/
dashboard/
datasets/
delta_sharing/
evidencias/
prepAmb/
proceso/
reversion/
seguridad/
README.md
```

---

# ⚙ Preparación del ambiente

El notebook `0_preparacion_ambiente` crea y configura:

- Metastore
- Unity Catalog
- Catálogo
- Esquemas
- External Locations
- Storage Credentials
- Tablas Delta

---

# 🔒 Gobierno y Seguridad

El proyecto utiliza Unity Catalog para administrar el acceso a los datos.

Se configuraron grupos:

- DEs
- BI
- CTs

Cada grupo cuenta con permisos específicos sobre catálogos, esquemas, tablas y external locations.

---

# 🔄 CI/CD

El despliegue se automatiza mediante GitHub Actions.

```text
Push a GitHub
      │
      ▼
GitHub Actions
      │
      ▼
Deploy de notebooks
      │
      ▼
Azure Databricks
      │
      ▼
Workflow ETL
```

---

# 🤝 Delta Sharing

La capa Golden se comparte mediante Delta Sharing para que Power BI pueda consultar la información sin duplicar datos.

Beneficios:

- Información actualizada.
- Compartición segura.
- Acceso controlado.
- Eliminación de copias innecesarias.

---

# 📊 Dashboard

El dashboard presenta indicadores como:

- Venta Total
- Ticket Promedio
- Unidades Vendidas
- Ventas por Categoría
- Ventas por Estado
- Productos Bajo Stock
- Riesgo Operativo

> Inserta aquí las capturas del dashboard.

---

# 🛠 Tecnologías

- Azure Databricks
- Apache Spark
- Delta Lake
- Unity Catalog
- Delta Sharing
- Azure Data Lake Storage Gen2
- Azure Key Vault
- GitHub
- GitHub Actions
- Python
- SQL
- Power BI

---

# 📈 Futuras mejoras

- Auto Loader
- Delta Live Tables
- Streaming
- Machine Learning
- Alertas automáticas
- Monitoreo de calidad de datos

---

# 👨‍💻 Autor

**Gabriel Salvador San Martín Jiménez**

Data Engineering | Azure Databricks | Azure | Delta Lake | Power BI

GitHub: https://github.com/Gabriel123-aka/CICD_DATABRICKS_072026

LinkedIn: www.linkedin.com/in/gabriel-salvador-san-martin-jimenez-268a28284

---

# 📄 Licencia

Proyecto desarrollado con fines académicos para demostrar la implementación de una solución de Ingeniería de Datos utilizando Azure Databricks, Arquitectura Medallion, Unity Catalog, Delta Lake y Delta Sharing.