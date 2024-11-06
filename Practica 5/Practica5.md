## PARTE I. Datos abiertos

1. Investigar y mencionar 3 sitios de datos abiertos donde se puedan obtener datasets
relevantes para diferentes análisis a realizar. Describa el tipo de datos que se puede encontrar
en cada uno.

2. ¿Cuál es la diferencia entre datos públicos y datos abiertos? Proporciona un ejemplo de
cada tipo.

    Datos públicos: Son datos generados o resguardados por el gobierno y que están disponibles para el público, aunque pueden tener restricciones en cuanto a su uso o distribución. Ejemplo: el padrón electoral de un país, el cual es un dato público pero no es de libre uso ni compartible sin restricciones.

    Datos abiertos: Son datos públicos o de cualquier otra fuente que están disponibles sin restricciones para acceder, usar y distribuir. Estos datos deben cumplir con ciertos requisitos para garantizar su accesibilidad y reutilización. Ejemplo: datos sobre la calidad del aire de una ciudad, publicados por el gobierno bajo una licencia abierta que permite su uso y redistribución.


3. Mencione 3 tipos de licencias que pueden tener los datos abiertos, describiendo diferencias
entre ellas.    

    Creative Commons Attribution (CC BY): Permite el uso y la distribución de los datos, siempre y cuando se dé crédito al autor original. Esta licencia es muy flexible y facilita la reutilización de los datos, siempre que se mencione al creador original.

    Creative Commons Attribution-ShareAlike (CC BY-SA): Esta licencia también permite el uso y distribución de los datos, con la condición de que cualquier obra derivada se comparta bajo la misma licencia. Así, garantiza que el trabajo derivado siga siendo abierto y accesible bajo los mismos términos.

    Open Data Commons Public Domain Dedication and License (PDDL): Esta licencia permite la libre distribución y uso de los datos, sin requerir atribución o compartir bajo la misma licencia. Coloca los datos en el dominio público, lo que facilita su acceso y uso sin restricciones.

4. Suponga que tiene acceso a un dataset abierto sobre los niveles de contaminación del aire en diferentes ciudades del país. ¿Qué tipos de análisis podría realizar para obtener información útil?

        Tendencias temporales: Analizar cómo cambian los niveles de contaminantes (como el PM2.5, PM10, NO2) a lo largo del tiempo. Esto podría ayudar a identificar periodos del año con niveles de contaminación elevados o patrones estacionales.

        Comparación entre ciudades: Evaluar y comparar los niveles de contaminación entre distintas ciudades para identificar cuáles son las más y menos contaminadas, así como entender posibles factores asociados como el tamaño de la población, el nivel de industrialización y el tráfico vehicular.

        Correlación con indicadores de salud: Realizar un análisis de correlación entre los niveles de contaminación y la incidencia de enfermedades respiratorias en las ciudades, lo cual puede ayudar a determinar el impacto de la contaminación en la salud pública.

        Evaluación del cumplimiento de normas: Comparar los niveles de contaminación registrados con los límites permitidos por las normas ambientales para identificar ciudades o periodos en los que se han superado los límites de calidad del aire, lo que podría requerir medidas correctivas.

## PARTE II. Visualización de Datos
Dadas las situaciones que se presentan a continuación, decidir qué tipo de gráfico utilizaría
para visualizar la información de manera clara y efectiva. Justifique su elección indicando por
qué ese tipo de gráfico es el más adecuado para cada caso.


a. Comparación de suscripciones anuales por región geográfica
Se cuenta con un conjunto de datos de las suscripciones anuales de una empresa de telefonía
celular en distintas regiones (Norte, Sur, Este, Oeste) durante los últimos 5 años. ¿Qué tipo de
gráfico utilizaría para comparar las ventas entre las regiones durante los 5 años?
.

    En este caso seria mejor opcion el grafico de barra ya que si necesitamos analizar segun la temporalidad durante esos 5 años se va a poder distingir mejor segun las regiones y los ultimos 5 añós.
    Otra opcion podria ser el de lineas pero el problema que para ver datos en un periodo de tiempo es mas complejo que el de barra


b. Seguimiento del caudal de un río
Se han almacenado datos de registro del caudal promedio mensual en un punto de interés del
río Salado durante los últimos 10 años dada la baja que se observa. ¿Qué tipo de gráfico
usaría para mostrar la evolución del caudal a lo largo del tiempo?

    En este caso la mejor opcion segun mi opinion es el grafico de lineas ya que permite poder ver de forma eficiente anomalias y largas series de datos. 
    Este grafico creo que es el mejor porque permite ver con mejor represetnacion la baja del caudal, caso contrario si fuera de barra ya que si queremos conectar puntos entre los datos es mas complejo de entender.



c. Análisis de la distribución de las edades de clientes
Se tiene un dataset con datos de los clientes de una tienda virtual, entre ellos, la edad. El
objetivo es entender cómo se distribuyen las edades de los clientes. ¿Qué tipo de gráfico
utilizará para representar la distribución de las ciudades de los clientes?

    Creo que seria una buena opcion usar el grafico de barra agrupando las edades y dando algo mas visual ya que tambien podriamos usar la tabla pero perderias el tema visual.



d. Relación entre el precio y la puntuación otorgada por el cliente
Se tiene información sobre el precio de diferentes servicios ofrecidos y la calificación otorgada
por los clientes. ¿Qué tipo de gráfico usaría para analizar si existe una relación entre el precio
del producto y la puntuación marcada por el cliente?

    Creo que seria mejor usar un grafico de dispersion ya que te permite mostrar la correlacion entre 2 variables, permitiendo saber si hay una correlacion positiva o no.


e. Análisis de los préstamos de libros por género
Se cuenta con el registro de los préstamos de una biblioteca escolar. Entre los datos de cada
uno de estos se tiene el género del libro (narrativa, poesía, cuento, novela y biografía). ¿Qué
gráfico es adecuado para visualizar la proporción de préstamos de cada género?

    Creo que seria bueno un grafico de tortas seria el mas eficiente ya que en este caso, cada porción de la torta representaría un género de libro, y el tamaño de cada porción reflejaría la proporción de préstamos de ese género en comparación con el total de préstamos. Tambien podriamos usar burbujas o treemap por la falicidad de visualizar los datos.

f. Distribución del presupuesto 2025 por departamento y actividades
Se dispone de un dataset que contiene el presupuesto asignado a los diferentes departamentos
de una empresa (Marketing, Ventas, Desarrollo, Recursos Humanos), y dentro de cada
departamento, las actividades específicas (publicidad, investigación, capacitación, etc.). Qué
gráfico utilizará para mostrar cómo se distribuye el presupuesto total por categoría y cuánto
consume cada actividad dentro de la categoría?

    Creo que la mejor opcion es un gráfico de barras creo que es ideal cuando necesitas mostrar la distribución total (en este caso, el presupuesto) entre varias categorías y subcategorías (departamentos y actividades).
    Cada barra representaría un departamento y dentro de cada barra, se apilarían segmentos que corresponden a las actividades dentro de ese departamento.
    El largo de la barra total representaría el presupuesto asignado al departamento, mientras que los segmentos apilados dentro de la barra indicarían qué porcentaje del presupuesto total de ese departamento se destina a cada actividad.




g. Tendencia de ingresos mensuales de una empresa
Se registraron los ingresos mensuales de una empresa mes a mes durante los últimos 3 años.
Se quiere observar la tendencia para determinar la tendencia al alza o a la baja. ¿Qué tipo de
gráfico es adecuado para representar la tendencia de ingresos elegiría?

    Creo que la mejor opcion podria ser un grafico de lineas ya que te permitiaria ver las diferentes subidas y bajadas mes a mes de los ingresos mensuales.
    Es fácil de interpretar y permite comparar la tendencia general de los ingresos en un periodo largo.


h. Evaluación de comentarios de un trailer de película
Se tiene un conjunto de datos con comentarios sobre el trailer de la película realizados por los
seguidores de perfil fan de la misma. ¿Qué tipo de gráfico usaría para evaluar qué comentarios
son más frecuentes y por lo tanto, describen al trailer de la película?

    La mejor opcion seria un grafico de nube de palabras ya que las palabras más frecuentes se presentan en un tamaño más grande, lo que permite identificar rápidamente qué términos dominan en la conversación sobre el trailer.
    Además, es una visualización atractiva y fácil de interpretar, especialmente para el análisis cualitativo de los comentarios.
    
i. Evolución del precio de una acción
Se dispone de un registro del precio diario de una acción durante el último año. ¿Qué tipo de
gráfico elegiría para mostrar la evolución del precio de la acción observada a lo largo del
tiempo?`

    Creo que la mejor opcion podria ser un gráfico de líneas ya que es el tipo de gráfico ideal para mostrar series temporales, como el precio diario de una acción. Este gráfico conecta los puntos de datos con una línea.

j. Densidad poblacional por provincia
Un conjunto de datos contiene la densidad de población (habitantes por km2) de cada provincia
del país. Qué gráfico le permitirá visualizar rápidamente qué provincias tienen una mayor
densidad de población, representando con diferentes tonos? Más oscuro, mayor densidad
poblacional.    

    Creo que la mejor opcion podria ser un grafico de mapa de simbolos propopcionales, ya que podrias ver las provincias y con un color dependiendo la densidad poblacional o quizas se puede usar grafico de barra o de dispersion aunque perderias la forma de verlo en un mapa. Entre barra y dispersion elegiria quizas el de barra es útil para comparar valores entre categorías, pero no te da ninguna idea de dónde están ubicadas las provincias ni cómo se distribuyen en el país.


k. Visualización de la proporción de ventas por categoría de producto
El dataset muestra la cantidad de clientes que compraron productos de distintas categorías
(Vegano, vegetariano, Sin TACC, sin azúcar agregada, orgánico, cosmética).¿Qué gráfico es
adecuado para visualizar la proporción de clientes que compraron cada categoría de producto?

    Creo que el grafico de barra seria la mejor opcion ya que es ideal cuando deseas comparar categorías discretas pero no habria que descartar el grafico de torta que puede llegar a ser mas vizual que el de barra y cada porcion de torta significaria un categoria de productos.