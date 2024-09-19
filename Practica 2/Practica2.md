# Práctica Nro. 2
## Normalización

![alt text](image.png)

# PARTE I
### 1) Indicar la opción correcta. 

#### Dado el siguiente esquema:

    MapasPublicados (idMapa, proyección, escalaMapa, idSitioWeb, dominioSitioWeb,especialidadSitioWeb, dueñosSitioWeb, fechaPublicaciónMapa, valorPublicación)
    
    Donde:
    
    ● A un sitio web se le cobra un valor (“valorPublicación”) por cada fecha (“fechaPublicaciónMapa”) en la cual publique un mapa.

    ● Un sitio web puede tener varios dueños (“dueñosSitioWeb”).
    
    ● Un sitio web posee un único dominio (“dominioSitioWeb”).
    
    ● El identificador de un mapa (“idMapa”) es único.
    
    ● El identificador de un sitio web (“idSitioWeb”) es único.
    
    ● Un mapa se genera con una proyección y a una escala.
    
    ● “especialidadSitioWeb” es la especialidad de un sitio.

DF:

 * idMapa --> proyeccion,escalaMapa

 * idSitioWeb --> dominioSitioWeb,especialidadSitioWeb

 * idMapa,idSitioWeb,fechaPublicacion --> valorPublicacion

 * idMapa,dominioSitioWeb,fechaPublicacion --> valorPublicacion
    
 * dominioSitioWeb --> idSitioWeb,especialidadSitioWeb
    
Seleccione la frase que considera verdadera

● El esquema tiene una clave candidata

● El esquema tiene más de una clave candidata (Verdadera)

Son: 

 * { ID Mapa, ID Sitio Web, fecha Publicación Mapa, dueños Sitio web }
 * { ID Mapa, dominio Sitio Web, fecha Publicación Mapa, dueños Sitio web }


## 2. Clave candidata

### Dado el siguiente esquema donde se cumplen las siguientes dependencias funcionales df1 y df2:

    E(a, b, c, d, e, f)

    df1) a->b, c
    df2) c->d, e

    ¿Cuál de las siguientes CC es la correcta?
    
    1. CC(a,c}
    2. CC(a)
    3. CC(a,f)
    4. CC(a,c,f)
    5. CC(f)


## 3. Indicar la opción correcta

### Dada la relación:

    ALUMNO (DNI, nyAp, nroLegajo, promedio, #libroUsadoEnCarrera)
    
En la que se cumple las siguientes dependencias funcionales:
DF1) DNI → nyAp, nroLegajo, promedio
DF2) nroLegajo → nyAp, DNI, promedio
¿Cuál de las siguientes afirmaciones es correcta?
a) La relación ALUMNO tiene dos claves candidatas y tendrá dos claves primarias.
b) La relación ALUMNO tiene dos claves candidatas y tendrá una clave primaria.
c) No puedo identificar una clave.
d) Ninguna de las anteriores.



4. Dependencias funcionales

Dado el siguiente esquema:

    TIENDA (#aplicacion, nombre_aplicacion, descripcion, #categoria, #etiqueta, #desarrollador, nombre_apellido_desarrollador, #actualizacion descripcion_cambios)

Donde:

    ● #aplicacion, #categoria, #etiqueta y #desarrollador son únicos en el sistema.

    ● Una aplicación tiene un nombre y una descripción, y puede actualizarse muchas
    veces

    ● Para cada actualización de una aplicación se registra un texto con los cambios
    realizados. El #actualización es secuencial, cada aplicación define los suyos y
    puede repetirse entre distintas aplicaciones.

    ● Cada aplicación tiene una única categoría y muchas etiquetas. Las etiquetas
    pueden ir cambiando con cada actualización de la aplicación (en cada
    actualización puede haber un conjunto diferente de etiquetas). La categoría
    nunca cambia, es decir que se mantiene igual sin importar las actualizaciones.

    ● Una aplicación es realizada por varios desarrolladores de los cuales se conoce
    su nombre y apellido.


Seleccione las DFs válidas / mínimas: Para las que no se seleccionen, indicar el
motivo.

    1) #aplicacion, #actualizacion -> nombre_aplicacion, descripcion ✅
    2) #aplicacion, #actualizacion -> descripcion_cambios ✅
    3) nombre_apellido_desarrollador -> #desarrollador ❌
    4) #desarrollador -> nombre_apellido_desarrollador ✅
    5) #aplicación -> #categoria ✅

Encontró alguna dependencia funcional más, que no se menciona entre las opciones?

* CC `{ #aplicación, #actualización, #desarrollador, #etiqueta }`


5. Dependencias multivaluadas

Dado el siguiente esquema:

    CURSOS(#curso, titulo_curso, #nro_modulo, titulo_modulo, contenido_modulo,
    nombre_autor, email_autor, contraseña_autor, año_edicion, calificacion,
    referencia)

Donde:

    ● Cada curso (#curso) se va editando todos los años, y en cada año (año_edicion)
    puede cambiar sus módulos, no así el título y el autor.
    ● En cada año que se edita un curso, recibe varias calificaciones anónimas.
    ● El email de cada autor se usa como login, y no puede repetirse en el sistema.
    ● Los números de módulo (#nro_modulo) son secuenciales (modulo 1, 2, 3, etc).
    Es decir, en cada edición de cada curso se enumeran los módulos de la misma
    forma, y se pueden repetir en diferentes ediciones de cursos.
    ● Cada curso tiene múltiples referencias bibliográficas, que se mantienen a través
    de todas sus ediciones.

Dadas las siguientes DF:

    ● #curso -> titulo_curso, email_autor
    ● #curso, año_edicion, #nro_modulo -> titulo_modulo, contenido_modulo
    ● email_autor -> nombre_autor, contraseña_autor
    
    Dada la siguiente CC:
    
        ● (#curso, año_edicion, #nro_modulo, calificacion, referencia)
    
    Y el esquema en BCNF
    
        CURSOS_N (#curso, año_edicion, #nro_modulo, calificacion, referencia)

Seleccione las DM que son válidas a la vez en el esquema CURSOS_N:

    ● #curso ->> año_edicion
    ● #curso ->> referencia
    ● #curso,año_edicion ->> calificacion
    ● referencia ->> #curso
    ● año_edicion ->> #curso

Existe alguna dependencia multivaluada más que no se menciona entre las opciones?




# Parte II

### Dados los siguientes esquemas, realizar todo el proceso de normalización hasta 4FN.

    6. SUSCRIPCION (#suscripcion, email, nombre_usuario, #plan, nombre_plan,
    texto_condiciones, precio, email_adicional, nombre_adicional, #contenido, titulo,sinopsis, duracion, fecha_adicional)
    
    Donde:

        ● Cada suscripción es realizada por un único usuario (identificado por el email) y un plan, pero además hay usuarios adicionales que la utilizan (email_adicional). De cada usuario adicional que se suma a la suscripción, se guarda la fecha.

        ● Un plan de suscripción tiene un nombre (que no puede garantizarse que sea único en el sistema), condiciones, y un precio mensual.

        ● Cada contenido tiene un título, sinopsis y duración. El #contenido es único en el sistema, pero del título no puede garantizarse que lo sea.

        ● De cada suscripción se sabe qué contenidos fueron reproducidos, sin distinción sobre qué usuario (titular o adicionales) reprodujo cada uno.

DF:
    

    1- #suscripcion --> email,#plan
    2- email --> nombre_usuario
    3- #plan --> nombre_plan,texto_condiciones,precio
    4- #contendio --> titulo, sinopsis , duracion
    5- email_adicional --> nombre_adicional
    6- #suscripcion,email_adicional --> fecha_adicional
    

* CC `{#suscripcion,#contenido,email_adicional}`

#### Iteracion 1:

En este caso podemos ver que tenemos al menos una DF, por ej DF5, en la que X no sea superclave en el esquema

Particionamos el esquema usando la DF5 `email_adicinal --> nombre_adicional`

* F1(**email_adicional**,nombre_adicional)

* F2(**#suscripcion,email_adicional,#contenido**, email, nombre_usuario, #plan, nombre_plan texto_condiciones, precio, titulo,sinopsis, duracion, fecha_adicional)

F1 esta en BCNF porque solo vale la DF5 donde email_adicional es clave del esquema.
En F2 valen DF1, DF2,DF3, DF4,DF6 por validacion simple no se pierden dependecias funcionales
F1 ⋂ F2 = email_adicional, que es clave en F1. Por lo tanto, no se perdió información.



    #suscripcion --> email,#plan
    email --> nombre_usuario
    #plan --> nombre_plan,texto_condiciones,precio
    #contendio --> titulo, sinopsis , duracion
    email_adicional --> nombre_adicional
    #suscripcion,email_adicional --> fecha_adicional





#### Iteracion 2:

F1 cumple con BCNF pero F2 sigue teniendo DF no triviales o en la que X no es una superclave

por lo que particionamos F2 siguiendo el esquema DF2

F3(**email**,nombre_usuario)
F4(**#suscripcion,email_adicional,#contenido**, email, #plan, nombre_plan texto_condiciones, precio, titulo,sinopsis, duracion, fecha_adicional)


F3 ⋂ F4 --> email no perdemos informacion
En F4 valen DF1,DF3,DF4,DF5 por validacion simple no se pierden dependecias funcionales

    #suscripcion --> email,#plan
    email --> nombre_usuario
    #plan --> nombre_plan,texto_condiciones,precio
    #contendio --> titulo, sinopsis , duracion
    email_adicional --> nombre_adicional
    #suscripcion,email_adicional --> fecha_adicional

#### Iteracion 3

F3 cumple con BCNF pero F4 no cumple BCNF ya que sigue teniendo DF las cuales X no es superclave
por lo que particionamos usando la DF3

F5(**#Plan**,nombre_plan,text_condiciones,precio)
F6(**#suscripcion,email_adicional,#contenido**, email, #plan, titulo,sinopsis, duracion, fecha_adicional)

F5 ⋂ F6 --> #Plan no perdemos informacion
En F6 valen DF1,DF4,DF6. No se pierden dependecias funcionales

#### Iteracion 4

F5 cumple con BCNF pero F6 no cumple ya que sigue teniendo DF de las cuales X no es superclave por lo que particionamos usando la DF4

F7(**#Contendio**,titulo,sinopsis,duracion)
F8(**#suscripcion,email_adicional,#contenido**, email, #plan,fecha_adicional)

F7 ⋂ F8 --> #Contenido no perdemos informacion
En F8 valen DF1,DF6. No se pierden dependecias funcionales

#### Iteracion 5
F7 cumple con BCNF pero F8 sigue teniendo DF de las cuales X no es superclave

F9(**#Suscripcion**,email,#plan)
F10(**#suscripcion,email_adicional,#contenido**,fecha_adicional)

F9 ⋂ F10 --> #Contenido no perdemos informacion
En F10 valen DF6. No se pierden dependecias funcionales

#### Iteracion 6

F9 cumple con BCNF pero F10 sigue teniendo DF de las cuales X no es superclave
por lo que particionamos usando la DF6

F11(**#suscripcion,email_adicional**,fecha_adicional)
F12(**#suscripcion,email_adicional,#contenido**)

F11 ⋂ F12 --> #suscripcion,email_adicional no perdemos informacion

Y con esta ultima iteracion tenemos como resultado

* F1(**email_adicional**,nombre_adicional)
* F3(**email**,nombre_usuario)
* F5(**#plan**,nombre_plan,text_condiciones,precio)
* F7(**#contendio**,titulo,sinopsis,duracion)
* F9(**#suscripcion**,email,#plan)
* F11(**#suscripcion,email_adicional**,fecha_adicional)
* F12(**#suscripcion,email_adicional,#contenido**)

ahora cada tabla se encuentra en BCNF

#Falta 4FN

# Ejercicio 7

7. MEDICION_AMBIENTAL(#medicion, #pozo, valor_medicion, #parametro, fecha_medicion,
cuil_operario, #instrumento, nombre_parametro, valor_ref, descripcion_pozo,
fecha_perforacion, nombre_parametro, apellido_operario, nombre_operario, fecha_nacimiento,
marca_instrumento, modelo_instrumento, dominio_vehiculo, fecha_adquisicion)

Donde:

    ● Cada medición es realizada por un operario en un pozo, en una fecha determinada. En
    ella se miden varios parámetros, y para cada uno se obtiene un valor. Notar que un
    mismo parámetro (#parametro) puede ser medido en diferentes mediciones.
    Independientemente de las mediciones, todo parámetro tiene un nombre y valor de
    referencia, y el #parametro es único en el sistema.
  
    ● En cada medición se utilizan varios instrumentos, independientemente de los
    parámetros medidos. De cada instrumento se conoce la marca y modelo.
 
    ● De cada operario se conoce su cuit, nombre, apellido y fecha de nacimiento.
 
    ● La empresa cuenta con vehículos, y de cada uno se conoce la fecha en la que fue
    adquirido. El dominio (patente) de cada vehículo es único en el sistema.
  
    ● Un pozo tiene una descripción y una fecha de perforación. El identificador #pozo es único en el sistema.'


* DF1: #medicion --> #pozo,cuil_operario,fecha_medicion
* DF2: #pozo --> descripcion_pozo,fecha_perforacion
* DF3: #medicion,#parametro --> valor_medicion
* DF4: cuil_operario --> nombre_operario, apellido_operario,fecha_nacimiento
* DF5: dominio_vehiculo --> fecha_adquisicion
* DF6: #parametro --> nombre_parametro,valor_referencia
* DF7: #intrumento --> marca_intrumento,modelo_intrumento

* CC {**#medicion,#parametro,#intrumento,dominio_vehiculo**}

# Iteracion 1

MEDICION_AMBIENTAL no esta en BCNF y podemos ver que tenemos varias DF de las cuales X no es superclave, por lo que usamos DF4 para particionar en 2 tablas F1,F2

F1(**cuil_operario**,nombre_operario,apellido_operario,fecha_nacimiento)

F2(**#medicion, #parametro , #instrumento, dominio_vehiculo**, valor_medicion, #pozo, fecha_medicion,
cuil_operario, valor_referencia, descripcion_pozo,fecha_perforacion, nombre_parametro,marca_instrumento, modelo_instrumento, fecha_adquisicion)

Si realizamos F1 ⋂ F2 --> ** cuil_operario** es super clave de F1 por lo que no se pierde informacion
En F2 valen DF1,DF2,DF3,DF5,DF6,DF7.No se pierden dependecias funcionales

# Iteracion 2

F1 se encuentra en BCNF puesto que en la DF4 'X' es superclave del esquema

F2 no se encuentra en BCNF y podemos ver que tenemos varias DF de las cuales X no es superclave 

Particionamos F2 usando la DF5 'dominio_vehiculo' --> fecha_adiquisicion

F3(**dominio_vehiculo**,fecha_adquisicion)
F4(**#medicion, #parametro , #instrumento, dominio_vehiculo**, valor_medicion,#pozo, fecha_medicion,
cuil_operario, valor_referencia, descripcion_pozo,fecha_perforacion, nombre_parametro,marca_instrumento, modelo_instrumento)

Si realizamos F3 ⋂ F4 --> **dominio_vehiculo** es superclave de F3 por lo que no se pierde informacion
En F4 valen DF1,DF2,DF3,DF6,DF7.No se pierden dependecias funcionales

# Iteracion 3

F3 se encuentra en BCNF puesto que en la DF5 'X' es superclave del esquema

F4 no se encuentra en BCNF y podemos ver que tenemos aun varias DF de las cuales 'X ' no es superclave

Particionamos F4 usando la DF6 '#parametro --> nombre_parametro,valor_referencia'

F5(**#parametro**,nombre_parametro,valor_referencia)
F6(**#medicion, #parametro, #instrumento, dominio_vehiculo**, valor_medicion,#pozo, fecha_medicion,
cuil_operario, descripcion_pozo,fecha_perforacion,marca_instrumento modelo_instrumento)

Si realizamos F5 ⋂ F6 --> **#parametro** es superclave de F5 por lo que no se pierde informacion
En F6 valen DF1,DF2,DF3,DF7.No se pierden dependecias funcionales

# Iteracion 4

F5 se encuentra en BCNF puesto que en la DF6 'X' es superclave del esquema
F6 no se encuentra en BCNF y podemos ver que quedan DF de las cuales 'X' no es superclave

Particionamos F6 usando la DF7 #intrumento --> marca_intrumento,modelo_intrumento

F7(**#intrumento**,marca_instrumento,modelo_intrumento)
F8(**#medicion, #parametro, #instrumento, dominio_vehiculo**, valor_medicion,#pozo, fecha_medicion,
cuil_operario, descripcion_pozo,fecha_perforacion)

Si realizamos F7 ⋂ F8 --> #intrumento es superclave F7 por lo que no perdemos informacion
En F8 valen DF1,DF2,DF3.No se pierden dependecias funcionales

# Iteracion 5 

F7 se encuentra en BCNF puesto que en la DF7 'X' es superclave del esquema
F8 no se encuentra en BCNF y podermo ver que quedan DF de las cuales 'X' no es superclave

Particionamos F8 usando la DF2 #pozo --> descripcion_pozo,fecha_perforacion

F9(**#pozo**, descripcion_pozo,fecha_perforacion)
F10(**#medicion, #parametro, #instrumento, dominio_vehiculo**, valor_medicion,#pozo, fecha_medicion,
cuil_operario)

F9 ⋂ F10 --> #pozo es superclave de F9 por lo que no perdemos informacion
En F10 valen DF1,DF3. No se pierden dependecias funcionales

# Iteracion 6

F9 se encuentra en BCNF puesto que en la DF2 'X' es superclave del esquema

F10 no se encuentra en BCNF puesto que seguimos encontrando DF de las cuales 'X' no es superclave

Particionamos F10 usando la DF1 #medicion --> #pozo,cuil_operario,fecha_medicion 

F11(**#medicion**, #pozo,cuil_operario,fecha_medicion)
F12(**#medicion, #parametro, #instrumento, dominio_vehiculo**, valor_medicion)

Si realizamos F11 ⋂ F12 --> #medicion es superclave de F11 por lo que no perdemos informacion
En F10 valen DF3. No se pierden dependecias funcionales

# Iteracion 7

F11 se encuentra en BCNF puesto que en la DF1 'X' es superclave del esquema
F12 no se encuentra en BCNF puesto que nos queda un DF la cual 'X' no es superclave

Particionamos F12 usando la DF3 #medicion,#parametro --> valor_medicion

F13(**#medicion,#parametro**,valor_medicion)
F14(**#medicion, #parametro, #instrumento, dominio_vehiculo**)

Si realizamos F13 ⋂ F14 --> #medicion,#parametro es superclave de F13 por lo que no perdemos informacion

Y con la ultima particion no da como resultado 7 tablas normalizadas a BCNF

F1,F3,F5,F7,F9,F11,F13 estan normalizadas a BCNF

F14 está en BCFN, puesto que tiene una DF **trivial**.

F1(**cuil_operario**,nombre_operario,apellido_operario,fecha_nacimiento)
F3(**dominio_vehiculo**,fecha_adquisicion)
F5(**#parametro**,nombre_parametro,valor_referencia)
F7(**#intrumento**,marca_instrumento,modelo_intrumento)
F9(**#pozo**, descripcion_pozo,fecha_perforacion)
F11(**#medicion**, #pozo,cuil_operario,fecha_medicion)
F13(**#medicion,#parametro**,valor_medicion)
F14(**#medicion, #parametro, #instrumento, dominio_vehiculo**)

* CC {**#medicion,#parametro,#intrumento,dominio_vehiculo**}


F14 aun asi no se encuentra en 4FN ya que tiene dos DMs no triviales

 1. #medicion >> #parametro
 2. #medicion >> #intrumento

Por lo tanto el esquema no se encuentra en 4FN 

Particionamos usando las DM 1 Y 2

F15(**#medicion, #parametro, dominio_vehiculo**)
F16(**#medicion, #instrumento, dominio_vehiculo**)

Resutlado final: 

    F1(**cuil_operario**,nombre_operario,apellido_operario,fecha_nacimiento)
    F3(**dominio_vehiculo**,fecha_adquisicion)
    F5(**#parametro**,nombre_parametro,valor_referencia)
    F7(**#intrumento**,marca_instrumento,modelo_intrumento)
    F9(**#pozo**, descripcion_pozo,fecha_perforacion)
    F11(**#medicion**, #pozo,cuil_operario,fecha_medicion)
    F13(**#medicion,#parametro**,valor_medicion)
    F14(**#medicion, #parametro, #instrumento, dominio_vehiculo**)
    F15(**#medicion, #parametro, dominio_vehiculo**)
    F16(**#medicion, #instrumento, dominio_vehiculo**)

Termino el proceso de normalizacion a 4FN con las siguientes particiones

# Ejercicio 8

8. FESTIVALES (#festival, denominacion_festival, localidad, cuil_musico, nombre_musico, fecha_nacimiento, #banda, nombre_banda estilo_musical, #tema, nombre_tema, duracion, instrumento, cuil_auspiciante, url_plataforma_entradas, #sponsor)


Donde:

    ● Para cada festival se conoce su denominación y la localidad en la que se realiza. Más de un festival podría tener la misma denominación.

    ● De cada banda se conoce su nombre y estilo musical.

    ● De cada músico se conoce su cuil, nombre y su fecha de nacimiento. Tenga en cuenta que varios músicos podrían tener el mismo nombre.

    ● Para cada tema interpretado por una banda en un festival se conoce su nombre y
    duración. Además, de cada músico que participó en el tema se sabe con qué
    instrumento lo hizo.

    ● Los #tema pueden repetirse para las distintas bandas.

    ● Un festival puede tener varios auspiciantes, y se vendieron entradas al mismo a través
    de varias plataformas.

    ● Se tiene además un registro de todas los sponsors que han participado de los distintos
    festivales realizados.

* DF1: #festival --> denominacion_festival,localidad
* DF2: #banda --> nombre_banda,estilo_musical
* DF3: cuil_musico --> nombre_musico,fecha_nacimiento
* DF4: #tema,#banda,#festival --> nombre_tema,duracion
* DF5: #tema,#musico --> instrumento

CC `{**#festival,#banda,#tema,cuil_musico,cuil_auspiciantes,url_plataforma_entradas,#sponsor**}`

# Iteracion 1

FESTIVALES no se encuentra en BCNF ya que tiene varias DF de las cuales 'X' no son superclaves por lo que particionamos FESTIVALES en F1,F2 siguiendo la DF3 cuil_musico --> nombre_musico,fecha_nacimiento

F1(**cuil_musico**,nombre_musico,fecha_nacimiento)
F2(#festival, denominacion_festival, localidad, cuil_musico, #banda, nombre_banda estilo_musical, #tema, nombre_tema, duracion, instrumento, cuil_auspiciante, url_plataforma_entradas, #sponsor)

Si realizamos F1 ⋂ F2 --> **cuil_musico** es superclave de F1 por lo que no perdemos informacion
En F2 valen DF1,DF2,DF4,DF5. No se pierden dependecias funcionales

# Iteracion 2

F1 se encuentra en BCNF puesto que en la DF3 'X' es superclave del esquema
F2 no se encuentra en BCNF ya que todavia tiene DF de las cuales 'X' no son superclaves

Particionamos F2 usando DF2 #banda --> nombre_banda,estilo_musical

F3(**#banda**,nombre_banda,estilo_musical)
F4(#festival, denominacion_festival, localidad, cuil_musico, #banda, #tema, nombre_tema, duracion, instrumento, cuil_auspiciante, url_plataforma_entradas, #sponsor)

Si realizamos F3 ⋂ F4 --> **#banda** es superclave de F3 por lo que no perdemos informacion
En F4 valen DF1,DF4,DF5. No se pierden dependecias funcionales

# Iteracion 3

F3 se encuentra en BCNF puesto que en la DF2 'X' es superclave del esquema
F4 no se encuentra en BCNF ya que todavia encontramos DF de las cuales 'X' no son superclaves

Particionamos F4 usando la DF1 #festival --> denominacion_festival,localidad

F5(**#festival**,denominacion_festival,localidad)
F6(#festival, #banda, #tema, nombre_tema, duracion, instrumento, ,cuil_auspiciantes,url_plataforma_entradas,#sponsor)

Si hacemos F5 ⋂ F6 --> **#festival** es superclave de F5 por lo que no perdemos informacion
En F6 valen DF4 Y DF5. No se pierden dependecias funcionales

# Iteracion 4 

F5 se encuentra en BCNF puesto que en la DF1 'X' es superclave del esquema
F6 no se encuentra en BCNF ya que presenta todavia DFs de las cuales 'X' no son superclaves

Particionamos F6 usando la  DF4: #tema,#banda,#festival --> nombre_tema,duracion

F7(**#tema,#banda,#festival**,nombre_tema,duracion)
F8(#festival, #banda, #tema, instrumento ,cuil_auspiciantes,url_plataforma_entradas,#sponsor)

Si hacemos F7 ⋂ F8 --> #tema,#banda,#festival es superclave de F7 por lo que no perdemos informacion
En F8 valen DF5. Por validacion simple no se pierden DF

# Iteracion 5

F7 se encuentra en BCNF puesto que en la DF4 'X' es superclave del esquema
F8 no se encuetra en BCNF ya que presenta una DF de la cual 'X' no es superclave del esquema

Particionamos F8 usando la DF5 #tema,#musico --> instrumento

F9(**#tema,#musico**,instrumento)
F10(#festival, #banda, #tema ,cuil_auspiciantes,url_plataforma_entradas,#sponsor)

Si hacemos F9 ⋂ F10 --> **#tema,#musico** es superclave de F9 por lo que no perdemos informacion
En F9 vale DF5 y F10 esta normalizada a BCNF ya que presenta un DF trivial

Como resultado obtenemos 6 tablas normalizadas a BCNF


Resultado:

    F1(**cuil_musico**,nombre_musico,fecha_nacimiento)
    F3(**#banda**,nombre_banda,estilo_musical)
    F5(**#festival**,denominacion_festival,localidad)
    F7(**#tema,#banda,#festival**,nombre_tema,duracion)
    F9(**#tema,#musico**,instrumento)
    F10(#festival, #banda, #tema ,cuil_auspiciantes,url_plataforma_entradas,#sponsor)


CC `{**#festival,#banda,#tema,cuil_musico,cuil_auspiciantes,url_plataforma_entradas,#sponsor**}

#### Normalizacion a 4FN

Dependencias Multivaluadas:

1. festival >> cuil_auspiciantes
2. festival >> url_plataforma_entrandas
3. {} >> sponsor o ??? (festival >> sponsor)

Analisis

F10 no esta en 4FN ya que presenta dependencias multivaluadas no triviales

Particionamos usando DM3 

F11(#sponsor)
F12(#festival, #banda, #tema ,cuil_auspiciantes,url_plataforma_entradas)

F12 sigue sin estar en 4FN ya que tiene dependnecias multivaluadas no triviales

Particionamos usando DM1 y DM2

F13(#festival, #banda, #tema ,cuil_auspiciantes)
F14(#festival, #banda, #tema ,url_plataforma_entradas)

F13 Y F14 estan en la 4FN ya que bi valen dependencias multivaluadas que no sean triviales

#### Esquema final resultante

    F1(**cuil_musico**,nombre_musico,fecha_nacimiento)
    F3(**#banda**,nombre_banda,estilo_musical)
    F5(**#festival**,denominacion_festival,localidad)
    F7(**#tema,#banda,#festival**,nombre_tema,duracion)
    F9(**#tema,#musico**,instrumento)
    F11(#sponsor)
    F13(#festival, #banda, #tema ,cuil_auspiciantes)
    F14(#festival, #banda, #tema ,url_plataforma_entradas)

No se encuentran dependencias multivaluadas no triviales. 

# Ejercicio 9

9. TORNEOS (#torneo, nombre_torneo, año, #equipo, nombre_equipo, estadio_equipo, puesto,
#reglamentacion, descripcion, #auspiciante)

    ● De cada torneo, se conoce su identificador (#torneo, único en el sistema) y un nombre. Un mismo torneo tiene diferentes ediciones, cada edición se realiza en un año determinado y el mismo torneo no puede repetirse el mismo año. En un año pueden
    realizarse varios torneos.

    ● Cada edición de un torneo tiene diferentes auspiciantes, identificados por #auspiciante
    (único en el sistema).

    ● En cada edición de un torneo participan varios equipos. De cada equipo se conoce su nombre, su estadio y su #equipo, que no se repite para diferentes equipos.

    ● Cada equipo finaliza una edición de un torneo en un puesto. Dos o más equipos no pueden finalizar en un mismo puesto.

    ● Además, se conoce un conjunto de reglamentaciones, identificadas por #reglamentación, aplicables a estos torneos.


* DF1: #torneo --> nombre_toreno,#reglamentacion
* DF2: #equipo --> nombre_equipo,estadio_equipo
* DF3: #torneo,#equipo,año --> puesto
* DF4: #reglamentacion --> descripcion

CC `{#toreno,#equipo,año,#auspiciante}`

