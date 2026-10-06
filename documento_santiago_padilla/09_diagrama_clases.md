# 9. DIAGRAMA DE CLASES

## Entidades y atributos

### Usuario
- id: int
- nombre: String
- email: String
- password: String
- fechaNacimiento: Date
- sexo: String
- peso: float
- altura: float
- nivelActividad: String
- objetivo: String

### PerfilNutricional
- id: int
- imc: float
- tmb: float
- tdee: float
- fechaCalculo: Date

### Alimento
- id: int
- nombre: String
- calorias: float
- proteinas: float
- carbohidratos: float
- grasas: float
- porcionBase: float

### RegistroDiario
- id: int
- fecha: Date
- cantidad: float
- caloriasTotales: float

### PlanAlimenticio
- id: int
- descripcion: String
- fechaInicio: Date
- fechaFin: Date

### Nutricionista
- id: int
- nombre: String
- email: String
- password: String
- especialidad: String

## Relaciones
- Usuario 1 —— 1 PerfilNutricional
- Usuario 1 —— N RegistroDiario
- RegistroDiario N —— 1 Alimento
- Nutricionista 1 —— N PlanAlimenticio
- Usuario (paciente) 1 —— N PlanAlimenticio

**Ilustración 1. Diagrama de clases del sistema nutricional**
