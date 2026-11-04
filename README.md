# Modelo Relacional de Bases de Datos



## Descripción



Este documento detalla el esquema y la estructura del modelo relacional de bases de datos para el sistema médico corregido (foco en especialidades, médicos, pacientes, turnos y medicamentos).

---

## Estructura de Tablas y Atributos



### 1. Especialidad



* **PK (Clave Primaria):** `id_especialidad`


* **Atributos:**
* `nombre`


* `area_medica`


* `nivel`


* `descripcion`





### 2. Medico-Especialidad



* **FK (Claves Foráneas):**
* `matricula` (asociado a la tabla Medicos)


* `id_especialidad` (asociado a la tabla Especialidad)





### 3. Medicos



* **PK (Clave Primaria):** `matricula`


* **Atributos:**
* `Nombre`


* `Teléfono`


* `Especialidad_Principal`


* `Especialidad_Secundaria`





### 4. Paciente



* **PK (Clave Primaria):** `N°Clinica`


* **Atributos:**
* `Nombre`


* `Apellido`


* `DNI`


* `Fecha_de_Nacimiento`


* `Domicilio`


* `Obra_social`





### 5. Turno



* **PK (Clave Primaria):** `id_Turnos`


* **Atributos:**
* `fecha_y_hora`


* `estado`


* `Diagnostico_u_observacion`




* **FK (Claves Foráneas):**
* `N°Clinica` (asociado a la tabla Paciente)


* `matricula` (asociado a la tabla Medicos)





### 6. Medicamentos



* **PK (Clave Primaria):** `Codigo_Medicamentos`


* **Atributos:**
* `Nombre_comercial`


* `Monodroga`


* `Laboratorio_de_fabricante`


* `Código_alfanumérico`





### 7. Detalle-Recetas



* **FK (Claves Foráneas):**
* `id_Turnos` (asociado a la tabla Turno)


* `Codigo_Medicamentos` (asociado a la tabla Medicamentos)





---

## Relaciones Principales



* **Especialidad y Medicos:** Se relacionan mediante la tabla intermedia `Medico-Especialidad` utilizando `matricula` e `id_especialidad`.


* **Paciente y Turno:** Un paciente puede registrar varios turnos vinculados por su `N°Clinica`.


* **Medicos y Turno:** Los turnos son asignados a un médico específico identificado por su `matricula`.


* **Turno y Medicamentos:** La relación de muchos a muchos para las recetas se maneja en la tabla `Detalle-Recetas` mediante `id_Turnos` y `Codigo_Medicamentos`.
