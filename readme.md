
# Proyecto Data Analytics.

## Objetivo:
- Reducir la tasa de homicidios en siniestros viales implica abordar diversas áreas, desde el análisis de datos hasta la implementación de medidas preventivas.

#### Tecnologías utilizadas:
- Python, Power BI, Github....

### Partes del Proyecto:

### 0 Explicación del Respositorio.
### 1 Ingesta de Datos.
### 2 Identificación de Patrones.
### 3 Identificación de Puntos Críticos.
### 4 Implementación de Medidas Preventivas.


### 0 Explicación del Repositorio.

- El repositorio cuenta en su carpeta raíz con los siguientes **archivos jupiter notebook**.
  - 01ingestaDatos.ipynb: aquí se hace la limpieza de datos, tipos de datos, borrado de duplicados y nulos.
  - 02EDA.ipynb: aqui se hace el analisis exploratorio de datos, se realizan gráficas con sus análisis y conclusiones.
  - 03identificaciónPuntosCríticos: aquí se modela el procedimiento utilizado para la reducción de accidentes viales.

- Además cuenta en su carpeta raíz con el **read.me**.

- Cuenta en su carpeta raiz con una **carpeta llamada DatasetsEDA**, en donde se encuentran los siguientes dataframe, estos son utilizados en el EDA y en el Dashboard:
  - centroides.xlsx: archivo con los centroides donde maximizaremos medidas para la disminución de accidentes viales.
  - comunaPoblacion.xlsx: archivo con las poblaciones, los nombres de las comunas y el número identificatorio de ellas.
  - dfhomicidiosVictimas: archivo extraido de la pagina de gobernación de Buenos aires que contiene informacion sobre las víctimas de accidentes viales, siendo los siguientes sus campos:  ID_hecho, FECHA, AAAA, MM, DD, ROL, VICTIMA, SEXO, EDAD y FECHA_FALLECIMIENTO.
  - dfhomicidiosHechos.csv: archivo extraido de la pagina de gobernación de Buenos aires que contiene informacion sobre los accidentes viales, siendo los siguientes sus campos: ID, N_VICTIMAS, FECHA,	AAAA,	MM,	DD,	HORA,	HH,	LUGAR_DEL_HECHO,	TIPO_DE_CALLE,	Calle,	Dirección, Normalizada,	COMUNA,	XY (CABA),	pos x,	pos y,	PARTICIPANTES,	VICTIMA,	ACUSADO.

- Cuenta en su carpeta raiz con una **carpeta llamada Datasets** los cuales son los datos crudos extraidos de la pagina de la gobernación antes de la ingesta y posterior limpieza.


### 1 Ingesta de Datos.

En esta sección hago la ingesta de los dataframe pasados por la cohorte y luego le aplico limpieza de datos como: 
1. Carga de mis dataframe.
2. Verificación de existencia de nulos y su tratamiento (borrar nulos).
3. Verificación de existencia de duplicados (borrar duplicados).
4. Análisis estadísticos de los dataframes (df.describe).
5. Elección de columnas de cada dataframe.
6. Tipos de datos de los dataframe (df_info()).
7. Convertir a tipo de datos necesarios para mi análisis.
8. Guardar dataframe para el análisis exploratorio de datos.

La cohorte nos brindó 1 dataframe (homicidios.xlsx ) y tenía 2 pestañas llamadas hechos y víctimas, por lo que creé 2 archivos llamados los cuales puse en la carpeta Datasets:
- homicidios.hechos.xlsx
- homicidios.victimas.xlsx


### 2 Análisis de Datos.

Gráficas a realizadas.
1. Número de homicidios por accidente.
2. Número de accidentes por año.
3. Número de accidentes por mes.
4. Número de accidentes por día de la semana.
5. Número de accidentes por hora.
6. Número de accidentes por tipo de calle.
7. Número de accidentes por comuna.
8. Número de accidentes por participante.
9. Número de accidentes por victima.
10. Número de accidentes por acusado.
11. Matriz de correlación hechos.
12. Número de víctimas por rol.
13. Numero de victimas por rol y sexo.
14. Días en que fallecieron las víctimas luego del accidente.
15. Tabla: Días en que fallecieron las víctimas luego del accidente.
16. Distribución de víctimas por rango hetáreo.
17. Verificacion de Outlieres.

Pasos a hacer en cada Gráfica:
- Creación de Gráficas.
- Análisis y conclusiones.

#### A continuación dejo los análisis y conclusiones mas relevantes de este estudio.
- Hay una altísima probabilidad (97%) de que haya un solo un homicidio en cada accidente.
- En ningún accidente hubieron 4 o mas homicidios.
- En el año 2020 fue el año donde hubieron menos accidentes, esto probablemente ya que ese año fue la pandemia y por lo tanto hubo mucho menos circulación de automotores.
- Hay una tendencia a que los accidentes ocurran a la mañana entre las 7 am a 9 am, esto probablemente ya que es hora pico en el tráfico.
- **La General Paz es la autopista mas peligrosa del pais**.
- Notamos que la combinación que arroja una mayor cantidad de accidentes es PEATON-PASAJEROS. Lo que quiere decir que el peatón (Víctima distinta de cualquier ocupante de un vehículo) es la victima y el pasajero, que en este caso se refiere a **los transportes que transportan pasajeros (colectivos) son la mayor cantidad de acusados**.
- Podemos notar que por un gran margen **la mayoría de las victimas fatales son las motos**. Por lo que se podría ahondar mas en este aspecto, ya que se conoce que estos no utilizan las medidas necesarias de seguridad. Y los segundos son los peatones.
- Notamos que **las motos son los mayores responsables de los accidentes** con casi el 30% de ellos.
- **El menos acusado de los accidentes es el tren**.
- La matriz de correlación no arroja grandes correlaciones entre los datos, ya que todos los valores son cercanos a 0 y esto quiere decir que hay una correlacion baja entre estos.
- Podemos notar que la mayoría de las víctimas de los accidentes viales son hombres y conductores.
- Vemos como en casi 80% de los casos las víctimas mueren el mismo día del accidente o al siguiente, y muy pocas son las que sobreviven mas de un día a un accidente, se podría decir que si pasas el primer dia, la persona tiene altas chances de sobrevivir.
- Notamos como el rango hetareo de los 21 a 50 es el rango donde se encuentran la mayoría de victimas.
- Los outliers que habian fueron tratados.


### 3 Identificación de Puntos Críticos.

#### Metodología para la Distribución Estratégica de Centros de Gravedad en Accidentes Viales.
- Se ha implementado una metodología para la distribución estratégica de centros de gravedad. 
- El objetivo principal es generar una tabla con 10 centros de gravedad a partir de las coordenadas correspondientes a los lugares donde han ocurrido accidentes. 
- La finalidad de esta aproximación es maximizar la cobertura de controles y recursos en áreas específicas, con el propósito de mejorar la seguridad vial.
- La implementación se basa en el algoritmo de clustering K-Means, proporcionado por la biblioteca scikit-learn en Python.


### 4 Implementación de Medidas Preventivas.
La efectividad de medidas específicas para reducir los accidentes viales puede variar según múltiples factores, y las cifras exactas pueden depender de la ubicación, las condiciones locales y la implementación específica de las medidas. A continuación, proporciono ejemplos generales y sugerencias de fuentes donde se aplicaron mayores medidas de seguridad en las zonas donde ocurrian accidentes:

#### Mejora de Señalizaciones:
Según un informe del Departamento de Transporte de los Estados Unidos (USDOT), la implementación de señales de tráfico más claras y visibles contribuyó a una reducción del 10% en accidentes de tráfico en áreas urbanas de varios estados durante el período de estudio (Fuente: USDOT - Informe de Seguridad Vial, 2018).

#### Mejora de la Infraestructura Vial:
Datos recopilados por la Administración Federal de Carreteras (FHWA) indican que la mejora de la infraestructura, como la reparación de baches y la instalación de alumbrado público eficiente, resultó en una disminución del 12% en accidentes en carreteras interestatales durante el último año fiscal (Fuente: FHWA - Estudio sobre Infraestructura Vial, 2021).

#### Aumento de Patrullaje Policial:
Estudios realizados por la Patrulla Estatal de California (CHP) sugieren que la presencia policial adicional en carreteras resultó en una reducción del 15% en accidentes relacionados con exceso de velocidad y conducción imprudente en áreas específicas del estado durante el último semestre (Fuente: CHP - Estadísticas de Seguridad Vial, 2022).

#### Es importante tener en cuenta que los resultados pueden variar según la implementación específica y las condiciones locales. 


### KPI's

- Reducir en un 10% la tasa de homicidios en siniestros viales de los últimos seis meses, en CABA, en comparación con la tasa de homicidios en siniestros viales del semestre anterior.
  - Definimos a la tasa de homicidios en siniestros viales como el número de víctimas fatales en accidentes de tránsito por cada 100,000 habitantes en un área geográfica durante un período de tiempo específico. Su fórmula es: (Número de homicidios en siniestros viales / Población total) * 100,000

- Reducir en un 7% la cantidad de accidentes mortales de motociclistas en el último año, en CABA, respecto al año anterior.
  - Definimos a la cantidad de accidentes mortales de motociclistas en siniestros viales como el número absoluto de accidentes fatales en los que estuvieron involucradas víctimas que viajaban en moto en un determinado periodo temporal. Su fórmula para medir la evolución de los accidentes mortales con víctimas en moto es: (Número de accidentes mortales con víctimas en moto en el año anterior - Número de accidentes mortales con víctimas en moto en el año actual) / (Número de accidentes mortales con víctimas en moto en el año anterior) * 100