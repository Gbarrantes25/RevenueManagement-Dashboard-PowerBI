# Revenue Management Dashboard

## 📃 Descripción General
El dashboard fue diseñado para un análisis básico del personal de la organización.


## 📊 Contenido del proyecto
- Página de resumen: Ofrece una vista consolidada de toda la infortación relevante de los empleados de la organización.
- Página Filtrado "Female": Contiene una vista de información sobre los empleados de género femenino.
- Página Filtrado "Male": Contiene una vista de información sobre los empleados de género masculino.


## 🛠️ Herramientas y Tecnologías Utilizadas
- Visualización: Power BI Desktop.
- Fuente de Datos:
  - [Empleados.csv](https://raw.githubusercontent.com/Gbarrantes25/Employee-Dashboard-PowerBI/refs/heads/main/Fuente%20de%20Datos/Empleados.csv)
  - [Evaluación.csv](https://raw.githubusercontent.com/Gbarrantes25/Employee-Dashboard-PowerBI/refs/heads/main/Fuente%20de%20Datos/Evaluacion.csv)
  - [Sueldos.csv](https://raw.githubusercontent.com/Gbarrantes25/Employee-Dashboard-PowerBI/refs/heads/main/Fuente%20de%20Datos/Sueldos.csv)
 
    
- Lenguajes: DAX para las medidas calculadas y Power Query (Lenguaje M) para la transformación de datos.


## ⚙️ Configuración del Entorno
- Software Necesario: Power BI Desktop.
- Instalación:
  - Descargar [Employee.pbix](https://github.com/Gbarrantes25/Employee-Dashboard-PowerBI/raw/refs/heads/main/Employee.pbix) con Power BI Desktop.
  - Entrar a Inicio y darle click a "Actualizar".


## 📂 Estructura del Repositorio
<code>.
  ├── Fuente de Datos/                  # Contiene los archivos de datos de ejemplo (.CSV)
  ├── Dashboard (Boxy sections 6).svg   # Es el archivo de fondo del lienzo del proyecto.
  ├── Employee.pbix                     # Archivo que será ejecutado con Power BI Desktop.
  └── README.md                         # Este archivo
</code>


## ✅ Características Principales
- Transformaciones en Power Query: Se realizaron procesos de limpieza y modelado de datos para optimizar el rendimiento.
- Medidas DAX: Se implementaron cálculos para análisis de empleados y segmentación por género.
  - <code>Promedio Edad = AVERAGE(Empleados[Edad])</code>
  - <code>Promedio Evaluación = AVERAGE(Evaluacion[Evaluación])</code>
  - <code>Promedio Sueldo = AVERAGE(Sueldos[Sueldo])</code>
  - <code>Total Empleados = DISTINCTCOUNT(Empleados[ID])</code>
- Diseño Interactivo: Uso de bookmarks para navegación y filtrado intuitivo entre páginas.


## 🖼️ Vistas Previas del proyecto
<details>
  <summary>Capturas</summary>


  Vista consolidada


  <img width="1862" height="1050" alt="image" src="https://github.com/user-attachments/assets/81920c57-ec5f-4876-943f-a5e1ab567005" />


  Género Femenino


  <img width="1825" height="1046" alt="image" src="https://github.com/user-attachments/assets/6b71785f-57ee-478f-9167-401282d07167" />


  Género masculino por Oficina Administrativa


  <img width="1810" height="1040" alt="image" src="https://github.com/user-attachments/assets/485ea7d6-5a39-42c9-a112-63c63bea30a5" />
</details>


## 👤 Autor
- Giancarlo Barrantes
- Lima, Perú
- [Linkedin](https://www.linkedin.com/in/gb25/)
