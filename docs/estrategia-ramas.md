# Estrategia de control de versiones

Se adopta una versión simplificada de **Git Flow**, adecuada para un equipo de dos personas que entrega por hitos.

## Ramas

| Rama | Origen | Se integra en | Propósito |
| --- | --- | --- | --- |
| `main` | – | – | Versiones entregables. Cada merge lleva una etiqueta `vX.Y.Z`. |
| `develop` | `main` | `release/*` | Integración continua del trabajo terminado. |
| `feature/<tema>` | `develop` | `develop` | Una tarea concreta (una HU, el diseño GUI, el diagrama de clases). |
| `release/vX.Y.Z` | `develop` | `main` y `develop` | Preparación de una entrega (CHANGELOG, ajustes finales). |
| `hotfix/<tema>` | `main` | `main` y `develop` | Corrección urgente sobre una versión ya entregada. |

Nombres en minúscula, con guiones y sin tildes: `feature/hu-01-datos-examen`.

## Convención de commits (Conventional Commits)

Formato: `tipo(alcance opcional): descripción en imperativo`

| Tipo | Uso |
| --- | --- |
| `feat` | Nueva funcionalidad o artefacto principal |
| `docs` | Cambios en documentación o especificaciones |
| `fix` | Corrección de un error |
| `refactor` | Reorganización sin cambiar el resultado |
| `chore` | Configuración y tareas de mantenimiento |
| `merge` | Mensaje de los merges de integración |

Ejemplos: `docs(hu): especificar HU-01 registrar datos de examen`, `fix(pruebas): corregir valor límite de cHDL`.

Reglas: un commit = un cambio lógico; primera línea de máximo ~72 caracteres; no subir archivos temporales.

## Reglas de integración

- Nadie hace commit directo en `main` ni en `develop`.
- Todo cambio entra por *pull request* con al menos una revisión del otro integrante.
- Los merges usan `--no-ff` para conservar la historia de cada rama en el grafo.
- Las ramas `feature/*` se eliminan una vez integradas.

## Versionado semántico

`vMAYOR.MENOR.PARCHE`

- `v0.1.0`: línea base del repositorio (README, estrategia, plantilla de PR).
- `v1.0.0`: primera entrega completa (HU-01, HU-02, pruebas, GUI y diagrama de clases).

## Configuración recomendada en GitHub

En *Settings → Branches* crear una regla de protección para `main` (y `develop`) que exija pull request antes de integrar.

## Conflictos

1. `git switch feature/mi-tarea` y `git merge develop`.
2. Abrir los archivos marcados con `<<<<<<<`, decidir el contenido final y quitar los marcadores.
3. `git add <archivo>` y `git commit` (el mensaje del merge ya viene sugerido).
