# PROYECTO APLICADO EN ANALITICA DE DATOS 
El grupo Stanley es un consorcio financiero creado hace 50 años, una de sus áreas
corporativas es la relacionada con la mesa de mercado de capitales MD, donde los énfasis son
las inversiones en instrumentos de renta variable (acciones derivadas cuyos subyacentes son
acciones) y cuya fundación se realizó hace seis años junto con el grupo de desarrollo de
innovación de producto financieros. Estos grupos están conformados por equipos en diferentes
países que se encargan, entre otros, de analizar oportunidades de inversión, fungir como
corredores en conjunto con otras entidades financieras, analizar tendencias del mercado y
desarrollar nuevos productos de inversión y de consumo masivo financiero.

El equipo  de especialistas y asesores externos proponen la creación y desarrollo de un nuevo producto que permita la visualización histórica y a futuro de las
variables de interés relacionadas con el índice S&P 500, adicionalmente este producto debe permitir la identificación o agrupación de acciones que poseen rendimientos similares con el
ánimo de generar una diversificación de portafolios más eficiente y de esta forma poder lograr incrementar el margen de rentabilidad proveniente de las inversiones realizadas por la mesa de dinero. 

# Desarrollo de la propuesta
En la primera parte se hace una carga y limpieza de los datos, luego el desempeño y analisis de los modelos y por último se encuentra
la parte de las predicciones. Este proceso se encuantra descrito en las siguinetes carpetas:

# Carga de los datos:
Dentro de la carpeta se encuentra el archivo "Yahoo_finance.ipynb" en este notebook se describe el proceso de cargue y actualización
de los datos. Este proceso se hace a través de una conexión con una hoja de spreadsheets para utilizarla como base de datos y guardar información de forma incremental. Primero se obtiene un primer historico y se almacena en la hoja, cada vez que se ejecuta el codigo, 
guarda  la información en ella, la convierte en un  dataframe  y la almacena. Este proceso se realiza todos los dias sobre las 
7:00 pm. 

En este dataframe encontramos todos los simbolos del S&P 500, este registro de los simbolos se hace sobre los últimos 5 dias y se 
concatena con la base guardada anteriormente. se eliminan duplicados para no incurrir en costos computacionales elevados y se obtiene 
un dataframe denominado simbolos. Finalmente se limpia la hoja de spreadsheets para comenzar de nuevo el ciclo de carga de los datos.

# Limpieza de datos:
luego de realizada la carga del dataframe y transcurrido el tiempo necesario (sobre las 7:30 pm), se conecta con la API de spreadsheets, luego abre la información actualizada y establece la fecha como el indice del dataframe. Una vez realizada esta transformaciòn se comienza a hacer el análisis exploratorio de los datos, se verifica la cantidad de datos nulos, se analiza la cantidad de datos a eliminar y se realiza la imputabilidad de variables. El proceso de imputabilidad se lleva a cabo mediante KNNImputer tomando como vecinos k=2; es decir,tomando el día anterior y posterior al dato faltante o los datos más cercanos en caso de no existir los primeros. 

Realizado el proceso de limpieza e imputación, se exporta esta data a un archivo denominado SP_500_data_clean, luego se transforman los datos obteniendo la variación porcentual y se envian a un nuevo archivo denominado SP_500_data_pct.

# Modelos y análisis:
El proceso de selección de modelo se realiza bajo demanda, en este caso se analizan dos modelos. Primero se hace un análisis historico mediante una descripciòn gráfica del portafolio de activos de preferencia de la mesa de mercado del grupo Stanley, luego se hace la descomposición de la serie de tiempo y hacemos el respectivo análisis de cada una de ellas mediante  estacionalidad, tendencia y ruido. posteriormente se realiza un analisis de los correlogramas y los gráficos de autocorrelación (ACF) y autocorrelación parcial (PACF) llegando a la conclusión de que pueden ser modeladas mediante procesos autoregresivos. Se analizan tambien los supuestos de media y desviación estándar, ya que en algunos casos la variabilidad de los datos puede enmascarar la naturaleza de la serie y por ende, afectar la capacidad evaluativa de la prueba ADF, se aplica una suavización exponencial a la serie para poder corregir el ruido







