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
 3. {} >> dominio_vehiculos
#FALTO DOMINIO DE LOS VEHIUCLOS REHACER

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
* DF5: #tema,#musico --> instrumento # MAL falta la banda y cuil_musico 

REHACER

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







*df1:* #sucursal → ciudad, telefono

*df2:* #empleado→ dni, nombre, fecha_ingreso, #sucursal

*df3:* dni → #empleado, nombre, fecha_ingreso, #sucursal

*df4:* #pago, #departamento → monto_pago, fecha_pago

*df5:* #honorario → descripcion_h, monto_h

df2 y df3 son equivalentes entre sí.


F8(#empleado,#departamento,#pago,#honorario)

1. #departamento >> #empleado
2. #deparamento >> #pago
3. {} >>  #honorario


F9(#honorario)
F10(#empleado,#departamento,#pago)



F10 FALTA 

F11(#departamento,#pago)
F12(#empleado,#departamento)



F1(#honorario,monto_h,desc_h)
F3(#sucursal,c,t)
F5(#pago,#deparamento,monto_pago,fecha_pago)
F7(#empleado,dni,nombre,fecha_ingreso,#sucursal)

F9(#deparamento,#pago)
F11(#honorario)
F13(#deparamento,#empleado)






P6(#emplado,dni)

DF2 #EMPLEADO -> DNI

Esta en BCNF puesto solo vale la DF2 de la cual su determinanto {#Empleado} es superclave del esquema P6

P7(#adawd,#dkal,#adkla)

P7 no esta en BCNF ya que existe al menos la dfx de la cual su determinante (#DETERMINANT) por lo que particinamos


P8 esta en BCNF puesto que no tiene df no triviales, de las cuales su determinantes no son superclave del esquema, en este caso no tiene df no triviales



TORNEOS (#torneo, nombre_torneo, año, #equipo, nombre_equipo, estadio_equipo, puesto,
#reglamentacion, descripcion, #auspiciante)

● De cada torneo, se conoce su identificador (#torneo, único en el sistema) y un nombre.
Un mismo torneo tiene diferentes ediciones, cada edición se realiza en un año
determinado y el mismo torneo no puede repetirse el mismo año. En un año pueden
realizarse varios torneos.
● Cada edición de un torneo tiene diferentes auspiciantes, identificados por #auspiciante
(único en el sistema).
● En cada edición de un torneo participan varios equipos. De cada equipo se conoce su
nombre, su estadio y su #equipo, que no se repite para diferentes equipos.
● Cada equipo finaliza una edición de un torneo en un puesto. Dos o más equipos no
pueden finalizar en un mismo puesto.
● Además, se conoce un conjunto de reglamentaciones, identificadas por
#reglamentación, aplicables a estos torneos.


Se analiza


DF1  #Torneo -> nombre_torneo
DF2  #Equipo -> nombre_equipo,estadio_equipo
DF3  #Torneo,Ano,Equipo -> Puesto
DF4  Puesto,Ano,#Torneo -> Equipo

CC{**#Torneo,#Equipo,Ano,#Auspiciante,#Reglamentacion,Desc_R**}
CC{**#Torneo,Ano,Puesto,#Auspiciante,#Reglamentacion,Desc_R**}

se elije la clave candidate {**#Torneo,#Equipo,Ano,#Auspiciante,#Reglamentacion,Desc_R**}

El esquema Torneo no se encuentra en BCNF puesto que existe la DF2, la cual es valida en el esquema y su determinante {#Equipo} no es superclave del esquema por lo tanto particionamos el esquema en 2 F1 Y F2 siguiendo DF2: #Equipo -> nombre_equipo,estadio_equipo

F1(#Equipo,nombre_equipo,estadio_equipo)
F2(#torneo, nombre_torneo, año, #equipo, puesto,#reglamentacion, descripcion, #auspiciante)

Si realizamos F1 V F2 -> {#Equipo}. #Esquipo es clave del esquema F1 por lo que no perdemos info
No se pierden df ya que en F1 valen DF2 y en F2 valen DF1,DF3,DF4

F1 esta en BCNF ya que solo vale la df2 y el determinante de la df2 es superclave del esquema

F2 no esta en BCNF puesto que tiene al menos el determinante de df1 no es superclave del esquema.
puesto particionamos el esquema en 2 F3 Y F4 siguiendo la DF1: #Torneo -> nombre_torneo

F3(#Torneo, nombre_torneo)
F4(#torneo, año, #equipo, puesto,#reglamentacion, descripcion, #auspiciante)

Si realizamos F3 V F4 -> {#Torneo}. #Torneo es clave del esquema F3 por lo que no perdemos info
No se pierden DF ya que en F3 valen DF1 y en F4 valen DF3,DF4

F3 esta en BCNF ya que solo vale la df1 y el determinante de la df1 es superclave del esquema

F4 No esta en BCNF puesto que tiene al menos el determinante de df3 no es superclave del esquema.
puesto que particionamos el esquema en 2 F5 Y F6 siguiendo la DF3: #Torneo,Ano,Equipo -> Puesto

F5(#Torneo,Ano,Equipo,Puesto)
F6(#torneo, año, #equipo,#reglamentacion, descripcion, #auspiciante)


F5 esta en bcnf ya que en ella solo valen DF3 Y DF4 cuyo determinantes: {#Torneo,Ano,Equipo},{#Torneo,Ano,Puesto} son superclaves de F5
si realizamos F5 V F6 -> {#Torneo,Ano,Equipo}. #Torneo,Ano,Equipo es clave del esquema F5 no se pierde informacion

F6 esta BNCF puesto que no tiene DF no triviales de las cuales su determinantes no son superclave del esquema, en este caso no tiene df no triviales

Resultado: 

F1(#Equipo,nombre_equipo,estadio_equipo)
F3(#Torneo, nombre_torneo)
F5(#Torneo,Ano,Equipo,Puesto)
F6(#torneo, año, #equipo,#reglamentacion, descripcion, #auspiciante)

Clave: {**#Torneo,#Equipo,Ano,#Auspiciante,#Reglamentacion,Desc_R**}


DM :

DM1: ANO,#TORNEO ->> #AUSPICIANTES
DM2: ANO,#TORNEO ->> #Equipo
DM3: {} ->> #reglamentacion
DM4: {} ->> desc


F6 esta en BCNF pero no esta en 4FN debido a que existe la DM1 la cual no es trivial por lo que particionamos usando DM1: ANO,#TORNEO ->> #AUSPICIANTES

F7(ANO,#TORNEO, #AUSPICIANTES) 
F8(#torneo, año, #equipo,#reglamentacion, descripcion)

F7 esta en 4FN ya que no valen dependecias multivaluadas que no sean triviales

F8 esta en BCNF pero no esta en 4FN debido a que existe la DM2 la cual no es trivial, por lo que particionamos usando DM2:DM2: ANO,#TORNEO ->> #Equipo

F9(ANO,#TORNEO, #Equipo)
F10(#torneo, año,#reglamentacion, descripcion)

F9 esta en 4FN ya que no valen dependecias multivaludas que no sean triviales

F10 esta en BCNF pero no esta en 4FN debido a que existe la DM3 la cual no es trivial, por lo que particionam,os usando DM3:{} ->> #reglamentacion




esquemas en 4fn:

F1(#Equipo,nombre_equipo,estadio_equipo)
F3(#Torneo, nombre_torneo)
F5(#Torneo,Ano,Equipo,Puesto)
F7(ANO,#TORNEO, #AUSPICIANTES) 
F9(ANO,#TORNEO, #Equipo)
F11(#reglamentacion)
F13(descripcion)
F14(#torneo, año)


esquemas sin proyeciones

F14 es una proyecion de F5,F7,F9 ya puede deducirse a travez de los atributos de ese esquema se elimina del mismo

resultado: 

F1(#Equipo,nombre_equipo,estadio_equipo)
F3(#Torneo, nombre_torneo)
F5(#Torneo,Ano,Equipo,Puesto)
F7(ANO,#TORNEO, #AUSPICIANTES) 
F9(ANO,#TORNEO, #Equipo)
F11(#reglamentacion)
F13(descripcion)















POLIZAS (#póliza,#cliente, cuil, nombre, dirección, teléfono, tipo_seguro, fecha_inicio, fecha_fin, #siniestro, fecha_denuncia, estado_siniestro,
#perito, #cuota, detalle_reparacion)

- De las pólizas se conoce un ID único (#póliza), un tipo de seguro, y las fechas de inicio y fin para el asegurado titular de la misma. Además se registran las cuotas pagas que le corresponden a las pólizas, cada uno identificada con #cuota, este es un número secuencial a partir de 1 por cada póliza.
- De los clientes se conoce un ID único (#cliente), su cuil, nombre, dirección y teléfono. Un cliente puede poseer varias pólizas. Una póliza pertenece a un único cliente
- De un siniestro se conoce un ID único (#siniestro), una fecha de denuncia y el estado (pendiente, en proceso, resuelto), Debe registrarse a su vez las pólizas asociadas al siniestro, ya que pueden estar involucrados más de un vehículo.
- Sobre cada siniestro distintos peritos (expertos en investigar el accidente) realizan una inspección, cada perito es identificado con un #perito.
- Sobre cada póliza involucrada en un siniestro se registran un conjunto de posibles reparaciones (detalle_reparación), los cuales son predefinidos, por lo que podrían repetirse.

DF
    DF1: #poliza -> tipo_seguro,fecha_inicio,fecha_fin,cuil
    DF2: #poliza -> tipo_seguro,fecha_inicio,fecha_fin,#cliente
    DF3: #cliente -> cuil,nombre,direccion,telefono
    DF4: cuil -> #cliente,nombre,direccion,telefono
    DF5: #Siniestro -> fecha_denuncia,estado_siniestro


    CC{#poliza,#siniestro,detalle_reparacion,#cuota,#perito}


Se analizan las dependecias funcionales:


POLIZAS no esta en BCNF porque existe al menos la DF5, la cual es valida en POLIZAS y su determinante {#Siniestro} no es superclave del esquema
por lo que particionamos el esquema en 2 F1 Y F2 siguiendo la DF5: #Siniestro -> fecha_denuncia,estado_siniestro

F1(**#Siniestro**,fecha_denuncia,estado_siniestro)
F2(#póliza,#cliente, cuil, nombre, dirección, teléfono, tipo_seguro, fecha_inicio, fecha_fin, #siniestro,
#perito, #cuota, detalle_reparacion)


F1 esta en BCNF ya que solo vale la DF5 de la cual su determinante {#Sinietro} es superclave del esquema
Si realizamos validacion simple: F1 V F2 -> {#Sinietro}.{#Siniestro} es clave del esquema F1 por lo que no perdemos informacion
F1 valen la DF5 y en F2 valen la DF1,DF2,DF3,DF4 por lo tante no se pierden dependecias funcionales

F2 no esta en BCNF porque existe al menos la DF3,la cual es valida en F2 y su determinante {#Cliente} no es superclave del esquema por lo que particionamos el esquema en 2 F3 Y F4
siguiendo la DF3: #cliente -> cuil,nombre,direccion,telefono

F3(#cliente,cuil,nombre,direccion,telefono)
F4(#póliza,#cliente, tipo_seguro, fecha_inicio, fecha_fin, #siniestro,
#perito, #cuota, detalle_reparacion)

F3 es tan BCNF porque solo valen la DF3 y DF4 (son equivalentes) de la cual sus determinantes {#Cliente},{cuil} son suprclave del esquema
Si realizamos validacion simple: F3 V F4 -> {#Cliente}. {#Cliente} es clave del esquema F3 por lo que no perdemos info 
F3 valen la DF3,DF4 y en F4 valen DF2
DF1 no es valida pero no se pierde ya que es posible acceder a sus determinantes con su determinando sea directa o inderectamente.

tipo_seguro,fecha_inicio,fecha_fin se pueden acceder directamente ya que estan en F4
cuil no esta en F4 sin embargo la DF no se pierde ya que existe una relacion indirecta con la DF2 #POLIZA -> #Cliente y DF3: #Cliente -> Cuil

DF1: #poliza -> tipo_seguro,fecha_inicio,fecha_fin,cuil

F4 no esta en BNCF porque existe al menos la DF1,la cual es valida en F4 y su determinante {#poliza} no es superclave del esquema por lo que particionamos el esquema en 2 F5 Y F6

F5(#poliza,tipo_seguro,fecha_inicio,fecha_fin,#cliente)
F6(#póliza,#siniestro,#perito, #cuota, detalle_reparacion)

F5 esta en BCNF porque solo vale la DF1 de la cual su determinante {#POLIZA} es superclave del esquema
Si realizamos validacion simple: F5 V F6 -> {#POLIZA}. {#Poliza} es clave del esquema F5 por lo que no perdemos info
F5 vale la DF1 

F6 esta en BCNF puesto que no tiene DF no triviales de las cuales su determinantes no son superclave del esquema, en este caso no tiene df no triviales

Esquemas en BCNF

F1(**#Siniestro**,fecha_denuncia,estado_siniestro)
F3(**#cliente**,cuil,nombre,direccion,telefono)
F5(**#poliza**,tipo_seguro,fecha_inicio,fecha_fin,#cliente)
F6(**#póliza,#siniestro,#perito, #cuota, detalle_reparacion**)

Clave: {#poliza,#siniestro,detalle_reparacion,#cuota,#perito}


DM:
    DM1: #POLIZA ->> #CUOTAS
    DM2: #POLIZA,#SINIESTRO ->> detalle_reparacion
    DM3: #SINESTRO ->> #perito

F6 esta en BCNF pero no esta en 4FNM debido a que existe la DM3 la cual no es trivial por lo que particionamos usando DM3:#SINESTRO ->> #perito

F7(**#SINESTRO**,#perito)
F8(**#póliza,#siniestro, #cuota, detalle_reparacion**)

F7 esta en 4FN ya que no valen dependencias multivaluadas que no sean triviles
    
F8 esta en BCNF pero no esta en 4FNM debido a que existe la DM2 la cual no es trivial por lo que particionamos usando DM2: #POLIZA,#SINIESTRO ->> detalle_reparacion

F9(**#POLIZA,#SINIESTRO**,detalle_reparacion)
F10(**#póliza,#siniestro, #cuota**)

F9 esta en 4FN ya que no valen dependencias multivaluadas que no sean triviles

F10 esta en BCNF pero no esta en 4FN debido a que existe la DM1 la cual no es trivial por lo que particionamos usando DM1: #POLIZA ->> #CUOTAS


F11(**#POLIZA**, #CUOTAS)
F12(**#póliza,#siniestro**)

F11 esta en 4FN ya que no valen dependencias multivaluadas que no sean triviles
F12 esta en 4FN ya que no valen dependencias multivaluadas que no sean triviles



Esquemas en 4FN

F1(**#Siniestro**,fecha_denuncia,estado_siniestro)
F3(**#cliente**,cuil,nombre,direccion,telefono)
F5(**#poliza**,tipo_seguro,fecha_inicio,fecha_fin,#cliente)
F7(**#SINESTRO**,#perito)
F9(**#POLIZA,#SINIESTRO**,detalle_reparacion)
F11(**#POLIZA**, #CUOTAS)
F12(**#póliza,#siniestro**)

Esquemas sin proyeciones

F12 es una proyeccion de F9 ya que puede deducirse atravez de los atributos del esquema. Se elimina F12

Resultado
F1(**#Siniestro**,fecha_denuncia,estado_siniestro)
F3(**#cliente**,cuil,nombre,direccion,telefono)
F5(**#poliza**,tipo_seguro,fecha_inicio,fecha_fin,#cliente)
F7(**#SINESTRO**,#perito)
F9(**#POLIZA,#SINIESTRO**,detalle_reparacion)
F11(**#POLIZA**, #CUOTAS)






















EXAMEN 2DA FECHA


PARQUEDIVERSIONES(id_atracitvo,nombre_atractivo,desc_atractivo,id_categoria_actractivo,nombre_categoria,cuil_empleado,nombre_apellido_empleado,nro_legajo_empleado,dia_semana,id_agente_mantenimineto)


    df1 : id_atractivo -> nombre_atractivo,desc_atravito
    df2 : id_categoria_actractivo -> nombre_categoria
    df3 : cuil_empleado -> nombre_apellido_empleado,nro_legajo_empleado
    df4 : nro_legajo_empleado -> nombre_apellido_empleado,cuil_empleado
    df5 : id_atractivo,cuil_empleado -> dia_semana
    df6 : id_atractivo,nro_legajo_empleado -> dia_semana



CC1{**id_atractivo,id_categoria_atractivo,cuil_empleado,id_agente_mantenimineto**}
CC2{**id_atractivo,id_categoria_atractivo,nro_legajo_empleado,id_agente_mantenimineto**}

Se analiza las dependecias funcionales para saber si cumplen la definicion de BCNF

PARQUEDIVERSIONES esta en BNCF? -> NO {PARQUEDIVERSIONES} no esta en bcnf porque existe al menos la DF1 la cual es valida en el esquema {PARQUEDIVERSIONES} y su determinante {id_atractivo} no es superclave del esquema por lo que particionamos el esquema PARQUEDIVERSIONES en P1 Y P2 siguiendo la DF1.

P1(**id_atractivo**,nombre_atractivo,desc_atravito)
P2(**id_atracitvo**,**id_categoria_actractivo**,nombre_categoria,**cuil_empleado**,nombre_apellido_empleado,**nro_legajo_empleado***,dia_semana,**id_agente_mantenimineto**)

P1 esta en BCNF ya que solo vale la DF1 de la cual su determinante {id_atractivo} es superclave del esquema
Si realizamos Validacion simple P1 ' P2 -> {id_atractivo}, {id_atractivo} es clave del esquema P1 por lo que no perdemos informacion
P1 valen la df1 y en P2 valen la df2,df3,df4,df5,df6 por lo que no se pierden defendecias funcionales


P2(**id_atracitvo**,**id_categoria_actractivo**,nombre_categoria,**cuil_empleado**,nombre_apellido_empleado,**nro_legajo_empleado***,dia_semana,**id_agente_mantenimineto**)

P2 no esta en BCNF puesto que existe al menos la df2 la cual es valida en el esquema P2 y su determinante {id_categoria_actractivo} no es superclave del esquema por lo que particionamos P2 en P3 Y P4 siguiendo la DF2

P3(**id_categoria_actractivo**,nombre_categoria)
P4(**id_atracitvo**,**id_categoria_actractivo**,**cuil_empleado**,nombre_apellido_empleado,**nro_legajo_empleado***,dia_semana,**id_agente_mantenimineto**)

P3 esta en BCNF ya que solo vale la DF2 de la cual su determinante {id_categoria_actracitvo} es superclave del esquema
Si realizamos validacion simple P3 ' P4 -> id_categoria_actracitvo, entonces id_categoria_actracitvo  es clave del  esuqema P3 por lo que no perdemos informacion
En P3 valen DF2 y en P4 valen DF3,DF4,DF5,DF6 por lo que no se pierden dependencias funcionales


P4(**id_atracitvo**,**id_categoria_actractivo**,**cuil_empleado**,nombre_apellido_empleado,**nro_legajo_empleado***,dia_semana,**id_agente_mantenimineto**)

No esta en BCNF porque existe al menos la DF5 la cual es valida en el esquema P4 y su determinanate {id_atractivo,cuil_empleado} no es superclave del esquema por lo que particionamos por P5 Y P6 siguiendo la df5

P5(**id_atractivo,cuil_empleado**, dia_semana)
P6(**id_atracitvo**,**id_categoria_actractivo**,**cuil_empleado**,nombre_apellido_empleado,**nro_legajo_empleado***,**id_agente_mantenimineto**)

P5 esta en BCNF ya que solo vale la DF5 la cual su determinante {id_atractivo,cuil_empleado} es superclave del esquema 
Si realizamos validacion simple P5 ' P6 -> id_atractivo,cuil_empleado , entonces id_atractivo,cuil_empleado es clave del esquema P5 por lo que no se pierde informacion
En P5 valen la DF5 y P6 valen DF3,DF4

que paso con DF6?

La DF6 no es valida pero no se pierde ya que se puede acceder a todo sus determinados con su determinante sea directa o indirectamente
Siguiendo la DF3 la cual es valida puede determinar el nro_legajo_empleado y con ese nro_legajo_empleado puedo obtener el dia de la semana


P6 no esta en BCNF puesto que existe al menos la df3 la cual es valida en el esquema P6 y su determinante {cuil_empleado} no es superclave del esquema por lo que particionamos P6 en P7 Y P8 siguiendo la DF3

P7(**cuil_empleado**, nombre_apellido_empleado,nro_legajo_empleado)
P8(**id_atracitvo,id_categoria_actractivo,cuil_empleado,id_agente_mantenimineto**)

P7 esta en BNCF ya que solo vale la DF3 la cual su determinante {cuil_empleado} es superclave del esquema
Si realizamos validacion simple P7 ' P8 -> cuil_empleado , entonces cuil_empleado es  clave del esquema P7 por lo que no se pierde inforamcion
P7 valen la DF3 y en P8?
En P8 no es valida la DF4 pero no se pierde ya que es posible acceder a todo sus determinados con su determinate sea directa o indirectamente
{nombre_apellido_empleado,cuil_empleado} no esta en P8 pero se lo puede acceder mediante la P7 ya que existe una realcion indirecta con la DF4 decimos que {cuil_empleado} -> {nro_legajo_empleado} y {nro_legajo_empleado} -> {cuil_emplado}

P8 esta en BCNF ya que no tiene dependencias funcionales no triviales de las cuales sus determinantes no son supercalve del esquema, en este caso no tiene df no triviles

Esquemas en BCNF:

P1(**id_atractivo**,nombre_atractivo,desc_atravito)
P3(**id_categoria_actractivo**,nombre_categoria)
P5(**id_atractivo,cuil_empleado**, dia_semana)
P7(**cuil_empleado**, nombre_apellido_empleado,nro_legajo_empleado)
P8(**id_atracitvo,id_categoria_actractivo,cuil_empleado,id_agente_mantenimineto**)

CC1{**id_atractivo,id_categoria_atractivo,cuil_empleado,id_agente_mantenimineto**}


4FN
Dependecias multivaluadas 
DM1: {} ->> id_agente_mantenimiento
DM2: id_atracitvo ->> cuil_empleado 
DM3: id_atracitvo ->> id_categoria_atractivo

P8 esta en BCNF pero no esta en 4FN debido que existe la DM1 la cual no es trivial por lo que particionamos usando DM1:{} ->> id_agente_mantenimiento

P9(**id_agente_mantenimiento**)
P10(**id_atracitvo,id_categoria_actractivo,cuil_empleado**)

P9 esta en 4FN ya que no valen dependecias multivaluadas que no sean triviales

P10 esta en BCNF pero no esta en 4FN debido que existe la DM2 la cual no es trivial por lo que particionamos usando DM2:id_atracitvo ->> cuil_empleado 

P11(**id_atracitvo**cuil_empleado )
P12(**id_atracitvo,id_categoria_actractivo**)

P11 esta en 4FN ya que no valen dependecias multivaluadas que no sean triviales

Al particionar P10 por la DM2 en P12 termina quedando 4FN ya que la DM3 y no valen dependecias multivaluadas que no sean triviales

P1(**id_atractivo**,nombre_atractivo,desc_atravito)
P3(**id_categoria_actractivo**,nombre_categoria)
P5(**id_atractivo,cuil_empleado**, dia_semana)
P7(**cuil_empleado**, nombre_apellido_empleado,nro_legajo_empleado)
P9(**id_agente_mantenimiento**)
P11(**id_atracitvo**cuil_empleado )
P12(**id_atracitvo,id_categoria_actractivo**)

CC1{**id_atractivo,id_categoria_atractivo,cuil_empleado,id_agente_mantenimineto**}

No se encuentran dependecias multivaluadas que no sean triviales en el esquema por lo esta en 4FN

Proyecciones

P11 es una proyeccion de P5 ya que puede deducise las atributos de ese esquema. Se elimina P11

P1(**id_atractivo**,nombre_atractivo,desc_atravito)
P3(**id_categoria_actractivo**,nombre_categoria)
P5(**id_atractivo,cuil_empleado**, dia_semana)
P7(**cuil_empleado**, nombre_apellido_empleado,nro_legajo_empleado)
P9(**id_agente_mantenimiento**)
P12(**id_atracitvo,id_categoria_actractivo**)

CC1{**id_atractivo,id_categoria_atractivo,cuil_empleado,id_agente_mantenimineto**}

Resultado final.