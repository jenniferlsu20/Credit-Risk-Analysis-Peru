# Evaluación del Riesgo Crediticio en Bancos Peruanos
Este proyecto aplica técnicas de **aprendizaje no supervisado** para analizar y segmentar clientes de entidades bancarias de Perú según su riesgo crediticio, empleando algoritmos como K-prototypes, Isolation Forest, y FAMD (Factor Analýsis of Mixed Data), para identificar patrones ocultos, perfiles de riesgo y posibles anomalías en los datos, con el objetivo de:

- Mejorar la toma de decisiones en la aprobación de créditos.
- Optimizar la gestión de riesgo financiero.
- Ofrecer recomendaciones basadas en datos reales.

Los resultados del análisis se presentan a través de un **dashboard interactivo en Power BI**, diseñado para comunicar los hallazgos de forma clara, visual y accesible para usuarios técnicos y no técnicos.

## Contenido del Repositorio
- README.md: Este documento explica el desarrollo del proyecto, los hallazgos y como replicarlo.
- riesgo_crediticio.ipynb: Notebook contentivo del análisis exploratorio realizado, modelo de aprendizaje automático no supervisado utilizado, y visualizaciones complementarias.
- credit_risk.pbix: Dashboard interactivo de Power BI.

## Origen de los Datos:
Los datos utilizados en este proyecto se extrajeron de la plataforma **Kaggle**. Se utilizó el conjunto de datos ["Análisis de incumplimiento bancario"](https://www.kaggle.com/datasets/luishcaldernb/morosidad). Este conjunto contiene un conjunto de datos identificado como: data.csv, donde se se procesaron variables clave como `mora`, `atraso`, `ingreso`, `deuda_sf`, `edad`, `score`, `vivienda`, `zona`, y `nivel_educ`. Agradezco a la comunidad de Kaggle y al creador del conjunto de datos por compartir esta información.

## Descripcion del proyecto:
El riesgo crediticio representa un desafío clave para las entidades financieras en Perú, donde la diversidad de perfiles de clientes dificultan la evaluación de su capacidad de pago. Este proyecto tiene como propósito aplicar técnicas de **aprendizaje automático no supervisado** para abordar este problema desde una perspectiva exploratoria y estratégica.  Los objetivos específicos son:

- **Segmentar clientes** en grupos según su nivel de riesgo mediante algoritmos de clustering.
- **Detectar anomalías** que puedan representar riesgos extremos, fraudes o errores.
- **Visualizar los resultados** de forma clara e interactiva para facilitar la toma de decisiones.
- **Proporcionar recomendaciones** para la aprobación o rechazo de solicitud de préstamos.

**Segmentación de Clientes:**
Se utilizó el algoritmo K-Prototypes, configurado con n_clusters=3, inicialización Cao y random_state=42, para clasificar a los clientes en tres grupos según su nivel de riesgo: *Alto*, *Moderado* y *Bajo*. Los resultados obtenidos fueron:

- *Cluster 0: Alto Riesgo*
    -  Mora: 77%
    -  Atraso: 3.7 días
    -  Ingreso: Bajo (-0.42 DE)
    -  Deuda_sf: Baja (-0.21 DE)
    -  Edad: Jovenes (-0.56 DE)
    -  Score: Bajo (-0.57 DE)
    -  Vivienda: Familiar
    -  Zona: Lima
    -  Nivel educativo: Tecnica
    -  Perfil: Jóvenes con ingresos bajos, score bajo, deuda controlada, y nivel educativo técnico.
    Implicación: Restringir acceso al préstamo o requerir garantías adicionales.

- *Cluster 2: Riesgo Moderado*
    -  Mora: 65.45%
    -  Atraso: 5.6 días
    -  Ingreso: Promedio (0.07 DE)
    -  Deuda_sf: Promedio (-0.16 DE)
    -  Edad: Adultos (0.57 DE)
    -  Score: Alto (0.56 DE)
    -  Vivienda: Familiar
    -  Zona: Lima
    -  Nivel educativo: Universitaria
    -  Perfil: Adultos con historial estable, ingresos promedio, y buena calificación crediticia.
    Implicación: Evaluar con condiciones estándar
        
- Cluster 1: Bajo Riesgo
    -  Mora: 52.55%
    -  Atraso: 3.9 días
    -  Ingreso: Alto (1.94 DE)
    -  Deuda_sf: Alta (1.69 DE)
    -  Edad: Adultos (0.79 DE)
    -  Score: Alto ( 0.88 DE)
    -  Vivienda: Propia
    -  Zona: Lima
    -  Nivel educativo: Universitaria
    -  Perfil: Adultos con alta capacidad de pago, buen historial crediticio y nivel educativo avanzado.
    Implicación: Ofrecer condiciones crediticias favorables.

**Detección de Anomalías:**
Se aplicó el algoritmo Isolation Forest, configurado con contamination=0.05 y random_state=42, reconocido por su eficiencia en la detección de observaciones atípicas.
Resultados:

- Mora: 61.2% en promedio
- Atraso promedio: 8.86 días (máximo: 245 días)
- Ingreso: Alto (2.14 DE)
- Deuda_sf: Alta (2.18 DE)

Estas anomalías corresponden a clientes con perfiles financieros extremos que, aunque muestran capacidad económica, presentan patrones inusuales que podrían indicar riesgos ocultos o errores de registro.  Se recomienda su **revisión manual** para descartar posibles fraudes o inconsistencias.

## Conclusiones:
Los algoritmos **K-Prototypes** e **Isolation Forest** demostraron ser herramientas valiosas para:

- Revelar patrones ocultos en el conjunto de datos.
- Clasificar a los clientes según su riesgo crediticio.
- Detectar irregularidades que podrían comprometer la estabilidad financiera.

  Este enfoque permite fortalecer la gestión del riesgo en procesos de aprobación de créditos, aportando una base analítica sólida para la toma de decisiones estratégicas.

## Visualizaciones en Power BI:
Para complementar el análisis, se desarrolló un *dashboard en Power BI* con un diseño limpio y minimalista, permitiendo explorar los hallazgos del modelo de forma intuitiva y dinámica. Cada sección está enfocada en facilitar la comprensión de los perfiles de riesgo y apoyar la toma de decisiones.

### Portada del Proyecto
Pantalla de bienvenida con una breve introducción al proyecto y botones de navegación para acceder rápidamente a las distintas secciones del dashboard.

![portada](https://github.com/user-attachments/assets/edad9458-0b69-40ae-b0f1-ef318bd47956)

### Perfiles de Riesgo
Visualización comparativa de variables clave como ingreso, deuda_sf, edad y score, segmentadas por nivel de riesgo y desglosadas por nivel educativo. Esta vista permite identificar rápidamente las diferencias entre los grupos de clientes.

![perfiles_de_riesgo](https://github.com/user-attachments/assets/dc5f0da2-71ad-41d5-a097-4d6c9fb112af)

### Resumen General
Panel resumen con estadísticas globales:

- Total de clientes analizados
- Promedio de mora y atraso
- Score promedio
- Distribución de clientes por nivel de riesgo
Ideal para obtener una visión general del comportamiento de la cartera.

![resumen_general](https://github.com/user-attachments/assets/3e460df9-4598-4993-b552-3a6b6af3d79d)

### Recomendaciones
Sección final con sugerencias concretas para la aprobación de créditos según el perfil de riesgo identificado. Estas recomendaciones están alineadas con los resultados del clustering y la detección de anomalías.

![recomendaciones](https://github.com/user-attachments/assets/31a2ea34-8e36-4f27-90df-26b2b3e3746b)

## Cómo replicar el proyecto
1. Descargar el conjunto de datos: Descargue el conjunto de datos original de [Kaggle](https://www.kaggle.com). Encontrará el enlace en la descripción del proyecto del conjunto de datos.
2. Abrir el panel: Abra el archivo "riesgo_crediticio.pbix" en Power BI Desktop para ver y explorar el panel interactivo.
3. Ejecutar el notebook: Abra el notebook "riesgo_crediticio.ipynb" en Jupyter Notebook, Jupyter Lab o VS Code.
4. Asegúrese de tener instaladas las bibliotecas necesarias (pandas, numpy, scikit-learn, matplotlib, seaborn, etc.).  Trace las celdas en el notebook para replicar el análisis.  Adaptar y personalizar: Puede modificar el análisis y las visualizaciones para adaptarlos a sus necesidades o profundizar en aspectos específicos del modelo.

## Requisitos
Power BI Desktop (versión gratuita) - Python 3.x
Bibliotecas: pandas, numpy, scikit-learn, matplotlib, seaborn, entre otras.
Jupyter Notebook o Jupyter Lab

## Contribuciones
¡Las contribuciones son bienvenidas!
Si tienes ideas, sugerencias o mejoras que puedan enriquecer este proyecto, no dudes en compartirlas. Puedes abrir un issue para reportar errores o proponer cambios, o enviar un pull request con tus aportes.

Tu participación ayuda a construir soluciones más sólidas y colaborativas. ¡Gracias por ser parte de este proyecto!

## Autora
Jennifer Silva
jenniferlsu20@gmail.com 
www.linkedin.com/in/jennifer-silva-3aa1462a
