# 6. OBJETIVO GENERAL

**Diseñar y desarrollar** una aplicación web para la gestión integral de perfiles nutricionales y alimentarios, que permita a los usuarios registrar sus datos antropométricos, calcular sus requerimientos calóricos y hacer seguimiento a su ingesta diaria de macronutrientes, con el fin de optimizar el control nutricional y mejorar la toma de decisiones alimenticias.

---

# 7. OBJETIVOS ESPECÍFICOS

1. **Implementar** un módulo de registro de usuarios que capture datos antropométricos (peso, talla, edad, sexo) y objetivos nutricionales (perder peso, mantener, ganar masa muscular), para generar un perfil inicial personalizado.

2. **Desarrollar** un motor de cálculo que determine el Índice de Masa Corporal (IMC), la Tasa Metabólica Basal (TMB) y el Gasto Energético Total Diario (TDEE) en función del nivel de actividad física del usuario.

3. **Crear** un sistema de seguimiento de ingesta diaria que permita al usuario registrar los alimentos consumidos y comparar automáticamente sus macronutrientes (proteínas, carbohidratos y grasas) contra las metas personalizadas.

4. **Integrar** un panel de administración para nutricionistas que facilite la visualización de la evolución de los pacientes, la creación de planes alimenticios personalizados y la generación de reportes de progreso.

---

# 8. PLANTEAMIENTO DEL PROBLEMA

Actualmente, muchas personas carecen de un control estructurado sobre su alimentación. La falta de conocimiento sobre sus requerimientos calóricos reales y la ausencia de herramientas accesibles para monitorear la ingesta diaria conllevan a dietas desbalanceadas, estancamiento en los objetivos físicos y problemas de salud asociados a una mala nutrición. Las soluciones existentes en el mercado suelen ser genéricas, costosas o difíciles de usar para el público general, lo que genera frustración y abandono de los procesos nutricionales.

En el contexto colombiano, según la Encuesta Nacional de Situación Nutricional (ENSIN), existe una alta prevalencia de sobrepeso y obesidad en la población adulta, lo que evidencia la necesidad de herramientas accesibles que apoyen la educación y el seguimiento alimentario. Adicionalmente, los nutricionistas enfrentan dificultades para hacer seguimiento continuo a sus pacientes fuera del consultorio, lo que limita la efectividad de los tratamientos.

La solución propuesta consiste en una aplicación web que centralice el cálculo de requerimientos nutricionales, el registro de alimentos y la comunicación entre paciente y nutricionista, ofreciendo una herramienta intuitiva, accesible y basada en datos objetivos.

## Tabla 1. Comparación: problema actual vs. solución propuesta

| Problema Actual | Consecuencia en la Operación | Solución con la Aplicación |
|:---|:---|:---|
| Cálculo manual e impreciso de calorías y macronutrientes. | Dietas que no se ajustan a las necesidades reales del usuario, provocando frustración y abandono. | Calculadora automática de IMC, TMB y TDEE basada en datos antropométricos y nivel de actividad. |
| Falta de seguimiento estructurado de la ingesta diaria. | El usuario no es consciente de sus excesos o déficits nutricionales, dificultando la corrección de hábitos. | Registro diario de alimentos con visualización gráfica de macronutrientes vs. metas establecidas. |
| Comunicación ineficiente entre nutricionista y paciente. | Pérdida de tiempo en consultas presenciales para ajustes menores y falta de datos objetivos para decisiones. | Panel de administración para nutricionistas con acceso al historial y evolución del paciente en tiempo real. |

---

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

---

# 10. DIAGRAMA MODELO RELACIONAL

## Tabla usuarios

| Campo | Tipo | Clave |
|:---|:---|:---|
| id | INT | PK |
| nombre | VARCHAR(100) | |
| email | VARCHAR(100) | UNIQUE |
| password | VARCHAR(255) | |
| fecha_nacimiento | DATE | |
| sexo | VARCHAR(10) | |
| peso_actual | DECIMAL(5,2) | |
| altura | DECIMAL(5,2) | |
| nivel_actividad | VARCHAR(50) | |
| objetivo | VARCHAR(50) | |

## Tabla perfiles_nutricionales

| Campo | Tipo | Clave |
|:---|:---|:---|
| id | INT | PK |
| usuario_id | INT | FK → usuarios(id) |
| imc | DECIMAL(4,2) | |
| tmb | DECIMAL(6,2) | |
| tdee | DECIMAL(6,2) | |
| fecha_calculo | DATE | |

## Tabla alimentós

