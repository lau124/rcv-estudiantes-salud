# HU-02 – Registrar datos de salud de medición/hábito

| **Historia de Usuario** | |
| --- | --- |
| **Código:** | HU-02 |
| **Nombre:** | Registrar datos de salud de medición/hábito (PA, tabaquismo) |
| **Actor:** | Estudiante |
| **Descripción:** | Como **estudiante** quiero **registrar mis datos de salud que requieren medición/hábito (PA, tabaquismo)** para **calcular mi RCV a 10 años**. |

## Criterios de aceptación

| CID | Condición | Resultado |
| --- | --- | --- |
| 1 | Cuando el estudiante ingresa presión sistólica (PAS) y diastólica (PAD) dentro de los rangos permitidos, selecciona su condición de tabaquismo y presiona **Guardar** | Entonces el sistema almacena los datos en el perfil de salud y muestra "Datos de medición y hábito guardados correctamente" |
| 2 | Cuando ingresa una PAS menor que 70 o mayor que 250 mmHg y presiona **Guardar** | Entonces el sistema no guarda y muestra "La presión sistólica debe estar entre 70 y 250 mmHg" |
| 3 | Cuando ingresa una PAD menor que 40 o mayor que 150 mmHg y presiona **Guardar** | Entonces el sistema no guarda y muestra "La presión diastólica debe estar entre 40 y 150 mmHg" |
| 4 | Cuando ingresa una PAS menor o igual que la PAD y presiona **Guardar** | Entonces el sistema no guarda y muestra "La presión sistólica debe ser mayor que la diastólica" |
| 5 | Cuando no selecciona si fuma actualmente y presiona **Guardar** | Entonces el sistema no guarda y muestra "Seleccione si fuma actualmente" |
| 6 | Cuando deja vacía la PAS o la PAD y presiona **Guardar** | Entonces el sistema no guarda y muestra "El campo [presión sistólica / presión diastólica] es obligatorio" |
| 7 | Cuando ingresa un valor no numérico en PAS o PAD | Entonces el sistema no guarda y muestra "Ingrese un valor numérico" |
| 8 | Cuando el estudiante ya tiene datos de medición/hábito registrados y guarda nuevos valores válidos | Entonces el sistema reemplaza los valores anteriores y muestra "Datos de medición y hábito actualizados correctamente" |

> **Supuestos (confirmar con el docente):** rangos PAS 70–250 mmHg y PAD 40–150 mmHg; "tabaquismo" se entiende como *fuma actualmente* (Sí/No); el campo "recibe tratamiento antihipertensivo" es opcional y por defecto es "No".

## Criterios susceptibles de pruebas unitarias

CID 1, 2, 3, 4, 5, 6 y 8. El CID 7 se valida en la capa de interfaz.
