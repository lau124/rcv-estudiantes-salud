# Diseño GUI de la interfaz

> **Pendiente del grupo:** construir los prototipos en una herramienta de diseño (Figma, Penpot, Balsamiq, etc.), exportarlos como PNG a `docs/diseno/img/` y enlazarlos aquí. Este documento define las pantallas, los campos y los mensajes que deben mostrar.

## Pantalla 1 – Datos de examen (HU-01)

Esquema de referencia:

```
+--------------------------------------------------+
|  Mi riesgo cardiovascular  >  Datos de examen    |
+--------------------------------------------------+
|  Colesterol total (CT)   [ ______ ] mg/dL        |
|  Colesterol HDL (cHDL)   [ ______ ] mg/dL        |
|  Fecha del examen        [ dd/mm/aaaa ]          |
|                                                  |
|  [ mensaje de éxito o error ]                    |
|                                                  |
|            [ Cancelar ]   [ Guardar ]            |
+--------------------------------------------------+
```

| Evento | Mensaje |
| --- | --- |
| Curso básico (CID 1) | "Datos del examen guardados correctamente" |
| Actualización (CID 8) | "Datos del examen actualizados correctamente" |
| CT fuera de rango (CID 2) | "El colesterol total debe estar entre 100 y 400 mg/dL" |
| cHDL fuera de rango (CID 3) | "El cHDL debe estar entre 10 y 150 mg/dL" |
| Campo vacío (CID 4) | "El campo colesterol total es obligatorio" / "El campo cHDL es obligatorio" |
| No numérico (CID 5) | "Ingrese un valor numérico" |
| cHDL > CT (CID 6) | "El cHDL no puede ser mayor que el colesterol total" |
| Fecha futura (CID 7) | "La fecha del examen no puede ser futura" |

## Pantalla 2 – Datos de medición y hábito (HU-02)

```
+--------------------------------------------------+
|  Mi riesgo cardiovascular  >  Medición y hábito  |
+--------------------------------------------------+
|  Presión sistólica (PAS)   [ ____ ] mmHg         |
|  Presión diastólica (PAD)  [ ____ ] mmHg         |
|  ¿Fuma actualmente?        ( ) Sí   ( ) No       |
|  [ ] Recibe tratamiento antihipertensivo         |
|                                                  |
|  [ mensaje de éxito o error ]                    |
|                                                  |
|            [ Cancelar ]   [ Guardar ]            |
+--------------------------------------------------+
```

| Evento | Mensaje |
| --- | --- |
| Curso básico (CID 1) | "Datos de medición y hábito guardados correctamente" |
| Actualización (CID 8) | "Datos de medición y hábito actualizados correctamente" |
| PAS fuera de rango (CID 2) | "La presión sistólica debe estar entre 70 y 250 mmHg" |
| PAD fuera de rango (CID 3) | "La presión diastólica debe estar entre 40 y 150 mmHg" |
| PAS ≤ PAD (CID 4) | "La presión sistólica debe ser mayor que la diastólica" |
| Tabaquismo sin seleccionar (CID 5) | "Seleccione si fuma actualmente" |
| Campo vacío (CID 6) | "El campo presión sistólica es obligatorio" / "El campo presión diastólica es obligatorio" |
| No numérico (CID 7) | "Ingrese un valor numérico" |

## Criterios de diseño

- Mensajes de error junto al campo afectado, en color distinto al de los mensajes de éxito, y no solo por color (también con texto o ícono).
- Unidades visibles al lado de cada campo.
- El botón **Guardar** permanece habilitado; la validación ocurre al presionarlo.
