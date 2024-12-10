


2. Hallar aquellos pacientes que para todas sus consultas médicas siempre hayan
dejado su número de teléfono primario (nunca el teléfono secundario).

```sql

    SELECT patient_id,patient_name FROM PATIENT p2
    WHERE NOT EXISTS(
        SELECT p.patient_id,p.patient_name FROM PATIENT p 
        INNER JOIN APPOINTMENT a on p.patient_id = a.patient_id
        WHERE a.contact_phone = p.secondary_phone
    );

```


3. Crear una vista llamada ‘doctors_per_patients’ que muestre los id de los pacientes y
los id de doctores de la ciudad donde vive el cliente.
```sql


    CREATE VIEW doctors_per_patients as (
        SELECT patient_id, doctor_id FROM PATIENT  
        INNER JOIN DOCTOR on patient_city = doctor_city
    )

```


PATIENT(patient_id,patient_name,patient_address,patient_city,primary_phone,
secondary_phone)
DOCTOR(doctor_id,doctor_name,doctor_address,doctor_city,doctor_speciality)
APPOINTMENT(patient_id,appointment_date,appointment_duration,contact_phone,
observations,payment_card)
MEDICAL_REVIEW(patient_id,appointment_date,doctor_id)
PRESCRIBED_MEDICATION(patient_id,appointment_date,medication_name)

4. Hallar los pacientes (únicamente es necesario su id) que se atendieron con todos los
doctores de la ciudad en la que viven


```sql

    SELECT p.patient_id FROM PATIENT p
    INNER JOIN MEDICAL_REVIEW mr on mr.patient_id = p.patient_id
    INNER JOIN DOCTOR d on d.doctor_city = p.patient_city
    GROUP BY patient_id
    HAVING COUNT(DISTINCT d.doctor_id) = (
        SELECT doctor COUNT(*) FROM DOCTOR 
        WHERE doctor_city = p.patient_city
    )

    

```
a. Realice la consulta sin utilizar la vista creada anteriormente
```sql

    SELECT patient_id FROM 
    doctors_per_patients
    GROUP BY patient_id
    HAVING COUNT(DISTINCT d.doctor_id) = (
        SELECT doctor COUNT(*) FROM DOCTOR 
        WHERE doctor_city = p.patient_city
    )


```

b. Realice la consulta utilizando la vista creada anteriormente
Restricción: resolver este ejercicio sin usar la cláusula “NOT EXIST”.
5. Agregar la siguiente tabla:
APPOINTMENTS_PER_PATIENT
idApP: int(11) PK AI
id_patient: int(11)
count_appointments: int(11)
last_update: datetime
user: varchar(16)
6. Crear un Stored Procedure que realice los siguientes pasos dentro de una
transacción:
a. Realizar una consulta que para cada pacient (identificado por id_patient),
calcule la cantidad de appointments que tiene registradas. Registrar la fecha
en la que se realiza esta carga y además del usuario con el se realiza.
b. Guardar el resultado de la consulta en un cursor.
c. Iterar el cursor e insertar los valores correspondientes en la tabla
APPOINTMENTS PER PATIENT.
7. Crear un Trigger de modo que al insertar un dato en la tabla Appointment, se
actualice la cantidad de appointments del paciente, la fecha de actualización y el
usuario responsable de la misma (actualiza la tabla APPOINTMENTS PER
PATIENT).
8. Crear un stored procedure que sirva para agregar un appointment, junto el registro
de un doctor que lo atendió (medical_review) y un medicamento que se le recetó
(prescribed_medication), dentro de una sola transacción. El stored procedure debe
recibir los siguientes parámetros: patient_id, doctor_id, appointment_duration,
contact_phone, appointment_address, medication_name. El appointment_date será
la fecha actual. Los atributos restantes deben ser obtenidos de la tabla Patient (o
dejarse en NULL).
9. Ejecutar el stored procedure del punto 9 con los siguientes datos:
patient_id: 10004427
4
