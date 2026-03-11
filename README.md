# LexApiRest

LexApiRest es una API RESTful desarrollada con el framework Spring Boot. El proyecto está diseñado para interactuar con bases de datos relacionales y proporcionar servicios web robustos y escalables.

---
**Recomendación para VS Code:** > Puedes gestionar este proyecto de forma eficiente usando el comando `Ctrl + Shift + P`, escribiendo **"Spring Initializr"** y seleccionando las opciones correspondientes para añadir dependencias o sincronizar el proyecto.

## 🚀 Tecnologías Utilizadas

Este proyecto utiliza las siguientes herramientas y frameworks:

- **Java 21**: La versión LTS más reciente para aprovechar las últimas mejoras de rendimiento.
- **Spring Boot 3.5.11**: Framework principal para el desarrollo de la aplicación.
- **Spring Data JPA**: Para la gestión de la persistencia de datos y el acceso a la base de datos de forma sencilla.
- **Spring Web**: Para la creación de endpoints REST y el manejo de peticiones HTTP.
- **PostgreSQL**: Driver de base de datos para entornos de producción y desarrollo.
- **Maven**: Herramienta de gestión de dependencias y construcción del proyecto.

---

## 🛠️ Requisitos Previos

Antes de comenzar, asegúrate de tener instalado lo siguiente:

- **Java Development Kit (JDK) 21** o superior.
- **Apache Maven** 3.6+
- **PostgreSQL** en ejecución.

---

## ⚙️ Configuración del Proyecto

La aplicación utiliza Spring Boot para la configuración. Las configuraciones principales se definen en `src/main/resources/application.properties`, y las variables sensibles se almacenan en un archivo `.env` en la raíz del proyecto para mayor seguridad.

### Archivo application.properties

```properties
# Nombre de la aplicación
spring.application.name=lexapirest

# Configuración de JPA / Hibernate
spring.jpa.hibernate.ddl-auto=update

# Puerto del servidor
server.port=8080

# Importar configuraciones opcionales desde .env
spring.config.import=optional:file:.env[properties]

# Configuración de la base de datos PostgreSQL (usando variables de entorno)
spring.datasource.url=${SPRING_DATASOURCE_URL}
spring.datasource.username=${SPRING_DATASOURCE_USERNAME}
spring.datasource.password=${SPRING_DATASOURCE_PASSWORD}
```

### Archivo .env

Crea un archivo `.env` en la raíz del proyecto con las siguientes variables:

```env
SPRING_DATASOURCE_URL=jdbc:postgresql://localhost:5432/database
SPRING_DATASOURCE_USERNAME=lex
SPRING_DATASOURCE_PASSWORD=123456
SPRING_DATASOURCE_DB=postgres
```

**Nota:** Asegúrate de que el archivo `.env` esté incluido en `.gitignore` para evitar exponer credenciales sensibles.

### Interconexión entre archivos

- **application.properties**: Define las configuraciones de Spring Boot. Utiliza `${VARIABLE}` para referenciar variables de entorno.
- **.env**: Almacena las variables de entorno de forma local. Spring Boot las importa opcionalmente con `spring.config.import=optional:file:.env[properties]`.
- **Ventajas**: Separa configuraciones sensibles del código, facilitando el despliegue en diferentes entornos (desarrollo, producción) sin modificar el código fuente.

---

## 🏃 Ejecución

Para ejecutar la aplicación localmente, abre una terminal en la raíz del proyecto y utiliza el siguiente comando de Maven:

```bash
mvn spring-boot:run
```

La API estará disponible por defecto en: **http://localhost:8080**

---

## 🧪 Pruebas

El proyecto incluye soporte para pruebas unitarias e integración con `spring-boot-starter-test`. Para ejecutar los tests:

```bash
mvn test
```

---

## 📦 Estructura del Proyecto

```
src/
├── main/
│   ├── java/
│   │   └── com/lex/apirest/
│   │       ├── controllers/       # Controladores REST
│   │       ├── services/          # Servicios de lógica de negocio
│   │       ├── models/            # Entidades y DTOs
│   │       ├── repositories/      # Interfaces de acceso a datos
│   │       └── LexapirestApplication.java
│   └── resources/
│       ├── application.properties  # Configuración
│       ├── static/                # Archivos estáticos
│       └── templates/             # Templates HTML
└── test/
    └── java/                       # Tests unitarios
```

- **Controladores**: Contienen los endpoints REST de la API.
- **Servicios**: Implementan la lógica de negocio.
- **Modelos**: Clases de entidades y DTOs.
- **Repositorios**: Interfaces para la interacción con la base de datos.
- **pom.xml**: Archivo de configuración de Maven con todas las dependencias.
