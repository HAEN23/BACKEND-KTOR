#  Backend API - Sistema de Gestión Musical (Ktor)

Este repositorio contiene la API RESTful que sirve como backend para la aplicación de catálogo musical. Está desarrollado en **Kotlin** utilizando el framework **Ktor**, estructurado bajo principios de Clean Architecture para garantizar escalabilidad y fácil mantenimiento.

##  Características Principales

* **CRUD Completo:** Endpoints disponibles para crear, leer, actualizar y eliminar registros de **Artistas**, **Álbumes** y **Pistas (Tracks)**.
* **Arquitectura por Capas:** Separación clara de responsabilidades entre el enrutamiento (`routes`), la lógica de acceso a datos (`repositories`) y los modelos de la base de datos (`models`).
* **Seguridad y DTOs:** Implementación de Data Transfer Objects (DTOs) para proteger la estructura interna de la base de datos y evitar la sobreexposición de datos sensibles al cliente.
* **Configuración Modular:** Uso de los *Plugins* de Ktor para manejar de forma aislada la serialización (JSON), la seguridad, el enrutamiento y la conexión a la base de datos.

## 🛠️ Stack Tecnológico

* **Lenguaje:** [Kotlin](https://kotlinlang.org/)
* **Framework:** [Ktor Server](https://ktor.io/)
* **Gestor de dependencias:** Gradle (Kotlin DSL)
* **Base de Datos:** (Configurada a través de `DatabaseFactory.kt` y `application.conf`)
* **Serialización:** `ktor-serialization-kotlinx-json`

##  Estructura del Código Source (`src/main/kotlin/`)

El proyecto está organizado en los siguientes paquetes principales:

* `models/`: Clases de datos (Data Classes) que representan las tablas en la base de datos.
* `dtos/`: Objetos de transferencia para estructurar el JSON de entrada y salida de las peticiones HTTP.
* `repositories/`: Clases que encapsulan las consultas (queries) a la base de datos.
* `routes/`: Definición de los endpoints de la API (`/artistas`, `/albumes`, `/tracks`).
* `plugins/`: Inicialización de módulos del servidor (Routing, Base de Datos, CORS/Security).
* `Application.kt`: Punto de entrada (Main) de la aplicación.

## ⚙️ Requisitos Previos

1. **Java Development Kit (JDK):** Versión 11 o superior.
2. **Base de Datos:** Asegúrate de tener tu gestor de base de datos en ejecución y verificar que las credenciales en `src/main/resources/application.conf` sean las correctas.
3. **IDE:** Recomendado usar IntelliJ IDEA (Community o Ultimate).

##  Cómo compilar y ejecutar el servidor localmente

No es necesario que instales Gradle en tu computadora, el proyecto incluye un *Wrapper* de Gradle que se encarga de todo.

1. **Abre una terminal en la raíz del proyecto.**
2. **Para compilar el proyecto:**
   * En Windows: `gradlew.bat build`
   * En Mac/Linux: `./gradlew build`
3. **Para arrancar el servidor Ktor:**
   * En Windows: `gradlew.bat run`
   * En Mac/Linux: `./gradlew run`

Una vez iniciado, el servidor estará escuchando peticiones (por defecto en `http://localhost:8080`, a menos que se especifique otro puerto en el archivo `.conf`).

