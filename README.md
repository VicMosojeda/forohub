# Forohub

Forohub es una aplicación web que permite a los usuarios crear, mostrar, actualizar y eliminar tópicos. El proyecto está desarrollado con Spring Boot, utiliza MySQL como base de datos y JWT para la autenticación. También se emplea Lombok para la reducción de código boilerplate en Java.

## Tecnologías Utilizadas

- **Java 17**: Lenguaje de programación utilizado.
- **Spring Boot**: Framework utilizado para el desarrollo del backend.
- **MySQL**: Base de datos relacional utilizada para almacenar los datos.
- **Lombok**: Librería utilizada para reducir el código boilerplate en Java.
- **JWT (JSON Web Tokens)**: Utilizado para la autenticación y autorización de usuarios.

## Prerrequisitos

- Java 17 o superior
- Maven
- Docker (opcional, para ejecutar MySQL en un contenedor)

## Instalación

1. Clona el repositorio:
    ```bash
    git clone https://github.com/VicMosojeda/forohub
    cd forohub
    ```

2. Configura la base de datos MySQL. Puedes usar Docker para iniciar una instancia de MySQL:
    ```bash
    docker run --name mysql-forohub -e MYSQL_ROOT_PASSWORD=tu_contraseña -e MYSQL_DATABASE=forohub -p 3306:3306 -d mysql:latest
    ```

3. Configura el archivo `application.properties` en `src/main/resources` con tus credenciales de MySQL:
    ```properties
    spring.datasource.url=jdbc:mysql://localhost:3306/forohub
    spring.datasource.username=root
    spring.datasource.password=tu_contraseña
    spring.jpa.hibernate.ddl-auto=update
    spring.jpa.show-sql=true
    spring.jpa.properties.hibernate.format_sql=true
    ```

4. Compila y ejecuta la aplicación:
    ```bash
    ./mvnw spring-boot:run
    ```

## Uso

La aplicación expone varios endpoints para manejar los tópicos. Aquí hay algunos ejemplos de cómo puedes interactuar con la API:

### Autenticación

- **Registro de Usuario**: `POST /api/usuarios`
    ```json
    {
        "nombre": "Usuario",
        "email": "usuario@example.com",
        "contrasena": "password123"
    }
    ```

- **Autenticación de Usuario**: `POST /api/autenticacion`
    ```json
    {
        "email": "usuario@example.com",
        "contrasena": "password123"
    }
    ```

### Tópicos

- **Crear Tópico**: `POST /api/topicos`
    ```json
    {
        "titulo": "Nuevo Tópico",
        "contenido": "Contenido del tópico",
        "autorId": 1
    }
    ```

- **Obtener Tópicos**: `GET /api/topicos`

- **Actualizar Tópico**: `PUT /api/topicos/{id}`
    ```json
    {
        "titulo": "Título Actualizado",
        "contenido": "Contenido Actualizado"
    }
    ```

- **Eliminar Tópico**: `DELETE /api/topicos/{id}`
