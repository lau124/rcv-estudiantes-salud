# HU-01 – Registrar datos de salud con examen

| **Historia de Usuario** | |
| --- | --- |
| **Código:** | HU-01 |
| **Nombre:** | Registrar datos de salud con examen (cHDL, CT) |
| **Actor:** | Estudiante |
| **Descripción:** | Como **estudiante** quiero **registrar mis datos de salud con examen (cHDL, CT)** para **calcular mi RCV a 10 años**. |

## Criterios de aceptación

| CID | Condición | Resultado |
| --- | --- | --- |
| 1 | Cuando el estudiante ingresa un colesterol total (CT) y un cHDL numéricos dentro de los rangos permitidos y una fecha de examen válida, y presiona **Guardar** | Entonces el sistema almacena los datos en el perfil de salud y muestra el mensaje "Datos del examen guardados correctamente" |
| 2 | Cuando ingresa un CT menor que 100 o mayor que 400 mg/dL y presiona **Guardar** | Entonces el sistema no guarda y muestra "El colesterol total debe estar entre 100 y 400 mg/dL" |
| 3 | Cuando ingresa un cHDL menor que 10 o mayor que 150 mg/dL y presiona **Guardar** | Entonces el sistema no guarda y muestra "El cHDL debe estar entre 10 y 150 mg/dL" |
| 4 | Cuando deja vacío el CT o el cHDL y presiona **Guardar** | Entonces el sistema no guarda y muestra "El campo [colesterol total / cHDL] es obligatorio" |
| 5 | Cuando ingresa un valor no numérico en CT o cHDL | Entonces el sistema no guarda y muestra "Ingrese un valor numérico" |
| 6 | Cuando ingresa un cHDL mayor que el CT y presiona **Guardar** | Entonces el sistema no guarda y muestra "El cHDL no puede ser mayor que el colesterol total" |
| 7 | Cuando ingresa una fecha de examen posterior a la fecha actual y presiona **Guardar** | Entonces el sistema no guarda y muestra "La fecha del examen no puede ser futura" |
| 8 | Cuando el estudiante ya tiene un examen registrado y guarda nuevos valores válidos | Entonces el sistema reemplaza los valores anteriores y muestra "Datos del examen actualizados correctamente" |

> **Supuestos (confirmar con el docente):** los rangos de validación (CT 100–400 mg/dL, cHDL 10–150 mg/dL) son valores razonables propuestos por el grupo; la unidad es mg/dL.

## Criterios susceptibles de pruebas unitarias

CID 1, 2, 3, 4, 6, 7 y 8 (reglas de dominio). El CID 5 se valida en la capa de interfaz, por lo que no genera caso de prueba unitaria.
