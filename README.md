# CIENCIA DE DATOS - PROYECTO INDIVIDUAL Nº1
## HASSINGER SIPIRAN NATALY ARLEEN - DATAFT13 
## Operaciones de aprendizaje automático (MLOps)
![Imagen del steam](proyecto.png) 

*Este proyecto abarca una serie de pasos para desarrollar un proceso de Data Engineering sobre un conjunto de datos de juegos, para posteriormente disponer de una serie de endpoints utilizando Machine Learning, a través de una API.*


### Contexto : 
*Se plantea desde los departamentos de Machine Learning y Analytics la necesidad de contar con los datos en una API para poder ser consumidos. Por otro lado existe la necesidad de poder realizar las consultas al modelo de recomendaciones para lo cual resulta necesario hacer un deployment de la API. El cual consta de 2 partes :*

### 1ra Parte: Transformaciones de los datos de una plataforma multinacional de videojuegos, llamada “Steam”:
*Hay datos anidados, datos en diccionario, datos nulos, fechas en otro formato, columnas que no se utilizarán y se borrarán.*
### 2da Parte: Desarrollar una API, con las siguientes consultas: se realiza una API para visualizar las consultas necesarias, como: 
*Género, Juegos, Specs (especificaciones), Earlyacces (acceso temprano), Sentiment (análisis de sentimiento), Metascore (score por metacrítica).*

## Conjunto de datos
*El [Dataset](https://drive.google.com/drive/folders/1HqBG2-sUkz_R3h1dZU5F2uAzpRn7BSpj) en cuestión posee información acerca de los videojuegos y características distintas de las mismas en su diccionario.*
<!--Enlace-->
[Steam](steampowered.com)
<!--imagen-->

![Imagen del steam](steam.png)

### API de desarrollo:
Propone disponibilizar los datos de la empresa usando el framework FastAPI. Las consultas que propone son las siguientes:

*Deben crear 6 funciones para los endpoints que se consumirán en la API, recuerden que deben tener un decorador por cada una (@app.get('/')):*

1. def genero( Año: str ): Se ingresa un año y devuelve una lista con los 5 géneros más ofrecidos en el orden correspondiente.

2. def juegos( Año: str ): Se ingresa un año y devuelve una lista con los juegos lanzados en el año.

3. def specs( Año: str ): Se ingresa un año y devuelve una lista con los 5 specs que más se repiten en el mismo en el orden correspondiente.

4. def earlyacces( Año: str ): Cantidad de juegos lanzados en un año con acceso anticipado.

5. def sentiment( Año: str ): Según el año de lanzamiento, se devuelve una lista con la cantidad de registros que se encuentran categorizados con un análisis de sentimiento.

6. def metascore( Año: str ): Top 5 juegos según año con mayor metascore.

## Ingeniería de datos
Para el trabajo de *Data Engineering* se procedió a efectuar una serie de transformaciones solicitadas sobre los datos, dentro de las cuales se encuentran:

- Algunos campos que están anidados, debeá ser desinfectados para poder avanzar y unirlos al conjunto de datos de nuevo para hacer alguna de las consultas de la API.

- Los valores nulos del campo deben eliminarse.

- De haber fechas, deberá tener el formato AAAA-mm-dd, además deberás crear la columna release_year donde extraerás el año de la fecha de estreno.

- Eliminar las columnas que no se utilizarán.

Se pueden visualizar las transformaciones,análisis y API realizados en el siguiente [archivo](PI1.ipynb) 

## Realizar un Deployment: por medio de Render.
Se realiza un Análisis exploratorio de datos: *( Exploratory Data Analysis-EDA ).*

- Se realiza un Modelo de Predicción (Regresión lineal y RMSE ), pensando en alguna relación entre variables, para predecir el precio de los videojuegos a futuro. Se escogen: “Id", “precio”, y “año_lanzamiento”.

# Conclusiones:
- Hubo problemas con el **“archivo .json”**, se transformó en un **“.csv”** para poder manipular los datos (problemas de “encodación”).

- Para el modelo de recomendación de videojuegos Machine Learning se obtuvo como criterio filtrar el dataset para los juegos lanzados a partir de 1996 release_year( por mostrar un gran crecimiento a partir de dicho año) .

- Se trabajó uniendo los textos de las columnas price, release_year e Id para concatenarlos en un solo campo de modo que el algoritmo pueda trabajar sobre el mismo. Una vez con el dataframe listo se procedió a construir el modelo.

- -Se intentó una Regresión lineal entre “precio” y “año”, pero no había relación alguna, por tanto no hay pendiente ni intercepto. Tampoco se obtuvo **RMSE**.
