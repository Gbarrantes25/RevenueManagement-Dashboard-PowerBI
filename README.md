# 📊 Revenue Management Dashboard

[![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![Excel](https://img.shields.io/badge/Excel-217346?style=flat&logo=microsoft-excel&logoColor=white)](https://www.microsoft.com/en-us/microsoft-365/excel)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Version](https://img.shields.io/badge/Version-1.0-blue.svg)]()

---

## 📋 Tabla de Contenidos

- [Descripción General](#-descripción-general)
- [Características Principales](#-características-principales)
- [Contenido del Proyecto](#-contenido-del-proyecto)
- [Herramientas y Tecnologías](#️-herramientas-y-tecnologías-utilizadas)
- [Configuración del Entorno](#️-configuración-del-entorno)
- [Estructura del Repositorio](#-estructura-del-repositorio)
- [Vistas Previas](#️-vistas-previas-del-proyecto)
- [Autor](#-autor)
- [Licencia](#-licencia)

---

## 📃 Descripción General

Dashboard de **Revenue Management** para Hotelería desarrollado en Power BI, diseñado para analizar y optimizar el rendimiento de ingresos de una cadena hotelera multinacional. Este proyecto transforma datos de reservaciones en métricas estratégicas del sector hotelero mediante:

- 📊 **2 Vistas Analíticas:** Regions (vista por país) y Hotel Branches (vista por sucursal)
- 🏨 **+10 Medidas DAX:** KPIs hoteleros especializados (RevPAR, ADR, Occupancy %, Total Revenue)
- 📈 **Formato Inteligente:** Medidas formateadas automáticamente (B, M, K) para grandes volúmenes
- 🎯 **Análisis de Ingresos:** Revenue por habitación, alimentos y bebidas (A&B)
- 🖱️ **Navegación Interactiva:** Segmentación por país, hotel y período de tiempo

---

## ✨ Características Principales

### 🔄 Transformaciones en Power Query
- Procesos de limpieza y modelado de datos para optimizar el rendimiento
- Transformación de datos desde archivo Excel
- Preparación de tablas de Reservaciones, Habitaciones y Calendario

### 📐 Modelo de Datos
- **Tablas de Dimensión:** Calendario, Habitaciones
- **Tabla de Hechos:** Reservaciones con información detallada de bookings
- Relaciones optimizadas para análisis de revenue management

### 🎨 Diseño Interactivo
- Navegación por páginas con paginado intuitivo
- Segmentación de datos dinámica por país y hotel
- Tarjetas KPI con formato inteligente (B, M, K)
- Visualizaciones profesionales con fondo personalizado

---

## 📊 Contenido del Proyecto

| Página | Descripción | Contenido Principal |
|--------|-------------|---------------------|
| **Regions** | Vista general por país | KPIs globales, revenue por región, análisis comparativo |
| **Hotel Branches** | Vista por sucursal | Detalle por hotel, RevPAR, ADR, Occupancy % |

---

## 🛠️ Herramientas y Tecnologías Utilizadas

### Software Requerido
- **Power BI Desktop** (versión más reciente)

### Fuente de Datos
- 📄 **Reservaciones.xlsx** - Archivo Excel con datos de reservaciones hoteleras

### Lenguajes y Tecnologías
- **DAX** - Cálculo de medidas y KPIs (+10 fórmulas especializadas)
- **Power Query (Lenguaje M)** - Transformación y limpieza de datos

---

## ⚙️ Configuración del Entorno

### Prerequisitos
1. Descargar e instalar [Power BI Desktop](https://powerbi.microsoft.com/desktop/)

### Paso 1: Descargar el Proyecto
1. Clonar o descargar el repositorio desde GitHub
2. Localizar el archivo `Revenue.pbix`

### Paso 2: Abrir en Power BI
1. Abrir el archivo `Revenue.pbix` con Power BI Desktop
2. Ir a la pestaña **Inicio**
3. Hacer clic en **"Actualizar"** para cargar todos los datos

### Paso 3: Explorar el Dashboard
1. Navegar entre las páginas **Regions** y **Hotel Branches**
2. Utilizar las segmentaciones de datos para filtrar por país, hotel y período
3. Analizar los KPIs principales: RevPAR, ADR, Occupancy % y Revenue

---

## 📂 Estructura del Repositorio
```
.
├── Dashboard (box azul).svg   # Archivo de fondo del lienzo del proyecto
├── Revenue.Report/            # Componentes del reporte (formato .pbip)
├── Revenue.SemanticModel/     # Modelo semántico
├── Revenue.pbip               # Proyecto Power BI (formato nuevo)
├── Revenue.pbix               # Archivo ejecutable de Power BI
├── Demo.gif                   # Demostración animada del proyecto
├── .gitignore                 # Archivo de configuración Git
└── README.md                  # Este archivo
```
---
## 🧮 Medidas DAX Implementadas

#### 📊 KPIs Principales (Métricas Hoteleras)

<details>
<summary>Ver KPIs de Revenue Management</summary>


**%Occ** - Occupancy Percentage (Porcentaje de Ocupación)
```dax
=DIVIDE([Total RNs],[RNs Disponibles],0)
```

**Conteo Días** - Conteo de días en el período
```dax
=COUNT(Calendario[Date])
```

**RNs Disponibles** - Room Nights Disponibles
```dax
=SUMX(Habitaciones,Habitaciones[Cantidad de Habitaciones]*[Conteo Días])
```

**ADR** - Average Daily Rate (Tarifa Promedio Diaria)
```dax
=DIVIDE([Total Revenue],[Total RNs],0)
```

**Total Revenue** - Ingresos Totales por Habitaciones
```dax
=SUMX(Reservaciones,Reservaciones[RN]*Reservaciones[Precio Unitario])
```

**Total RNs** - Total Room Nights (Noches de Habitación)
```dax
=SUM(Reservaciones[RN])
```

**RevPar** - Revenue Per Available Room (Ingreso por Habitación Disponible)

```dax
=[ADR]*[%Occ]
```

**Total A&B** - Total Alimentos y Bebidas

```dax
=SUM(Reservaciones[A&B])
```

</details>

#### 🎨 Medidas Formateadas (Formato Inteligente)
<details>
<summary>Ver medidas con formato B, M, K</summary>

ADR*** - ADR con formato inteligente

```dax
VAR T = ABS([ADR])
RETURN
SWITCH(TRUE(),
T >= 1000000000, FORMAT(T, "$#,,,.00 B"),
T >= 1000000, FORMAT(T, "$#,,.00 M"),
T >= 1000, FORMAT(T, "$#,.00 K"),
SUBSTITUTE(FORMAT(T, "$#.00"),",","."))
```

RNs*** - Room Nights con formato inteligente

```dax
VAR T = [Total RNs]
RETURN
SWITCH(TRUE(),
T >= 1000000000, FORMAT(T, "#,,,.00 B"),
T >= 1000000, FORMAT(T, "#,,.00 M"),
T >= 1000, FORMAT(T, "#,.00 K"),
FORMAT(T,"0"))
```

Revenue*** - Revenue con formato inteligente

```dax
VAR T = [Total Revenue]
RETURN
SWITCH(TRUE(),
T >= 1000000000, FORMAT(T, "$#,,,.00 B"),
T >= 1000000, FORMAT(T, "$#,,.00 M"),
T >= 1000, FORMAT(T, "$#,.00 K"),
FORMAT(T,"$0.00"))
```

A&B*** - Alimentos y Bebidas con formato inteligente

```dax
VAR T = [Total A&B]
RETURN
SWITCH(TRUE(),
T >= 1000000000, FORMAT(T, "$#,,,.00 B"),
T >= 1000000, FORMAT(T, "$#,,.00 M"),
T >= 1000, FORMAT(T, "$#,.00 K"),
FORMAT(T,"$0"))
```

Estas medidas formatean automáticamente los números grandes usando sufijos:
B = Billones (≥ 1,000,000,000)
M = Millones (≥ 1,000,000)
K = Miles (≥ 1,000)
</details>

---
## 🖼️ Vistas Previas del Proyecto
<details>
<summary>📸 Ver Capturas de Pantalla</summary>
  Página "Regions"
  
  ![Animation1](https://github.com/user-attachments/assets/0d3de5f3-ae65-43e6-abc6-72e97e6a6be9)
  
  Página "Hotel Branches"
  ![Animation2](https://github.com/user-attachments/assets/0d347ecd-a7cb-496e-940e-a18ad0723a01)
  
</details>

<details>
  <summary>Video</summary>
  https://www.youtube.com/watch?v=TMqiaGSsMXk
</details>

---
## 👤 Autor
Giancarlo Barrantes

Business Intelligence Developer | Power BI Specialist


<a href="https://www.linkedin.com/in/gb25"><img width="70" height="20" alt="image" src="https://github.com/user-attachments/assets/e0d69586-c6f9-4f66-9a3d-bc8dfa146463" /></a>
<a href="https://www.instagram.com/gbarrantes25"><img width="70" height="20" alt="image" src="https://github.com/user-attachments/assets/68773029-5e0f-49da-92e9-fb93a223dd09" />
</a>
<a href="https://www.tiktok.com/@gbarrantes25"><img width="65" height="20" alt="image" src="https://github.com/user-attachments/assets/349c87c0-1f3a-4368-8517-64a6012565c0" /></a>
<a href="https://www.youtube.com/@gbarrantes25"><img width="70" height="20" alt="image" src="https://github.com/user-attachments/assets/d9e2cb69-29ec-47fc-93ae-30896a7b533d" />
</a>

---
## 📝 Licencia
Este proyecto está bajo la Licencia MIT - ver el archivo <a href="https://mit-license.org/">LICENSE</a> para más detalles.

---
## ⭐ Agradecimientos
Si este proyecto te resultó útil, considera darle una ⭐ en GitHub y compartirlo con otros profesionales de Business Intelligence.

<div align="center">
   Hecho por <a href="https://gbarrantes25.github.io/">Giancarlo Barrantes</a>
</div>
