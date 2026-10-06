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

## Tabla alimentos

| Campo | Tipo | Clave |
|:---|:---|:---|
| id | INT | PK |
| nombre | VARCHAR(100) | |
| calorias | DECIMAL(6,2) | |
| proteinas | DECIMAL(5,2) | |
| carbohidratos | DECIMAL(5,2) | |
| grasas | DECIMAL(5,2) | |
| porcion_base | DECIMAL(5,2) | |

## Tabla registros_diarios

| Campo | Tipo | Clave |
|:---|:---|:---|
| id | INT | PK |
| usuario_id | INT | FK → usuarios(id) |
| alimento_id | INT | FK → alimentos(id) |
| fecha | DATE | |
| cantidad | DECIMAL(5,2) | |

## Tabla planes_alimenticios

| Campo | Tipo | Clave |
|:---|:---|:---|
| id | INT | PK |
| nutricionista_id | INT | FK → nutricionistas(id) |
| paciente_id | INT | FK → usuarios(id) |
| descripcion | TEXT | |
| fecha_inicio | DATE | |
| fecha_fin | DATE | |

## Tabla nutricionistas

| Campo | Tipo | Clave |
|:---|:---|:---|
| id | INT | PK |
| nombre | VARCHAR(100) | |
| email | VARCHAR(100) | UNIQUE |
| password | VARCHAR(255) | |
| especialidad | VARCHAR(100) | |

**Ilustración 2. Diagrama del modelo relacional de la base de datos**
