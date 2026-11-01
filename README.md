# RCV Estudiantes – Registro de datos de salud

Repositorio académico del curso **Análisis y modelamiento de software** (Ingeniería de Sistemas, Universidad Mariana).

Contiene la especificación y el diseño de dos historias de usuario del módulo de **riesgo cardiovascular (RCV) a 10 años**:

- **HU-01** – Registrar datos de salud con examen (cHDL, CT).
- **HU-02** – Registrar datos de salud de medición/hábito (PA, tabaquismo).

> Grupo 3 – Tema: **Control de versiones profesional** (flujo Git con ramas, merges y estrategia).
> Integrantes: Luis Insuasti Salas, Laura Camila Mora.

## Estructura del repositorio

| Ruta | Contenido |
| --- | --- |
| `docs/historias-de-usuario/` | Especificación de HU-01 y HU-02 (Anexo A) |
| `docs/pruebas/` | Escenarios de prueba (Anexo B) y casos de prueba (Anexo C) por historia |
| `docs/diseno/` | Diseño GUI y diagrama de clases del modelo del mundo |
| `docs/estrategia-ramas.md` | Estrategia de ramas, convención de commits y versionado |
| `.github/` | Plantilla de pull request |
| `CHANGELOG.md` | Historial de versiones |

## Flujo de trabajo (resumen)

1. `main` solo contiene versiones entregables y etiquetadas (`vX.Y.Z`).
2. `develop` integra el trabajo terminado.
3. Cada tarea se hace en una rama `feature/<descripcion-corta>` creada desde `develop`.
4. Se integra con *pull request* y revisión del otro integrante; el merge se hace con `--no-ff`.
5. Los commits siguen *Conventional Commits* (`feat`, `docs`, `fix`, `chore`, `merge`).

Detalle completo en [`docs/estrategia-ramas.md`](docs/estrategia-ramas.md).

## Cómo clonar y colaborar

```bash
git clone <URL-del-repositorio>
cd rcv-estudiantes-salud
git switch develop
git switch -c feature/mi-tarea
# ... trabajar y hacer commits ...
git push -u origin feature/mi-tarea   # y abrir el pull request hacia develop
```
