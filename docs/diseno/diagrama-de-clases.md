# Diagrama de clases – complemento del modelo del mundo

> **Nota:** este diagrama contiene solo las clases necesarias para HU-01 y HU-02. Debe integrarse con el diagrama del modelo del mundo que el grupo ya tiene (por ejemplo, `Estudiante` probablemente ya existe allí).

```mermaid
classDiagram
    class Estudiante {
        -id: int
        -nombres: String
        -fechaNacimiento: LocalDate
        -sexo: Sexo
    }
    class PerfilSalud {
        -estudianteId: int
        -datosExamen: DatosExamen
        -datosHabito: DatosHabito
        +registrarDatosExamen(ct: Double, cHDL: Double, fecha: LocalDate) void
        +registrarDatosHabito(pas: Integer, pad: Integer, fumador: Boolean, tratamientoHTA: Boolean) void
        +tieneDatosCompletos() boolean
    }
    class DatosExamen {
        -colesterolTotal: double
        -colesterolHDL: double
        -fechaExamen: LocalDate
    }
    class DatosHabito {
        -presionSistolica: int
        -presionDiastolica: int
        -fumador: boolean
        -tratamientoHTA: boolean
    }
    class CalculoRCV {
        -fechaCalculo: LocalDate
        -porcentaje10Anios: double
        -categoria: CategoriaRiesgo
    }
    class CategoriaRiesgo {
        <<enumeration>>
        BAJO
        MODERADO
        ALTO
    }
    class Sexo {
        <<enumeration>>
        FEMENINO
        MASCULINO
    }
    class DatoInvalidoException {
        +getMessage() String
    }

    Estudiante "1" --> "1" PerfilSalud
    PerfilSalud "1" *-- "0..1" DatosExamen
    PerfilSalud "1" *-- "0..1" DatosHabito
    PerfilSalud ..> DatoInvalidoException : lanza
    PerfilSalud "1" --> "0..*" CalculoRCV : alimenta
    CalculoRCV --> CategoriaRiesgo
    Estudiante --> Sexo
```

## Responsabilidades

- **PerfilSalud:** concentra los datos de salud del estudiante y valida las reglas de HU-01 y HU-02.
- **DatosExamen:** valores de laboratorio (CT, cHDL) y fecha del examen.
- **DatosHabito:** presión arterial, tabaquismo y tratamiento antihipertensivo.
- **CalculoRCV:** resultado del cálculo a 10 años; su lógica queda fuera del alcance de estas dos historias.
