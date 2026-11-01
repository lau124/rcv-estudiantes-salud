# HU-01 – Escenarios y casos de prueba

Clase bajo prueba: `PerfilSalud`. Fecha actual del sistema fijada en las pruebas: **2026-10-31**.
Orden de validación en el método: (1) campos obligatorios, (2) rangos, (3) cHDL ≤ CT, (4) fecha no futura.

## Escenarios de prueba (Anexo B)

| Código HU | HU-01 |
| --- | --- |
| **No** | E1 |
| **Descripción** | Estudiante con perfil de salud sin datos de examen registrados |
| **Datos** | `PerfilSalud { estudianteId = 1001, datosExamen = null }` |
| **CID** | 1, 2, 3, 4, 6, 7 |

| Código HU | HU-01 |
| --- | --- |
| **No** | E2 |
| **Descripción** | Estudiante con un examen previamente registrado que desea actualizarlo |
| **Datos** | `PerfilSalud { estudianteId = 1002, datosExamen = { ct = 210, cHDL = 55, fechaExamen = 2026-09-15 } }` |
| **CID** | 8 |

## Casos de prueba (Anexo C)

| CPId | Nombre | Clase | Método | HU | Escenario | Valores de entrada | Resultado esperado |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CP-01-01 | testRegistrarExamenValido | PerfilSalud | registrarDatosExamen | HU-01 | E1 | ct = 200, cHDL = 50, fecha = 2026-10-20 | Se almacena el examen (200, 50, 2026-10-20); no lanza excepción |
| CP-01-02 | testCtPorDebajoDelMinimo | PerfilSalud | registrarDatosExamen | HU-01 | E1 | ct = 99, cHDL = 50, fecha = 2026-10-20 | Lanza `DatoInvalidoException` con "El colesterol total debe estar entre 100 y 400 mg/dL"; `datosExamen` sigue en null |
| CP-01-03 | testCtPorEncimaDelMaximo | PerfilSalud | registrarDatosExamen | HU-01 | E1 | ct = 401, cHDL = 50, fecha = 2026-10-20 | Lanza `DatoInvalidoException` con "El colesterol total debe estar entre 100 y 400 mg/dL" |
| CP-01-04 | testCtEnLimites | PerfilSalud | registrarDatosExamen | HU-01 | E1 | ct = 100 y luego ct = 400, cHDL = 50, fecha = 2026-10-20 | Ambos valores se aceptan y se almacenan |
| CP-01-05 | testHdlPorDebajoDelMinimo | PerfilSalud | registrarDatosExamen | HU-01 | E1 | ct = 200, cHDL = 9, fecha = 2026-10-20 | Lanza `DatoInvalidoException` con "El cHDL debe estar entre 10 y 150 mg/dL" |
| CP-01-06 | testHdlPorEncimaDelMaximo | PerfilSalud | registrarDatosExamen | HU-01 | E1 | ct = 400, cHDL = 151, fecha = 2026-10-20 | Lanza `DatoInvalidoException` con "El cHDL debe estar entre 10 y 150 mg/dL" |
| CP-01-07 | testCtVacio | PerfilSalud | registrarDatosExamen | HU-01 | E1 | ct = null, cHDL = 50, fecha = 2026-10-20 | Lanza `DatoInvalidoException` con "El campo colesterol total es obligatorio" |
| CP-01-08 | testHdlMayorQueCt | PerfilSalud | registrarDatosExamen | HU-01 | E1 | ct = 120, cHDL = 130, fecha = 2026-10-20 | Lanza `DatoInvalidoException` con "El cHDL no puede ser mayor que el colesterol total" |
| CP-01-09 | testFechaExamenFutura | PerfilSalud | registrarDatosExamen | HU-01 | E1 | ct = 200, cHDL = 50, fecha = 2026-11-05 | Lanza `DatoInvalidoException` con "La fecha del examen no puede ser futura" |
| CP-01-10 | testActualizarExamenExistente | PerfilSalud | registrarDatosExamen | HU-01 | E2 | ct = 180, cHDL = 60, fecha = 2026-10-25 | `datosExamen` pasa de (210, 55, 2026-09-15) a (180, 60, 2026-10-25) |

## Trazabilidad

| CID | Casos de prueba |
| --- | --- |
| 1 | CP-01-01, CP-01-04 |
| 2 | CP-01-02, CP-01-03, CP-01-04 |
| 3 | CP-01-05, CP-01-06 |
| 4 | CP-01-07 |
| 5 | No aplica (validación de la interfaz) |
| 6 | CP-01-08 |
| 7 | CP-01-09 |
| 8 | CP-01-10 |
