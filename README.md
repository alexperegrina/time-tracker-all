
# ⏰ **Time Tracker Developer Exercise**

¡Bienvenido a mi implementación del ejercicio de seguimiento de tiempo! 🎉  
Esta solución está dividida en **dos proyectos**:

- 🖥️ **Backend**: Implementado con **Symfony**.
- 🌐 **Frontend**: Construido con **Angular**.

Puedes consultar el enunciado de la prueba haciendo clic [aquí](etc/readme/statement.md)
o el archivo original [aquí](etc/readme/statement.pdf)
---

## 📚 **Estructura del README**

1. [🔍 Introducción](#-introducción)
2. [🛠️ Solución Técnica](#️-solución-técnica)
3. [🚀 Preparar el Entorno](#-preparar-el-entorno)
5. [🎯 Docker](#-consideraciones-finales)

---

## 🔍 **Introducción**

El objetivo de este proyecto es ofrecer una aplicación simple para que los usuarios puedan:
- Crear tareas, iniciar y detener su seguimiento de tiempo.
- Visualizar un resumen del tiempo dedicado a cada tarea.

---

## 🛠️ **Solución Técnica**

### 🖥️ **Backend**
El backend se ha implementado en **Symfony** y se organiza en los siguientes módulos:

1. **App**: Módulo principal para la configuración inicial y las dependencias principales.
2. **Auth**: Módulo encargado de la autenticación y gestión de usuarios (JWT incluido 🚀).
3. **Core**: Contiene la lógica compartida y componentes reutilizables del sistema.
4. **TimeRecording**: Maneja la lógica específica del seguimiento de tiempo y las tareas.

#### 📦 **Arquitectura**
- **Bundles Symfony**: Cada módulo es un bundle autocontenido, siguiendo una estructura modular.
- **DDD y CQS**:
   - Contextos delimitados claramente definidos en cada módulo.
   - Aplicación de consultas y comandos separados para mejorar la mantenibilidad.

#### ✅ **Pruebas**
Cada módulo incluye sus propias pruebas:
- 🧪 **Unitarias**: Validan funcionalidades individuales.
- 🔄 **Integración**: Comprueban la comunicación entre los módulos.
- 🌐 **End-to-End (E2E)**: Validan flujos completos de la aplicación.

### 🌐 **Frontend**
El frontend utiliza **Angular** con las siguientes características:
- **Responsividad**: Diseño adaptado a dispositivos móviles y de escritorio.
- **Integración con el Backend**: Uso de servicios HTTP para interactuar con los endpoints del backend.
- **Flujo de Usuario**:
   1. Registro / Inicio de Sesión.
   2. Gestión de tareas (crear, iniciar, detener).
   3. Resumen de tareas y tiempo.

---

## 🚀 **Preparar el Entorno**

### 🖥️ **Root**

1. Clona el repositorio del backend:
   ```bash
   git clone --recurse-submodules https://github.com/alexperegrina/time-tracker-all.git
   cd time-tracker-all
   ```
2. Actualizar los submódulos:
   ```bash
   git submodule update --remote
   ```
   
En este punto tendremos que tener dos ventanas de la terminal.
Por motivos de rendimiento se deja para el final todo el tema relacionado con Docker.


### 🖥️ **Backend**

1. Nos movemos al backend:
   ```bash
   cd time-tracker-backend
   ```
2. Inicia el entorno Docker:
   ```bash
   make docker-db-start
   ```
3. Instala las dependencias:
   ```bash
   make first-env
   ```
4. Aplica las migraciones:
   ```bash
   make restore-env
   ```
5. Levanta el servidor de desarrollo:
   ```bash
   symfony server:start --no-tls
   ```

### 🌐 **Frontend**

1. Nos movemos al frontend:
   ```bash
   cd time-tracker-frontend
   ```
2. Instala las dependencias:
   ```bash
   npm install
   ```
3. Levanta el servidor de desarrollo:
   ```bash
   npm start
   ```
4. Accede a la aplicación:  
   Abre tu navegador y dirígete a [http://localhost:4200](http://localhost:4200).

---
## 🎯 **Docker**

Se ha añadido por cada proyecto los servicios que necesita. 
En el root del proyecto hay otra configuracion para poder inicializar todo de golpe.
Por motivos que desconozco el rendimiento de la aplicacion se ve muy afectado si se utiliza el 
docker antes de encender los servicios a mano.
---

Encontraras información mas amplia en el README de cada proyecto