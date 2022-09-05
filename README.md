# w4 ETL Project


## Introduction

El proyecto de esta semana consiste en hacer el proceso completo de ETL (extracción, transformación y carga)

Hemos elegido la tematica de Car Sharing, donde analizaremos algunos datos como coste medio trayecto desde un origen a un destino, dias mas/menos economicos para usar este servicio, ahorro frente a otros medios de transporte..


## Proceso

Despues de buscar en varias webs de bases de datos, no encontramos nada con la tematica relacionada, por lo que decidimos extraer los datos de manera manual de su web.

Primeramente hemos intentado usar BS4, pero nos ha resultado imposible, ya que, pese a que en el inspector de Chrome, si nos mostraba las etiquetas, clases y demas parametros, cuando intentamos hacerlo con BS4, nos mostraba un bloqueo.

Tras este inconveniente, decidimos pasar a utilizar selenium.

El primer reto dentro de seleción era descifrar la estructura de su URL para poder simularla y realizar busquedas directas.

Una vez descifrada la URL, empezamos el scrapeo, y nos damos cuenta de que solo nos esta escrapeando los 9-10 primeros valores. Como solución, modificamos el codigo, añadiendo un scrol hasta el final de pagina. Aun asi, tenemos que seguir realizando varios scrols por que sigue carando viajes.

Empezamos a scrapear los primeros datos, y decidimos utilizar mongo como alojamiento de los datos.

Tras las primeras casi mil lineas, nos damos cuenta que el codigo esta mal, y estamos introduciendo el mismo ID a todos los viajes.

Borramos BBDD y volvemos a iniciar el proceso.

Tras otras miles de lineas, nos damos cuenta, que tanto la ciudad de origen, como ciudad de destino que nos esta extrayendo, no es la correcta, puesto que esta cogiendo la localidad en lugar de la ciudad, lo que nos dificultaria a posteriori el analisis de la información.

Procedemos de nuevo a borrar la BBDD y corregimos el codigo para que extraiga la provincia.

A todo esto, hay que decir que cada x tiempo, nos salta el detector de boot. Intentamos dar tiempos de espera mayores, cambiar patrones... pero no conseguimos evitarlo, aunque si alargar el tiempo entre las veces que nos salta.



El siguiente metodo de extracción de la información es a traves de API. Nos conectamos a la API de la AEMET y nos traemos información del tiempo por provincia. Para mas adelante, ver si tiene relación las condiciones climatologicas con el aumento o disminución del numero de trayectos.

Por ultimo, volver a hacer una extracción de la wikipedia de una tabla de CP y Provincias para poder unir las BBDD de los viajes de BlaBlaCar con la tabla de la AEMET.

Finalmente volcamos las tablas a power bi, para realizar la presentación y analisis de los datos.






