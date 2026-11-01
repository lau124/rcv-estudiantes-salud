# HU-02 – Escenarios y casos de prueba

Clase bajo prueba: `PerfilSalud`.
Orden de validación: (1) campos obligatorios, (2) rangos, (3) PAS > PAD, (4) tabaquismo seleccionado.

## Escenarios de prueba (Anexo B)

| Código HU | HU-02 |
| --- | --- |
| **No** | E1 |
| **Descripción** | Estudiante con perfil de salud sin datos de medición ni hábito registrados |
| **Datos** | `PerfilSalud { estudianteId = 1001, datosHabito = null }` |
| **CID** | 1, 2, 3, 4, 5, 6 |

| Código HU | HU-02 |
| --- | --- |
| **No** | E2 |
| **Descripción** | Estudiante con datos de medición/hábito previos que desea actualizarlos |
| **Datos** | `PerfilSalud { estudianteId = 1002, datosHabito = { pas = 130, pad = 85, fumador = true, tratamientoHTA = false } }` |
| **CID** | 8 |

## Casos de prueba (Anexo C)

| CPId | Nombre | Clase | Método | HU | Escenario | Valores de entrada | Resultado esperado |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CP-02-01 | testRegistrarHabitoValido | PerfilSalud | registrarDatosHabito | HU-02 | E1 | pas = 120, pad = 80, fumador = false, tratamientoHTA = false | Se almacenan los datos; no lanza excepción |
| CP-02-02 | testPasPorDebajoDelMinimo | PerfilSalud | registrarDatosHabito | HU-02 | E1 | pas = 69, pad = 60, fumador = false, tratamientoHTA = false | Lanza `DatoInvalidoException` con "La presión sistólica debe estar entre 70 y 250 mmHg" |
| CP-02-03 | testPasPorEncimaDelMaximo | PerfilSalud | registrarDatosHabito | HU-02 | E1 | pas = 251, pad = 80, fumador = false, tratamientoHTA = false | Lanza `DatoInvalidoException` con "La presión sistólica debe estar entre 70 y 250 mmHg" |
| CP-02-04 | testPadPorDebajoDelMinimo | PerfilSalud | registrarDatosHabito | HU-02 | E1 | pas = 120, pad = 39, fumador = false, tratamientoHTA = false | Lanza `DatoInvalidoException` con "La presión diastólica debe estar entre 40 y 150 mmHg" |
| CP-02-05 | testPadPorEncimaDelMaximo | PerfilSalud | registrarDatosHabito | HU-02 | E1 | pas = 250, pad = 151, fumador = false, tratamientoHTA = false | Lanza `DatoInvalidoException` con "La presión diastólica debe estar entre 40 y 150 mmHg" |
| CP-02-06 | testPasIgualQuePad | PerfilSalud | registrarDatosHabito | HU-02 | E1 | pas = 90, pad = 90, fumador = false, tratamientoHTA = false | Lanza `DatoInvalidoException` con "La presión sistólica debe ser mayor que la diastólica" |
| CP-02-07 | testPasMenorQuePad | PerfilSalud | registrarDatosHabito | HU-02 | E1 | pas = 80, pad = 100, fumador = false, tratamientoHTA = false | Lanza `DatoInvalidoException` con "La presión sistólica debe ser mayor que la diastólica" |
| CP-02-08 | testTabaquismoNoSeleccionado | PerfilSalud | registrarDatosHabito | HU-02 | E1 | pas = 120, pad = 80, fumador = null, tratamientoHTA = false | Lanza `DatoInvalidoException` con "Seleccione si fuma actualmente" |
| CP-02-09 | testPasVacia | PerfilSalud | registrarDatosHabito | HU-02 | E1 | pas = null, pad = 80, fumador = false, tratamientoHTA = false | Lanza `DatoInvalidoException` con "El campo presión sistólica es obligatorio" |
| CP-02-10 | testActualizarHabitoExistente | PerfilSalud | registrarDatosHabito | HU-02 | E2 | pas = 118, pad = 76, fumador = false, tratamientoHTA = false | `datosHabito` pasa de (130, 85, true, false) a (118, 76, false, false) |
| CP-02-11 | testPresionesEnLimites | PerfilSalud | registrarDatosHabito | HU-02 | E1 | pas = 70, pad = 40, fumador = true, tratamientoHTA = false | Los valores límite se aceptan y se almacenan |

## Trazabilidad

| CID | Casos de prueba |
| --- | --- |
| 1 | CP-02-01, CP-02-11 |
| 2 | CP-02-02, CP-02-03 |
| 3 | CP-02-04, CP-02-05 |
| 4 | CP-02-06, CP-02-07 |
| 5 | CP-02-08 |
| 6 | CP-02-09 |
| 7 | No aplica (validación de la interfaz) |
| 8 | CP-02-10 |
