Airbnb Analisis Exploratorio y Descriptivo


Importación de las bibliotecas que usaremos.

import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt


Importamos el archivo "listings.csv", ubicado dentro de la carpeta "2 Airbnb"


listings = pd.read_csv("./2 AirBnB/listings.csv", low_memory=False)


Luego de ello, comenzaremos a depurar los datos y plantear algunas preguntas para profundizar un poco más en el tema y entender qué queremos analizar e indagar en las propiedades.

Diccionario de variables

id', número para identificar la propiedad

'name', nombre de la propiedad

'host_id', número de identificación del Propietario

'host_name', nombre del Propietario

'neighbourhood', Distrito o Barrio

'latitude', coordenada de latitud geográfica de la propiedad

'longitude', coordenada de longitud geográfica de la propiedad

'property_type', tipo de propiedad

'room_type', tipo de habitacion

'price', recio de alquiler de la propiedad

'minimum_nights', número mínimo de noches para reservar

'maximum_nights', número maximo de noches para reservar

'availability_365', número de días de disponibilidad dentro de los 365 días

'number_of_reviews', cantidad de reseñas

'last_review', fecha de la última reseña

'review_scores_rating', rating puntaje de reseña

'review_scores_value', puntaje de reseña

'amenities', Servicios ofrecidos por la propiedad

'calculated_host_listings_count', número de propiedades del mismo anfitrión

'calculated_host_listings_count_entire_homes', número de propiedades del mismo anfitrión del tipo de habitación Homes

'calculated_host_listings_count_private_rooms', número de propiedades del mismo anfitrión del tipo de habitación Privada

'calculated_host_listings_count_shared_rooms', número de propiedades del mismo anfitrión del tipo de habitación Compartida

'reviews_per_month' cantidad de reseñas por mes


Análisis de los datos

<class 'pandas.core.frame.DataFrame'>
RangeIndex: 23729 entries, 0 to 23728
Data columns (total 23 columns):
 #   Column                                        Non-Null Count  Dtype  
---  ------                                        --------------  -----  
 0   id                                            23729 non-null  int64  
 1   name                                          23719 non-null  object 
 2   host_id                                       23729 non-null  int64  
 3   host_name                                     23726 non-null  object 
 4   neighbourhood                                 23729 non-null  object 
 5   latitude                                      23729 non-null  float64
 6   longitude                                     23729 non-null  float64
 7   property_type                                 23729 non-null  object 
 8   room_type                                     23729 non-null  object 
 9   price                                         23729 non-null  object 
 10  minimum_nights                                23729 non-null  int64  
 11  maximum_nights                                23729 non-null  int64  
 12  availability_365                              23729 non-null  int64  
 13  number_of_reviews                             23729 non-null  int64  
 14  last_review                                   17222 non-null  object 
 15  review_scores_rating                          16839 non-null  float64
 16  review_scores_value                           16820 non-null  float64
 17  amenities                                     23729 non-null  object 
 18  calculated_host_listings_count                23729 non-null  int64  
 19  calculated_host_listings_count_entire_homes   23729 non-null  int64  
 20  calculated_host_listings_count_private_rooms  23729 non-null  int64  
 21  calculated_host_listings_count_shared_rooms   23729 non-null  int64  
 22  reviews_per_month                             17222 non-null  float64
dtypes: float64(5), int64(10), object(8)
memory usage: 4.2+ MB


En este punto podemos ver que solo en las reviews tenemos una cantidad considerable de datos nulos, estos podrian deberse a que la misma propiedad aun no ha recibido opiniones, que si bien utilizaremos este dato para futuros analisis, no realizaremos ninguna manipulación, por que las propiedades que no tienen reviews es por su poca o nula demanda.

lo que debemos de realizar es el cambio de tipo de dato de la columna 'price' a float y la columna 'last_review' a Datetime.

Analizamos el valor minimo y maximo del precio, encontramos datos extremadamente bajo y alto, para el precio '0' lo eliminamos.



