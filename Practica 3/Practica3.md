

### Resolver los siguientes ejercicios aplicando las operaciones del álgebra relacional vistas 
en la materia:


    · Selección σ 
    · Proyección π 
    · Producto Cartesiano  X 
    · Producto Natural  |X| 
    · Diferencia o Resta  – 
    · Intersección ∩ 
    · Unión ∪ 
    · División  % 
    · Renombre ρ 
  
 
### PARTE I 
 
### 1)  Indique las opciones correctas: 
 
#### A) Indique cuáles de las siguientes operaciones son válidas: 

    [ ] A(a,b,c) U B(a,b,d) 
    [ ] ( A(a,b,c) |X| B(a,b) ) - C(a,b,c) 
    [x] ( A(a,b,c) |X| B(a,d,e) ) ∩ D(a,b,c,d,e) 
    [x] ( A(a,b,c) X B (a,b,d) ) ∩ D(a,b,c,d)  
 

#### B) Para la operación de resta es necesario que los esquemas involucrados sean 
compatibles, es decir, deben cumplir las siguientes condiciones:

    [x] Deben tener la misma cantidad de columnas 
    [x] Las columnas deben ser del mismo dominio 
    [x] El orden de los columnas debe ser el mismo 
    [ ] Las columnas deben tener igual nombre 
 
 
### 2)  ¿Para cuáles de las siguientes operaciones es necesario que los operandos sean union compatibles? Marque todas las opciones correctas: 

    [x] resta - 
    [ ] división % 
    [x] unión U 
    [ ] producto cartesiano X 
    [ ] producto natural |X| 
 
### 3)  Dados los siguientes esquemas 
 
    COMPRA(#compra, fecha, monto_total) 
    COMPRA_PRODUCTO(#compra, cantidad, #producto) 
    PRODUCTO(#producto, nombre, precio) 
 
#### Indique qué formato (conjunto de atributos) tiene el resultado de aplicar la siguiente operación. 
 
    COMPRA_PRODUCTO % ∏#productoPRODUCTO 
 
    [x] (#compra, cantidad) 
    [ ] (#compra, cantidad, #producto) 
    [ ] (#compra) 

 

### 4) Dado el siguiente esquema: 
 
    PASAJERO (#pasajero, nombre, dni, puntaje) 
    PASAJERO_RESERVA (#pasajero, #reserva) 
    RESERVA (#reserva, #vuelo, fecha_reserva, monto, #asiento) 
    VUELO (#vuelo, aeropuerto_salida, aeropuerto_destino, fecha_vuelo) 
 
#### Indicar si las siguientes consultas obtienen el resultado correcto (sin importar la  optimización). 
 
#### A)  Obtener los pasajeros que tengan reservas sobre vuelos del próximo año, listando #pasajero, #vuelo y #asiento. 

    VUELOS_PROX_AÑO <— σ fecha_vuelo >= 1/1/2024 AND fecha_vuelo <= 31/12/2024 VUELO 

    RES <— Π #pasajero,#vuelo,#asiento ( VUELOS_PROX_AÑO |X| RESERVA |X| PASAJERO_RESERVA) 

    RES = (#vuelo, aeropuerto_salida, aeropuerto_destino, fecha_vuelo, #reserva, #vuelo, fecha_reserva, monto, #asiento,#pasajero) 
si se obtienen los pasajeros
 
#### B) Obtener el listado de montos de reservas realizadas para vuelos efectuados el pasado Agosto desde Buenos Aires a Córdoba. 

    VUELOS_BUE_CBA <— σ ciudad_salida=“Buenos Aires” AND ciudad_destino=“Córdoba” VUELO 
    RESERV_AGO <— ( σ fecha_reserva >= 1/8/2024 AND fecha_reserva <= 31/8/2024 RESERVA) |X| VUELOS_BUE_CBA 
    RES <— Π monto RESERV_AGO 

No se obtiene las reservas ciudad_destino y ciudad_salida no existen
 

#### C) Obtener el/los pasajeros que solo hayan reservado vuelos cuyo aeropuerto de salida sea el aeropuerto “Ministro Pistarini”. Listar el nombre y dni de los pasajeros. 

    VUELOS_PISTARINI <-  Π #vuelo (σ aeropuerto_salida=“Ministro Pistarini” VUELO ) 
    RESERVA_PISTARINI <-  Π #pasajero (VUELOS_PISTARINI |X| RESERVA) 
    PASAJEROS_PISTARINI <-  Π nombre,dni (RESERVA_PISTARINI |X| PASAJERO) 

No obtiene los nombre y dni porque falta hacer el producto natural de pasajero_reserva.


#### D) Obtener el/los id/s de los pasajeros que hayan realizado reservas por un monto superior a $99000 

    RESERVAS_MAS_99000 <- Π #pasajero (σ monto < 99000 RESERVA ) 

Esto obtiene todas las reservas pero no los pasajeros


### Parte II: Para cada uno de los esquemas dados, resolver las consultas pedidas: 
 
### 6) Choferes 
 
    DUEÑO ( id_dueño, nombre, teléfono, dirección, dni ) 
    CHOFER ( id_chofer, nombre, teléfono, dirección, fecha_licencia_desde, 
    fecha_licencia_hasta, dni ) 
    AUTO ( patente, id_dueño, id_chofer, marca, modelo, año ) 
    VIAJE ( patente, hora_desde, hora_hasta, origen, destino, tarifa, metraje ) 
  
#### a) Listar el dni, nombre y teléfono de todos los dueños que NO son choferes 


    NO_CHOFERES <- Π dni, nombre, teléfono (DUEÑO) - Π dni, nombre, teléfono (CHOFER)



#### b) Listar la patente y el id_chofer de todos los autos a cuyos choferes les caduca la licencia el 01/01/2024 
 
    CHOFERES_VENCIMIENTO <- σ fecha_licencia_hasta=01/01/2024(CHOFER) 
    AUTOS_VENCIDOS <- Π patente, id_chofer (AUTO |X| CHOFERES_VENCIMIENTO)


### 7) Estudiantes y carreras 
 
    ESTUDIANTE ( #legajo, nombreCompleto, nacionalidad, añoDeIngreso, códigoDeCarrera ) 
    CARRERA ( códigoDeCarrera, nombre ) 
    INSCRIPCIONAMATERIA ( #legajo, códigoDeMateria ) 
    MATERIA ( códigoDeMateria, nombre ) 
  
#### a) Obtener el nombre de los estudiantes que ingresaron en 2019. 
 
    RES <- Π nombreCompleto (σ añoDeIngreso = 2019 (ESTUDIANTE))

#### b) Obtener el nombre de los estudiantes con nacionalidad “Argentina” que NO estén en la 
carrera con código “LI07” 

ArgentinosEnOtrasCarreras <- σ nacionalidad = 'Argentina' and códigoDeCarrera <> 'LI07' (ESTUDIANTE)


#### c) Obtener el legajo de los estudiantes que se hayan anotado en TODAS las materias. 
 
AnotadosEnTodas <- INSCRIPCIONAMATERIA % Π códigoDeMateria(MATERIA)


### 8) Cursos 
 
LUGAR_TRABAJO ( #empleado, #departamento ) 
CURSO_EXIGIDO ( #departamento, #curso ) 
CURSO_REALIZADO ( #empleado, #curso ) 
 
 
#### a) ¿Quiénes son los empleados que han hecho todos los cursos, independientemente de qué 
departamento los exija? 

TodosLosCursos <- (CURSO_REALIZADO) % Π #curso (CURSO_EXIGIDO)



#### b) ¿Quiénes son los empleados que ya han realizado todos los cursos exigidos por sus  departamentos? 


    CursosExigidos <- Π #empleado, #curso (LUGAR_TRABAJO |X| CURSO_EXIGIDO)
    TodosLosCursosExigidosPorDep <- Π #empleado (CURSO_REALIZADO % CursosExigidos)

Mal division, es -

Correcion 

    EmpleadoNecesitaCurso <- Π #empleado, #curso (Lugar_Trabajo |X| Curso_Exigido)
    EmpleadoFaltaCurso <- (EmpleadoNecesitaCurso - Curso_Realizado)
    EmpleadosQueHicieronTodos <- EmpleadoNecesitaCurso - EmpleadoFaltaCurso #PULIR


### 9) Fabricantes de Muebles 
 
    TIPOMUEBLE ( id_tipomueble, descripción ) 
    FABRICANTE ( id_fabricante,nombrefabricante, cuit ) 
    TIPOMADERA ( id_tipomadera, nombremadera ) 
    AMBIENTE ( id_ambiente, descripcionambiente ) 
    MUEBLE ( id_mueble, id_tipomueble, id_fabricante, id_tipomadera, precio, dimensiones, descripcion ) 
    MUEBLEAMBIENTE ( id_mueble, id_ambiente ) 
 
 
#### a.  Obtener los nombres de los fabricantes que fabrican muebles en todos los tipos de madera. 

    TodosFabriantes <- Π id_fabricante (Π id_fabricante,id_tipomadera MUEBLE % Π id_tipomadera (TIPOMADERA))
    RES <- Π nombrefabricante (FABRICANTE |X| TodosFabriantes )

#### b.  Obtener los nombres de los fabricantes que sólo fabrican muebles en Pino. 

    MaderaPino <- Π id_tipomadera (σ nombreMadrea = Pino (TIPOMADERA))
    MaderaDistintaPino <- Π id_tipomadera (σ nombreMadrea <> Pino (TIPOMADERA))
    FabricantesPino <- Π id_fabricante,nombrefabricante (FABRICANTE |X| MaderaPino)
    FabricantesDistintoPino <- Π id_fabricante,nombrefabricante (FABRICANTE |X|MaderaDistintaPino)
    FabricantesSoloPino <- Π nombrefabricante (FabricantesPino - FabricantesDistintoPino)

#### c.  Obtener los nombres de los fabricantes que fabrican muebles para todos los ambientes. 

    AmbientesMueble <- (MUEBLE |X| MUEBLEAMBIENTE)
    Π nombrefabricante FABRICANTE |X| (Π id_mueble, id_tipomueble, id_fabricante AmbientesMueble % Π id_ambiente AMBIENTE)

#### d.  Obtener los nombres de los fabricantes que sólo fabrican muebles para oficina. 

    MuebleOficina <- Π id_ambiente (σ descripcionambiente = Oficina (AMBIENTE))
    MuebleNoOficina <- Π id_ambiente (σ descripcionambiente <> Oficina (AMBIENTE ))
    FabricantesOficina <- Π id_fabricante,nombrefabricante (FABRICANTE |X| MuebleOficina)
    FabricantesDistintoOficina <- Π id_fabricante,nombrefabricante (FABRICANTE |X| MuebleNoOficina)
    FabricantesSoloOficina <- Π nombrefabricante (FabricantesOficina  - FabricantesDistintoOficina)


#### e.  Obtener los nombres de los fabricantes que sólo fabrican muebles para baño y cocina.

    LO mismo que F despue lo hago

#### f.  Obtener los nombres de los fabricantes que producen muebles de cedro y roble. 
    MaderaRoble <- Π id_tipomadera (σ nombreMadrea = roble (TIPOMADERA))
    MaderaCedro <- Π id_tipomadera (σ nombreMadrea = cedro (TIPOMADERA))
    FabricanteRoble <- Π id_fabricante,nombrefabricante(FABRICANTE |X| MaderaRoble)
    FabricanteCedro <- Π id_fabricante,nombrefabricante(FABRICANTE |X| MaderaCedro)
    Π nombrefabricante (FabricanteRoble ∩ FabricanteCedro)

#### g.  Obtener los nombres de los fabricantes que producen muebles de melamina o MDF

    MaderaMelamina <- Π id_tipomadera (σ nombreMadrea = melamina (TIPOMADERA))
    MaderaMDF <- Π id_tipomadera (σ nombreMadrea = MDF (TIPOMADERA))
    FabricanteMelamina <- Π id_fabricante,nombrefabricante(FABRICANTE |X| MaderaMelamina)
    FabricanteMDF  <- Π id_fabricante,nombrefabricante(FABRICANTE |X| MaderaMDF)
    Π nombrefabricante (FabricanteMelamina U FabricanteMDF)