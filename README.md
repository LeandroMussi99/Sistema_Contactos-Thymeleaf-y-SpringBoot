# 📇 Sistema de Contactos (Spring Boot + Thymeleaf)

Aplicación web CRUD desarrollada con **Spring Boot 3**, **Thymeleaf** y **Spring Data JPA** para la gestión de contactos.  
Permite registrar, editar y eliminar contactos almacenados en una base de datos **MySQL**, con una interfaz moderna basada en **Bootstrap**.

---

## 🖼️ Vista general

> Interfaz principal del sistema de contactos y formulario para agregar un nuevo registro.

<img width="1426" height="518" alt="Sistema Contactos " src="https://github.com/user-attachments/assets/ffecc061-95ea-4ca7-83fe-72bc3b4d5aa8" />

<img width="1424" height="564" alt="Sistema Contactos agregar" src="https://github.com/user-attachments/assets/a86b36ce-effa-4b12-8a20-d14a7d1b7921" />

---

## ✨ Características principales

- 📋 **Listado de contactos** en tabla con acciones de edición y eliminación.  
- 🧾 **Formulario de alta y edición** con validaciones en el navegador.  
- ⚙️ **Arquitectura en capas:** Controlador → Servicio → Repositorio → Entidad.  
- 🗄️ **Persistencia JPA/Hibernate** con gestión automática del esquema (`ddl-auto=update`).  
- 🧱 **Plantillas Thymeleaf** con fragmentos reutilizables (`cabecero`, `navegacion`, `pie-pagina`).  
- 🔍 **Registro de eventos** con **SLF4J** para depuración de operaciones CRUD.  

---

## 🧩 Estructura del proyecto

```text
├── pom.xml                         # Dependencias y configuración de Maven
├── src
│   ├── main
│   │   ├── java/lm/contactos/
│   │   │   ├── ContactosApplication.java        # Clase principal
│   │   │   ├── controlador/ContactoControlador  # Controladores web
│   │   │   ├── modelo/Contacto.java             # Entidad JPA
│   │   │   ├── repositorio/ContactoRepositorio  # Interfaz JpaRepository
│   │   │   └── servicio/                        # Capa de servicio
│   │   └── resources/
│   │       ├── templates/                       # Vistas Thymeleaf
│   │       │   ├── index.html
│   │       │   ├── modificar.html
│   │       │   ├── agregar.html
│   │       │   └── fragmentos/
│   │       │       ├── cabecero.html
│   │       │       ├── navegacion.html
│   │       │       └── pie-pagina.html
│   │       ├── application.properties           # Configuración de base de datos
│   │       └── logback-spring.xml               # Logging
└── test/
    └── java/lm/contactos/ContactosApplicationTests.java
```

## 🧰 Requisitos previos

Java 21
Maven 3.9+
MySQL 8 o compatible
(Opcional) Plugin de Lombok en tu IDE (IntelliJ, Eclipse o VS Code)

## ⚙️ Configuración
Editá el archivo src/main/resources/application.properties con tus credenciales de base de datos:

spring.datasource.url=jdbc:mysql://localhost:3306/contactos_db?createDatabaseIfNotExist=true&useSSL=false&serverTimezone=UTC
spring.datasource.username=tu_usuario
spring.datasource.password=tu_contraseña
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

✅ La base contactos_db se crea automáticamente si no existe.

## 🚀 Ejecución

Desde consola: mvn spring-boot:run O desde tu IDE ejecutando la clase: ContactosApplication

La aplicación estará disponible en 👉 http://localhost:8080

## 🧭 Flujo funcional

1. Inicio (/) – Muestra el listado de contactos.
2. Agregar (/agregar) – Formulario para crear un nuevo contacto.
3. Editar (/editar/{id}) – Carga el contacto seleccionado para modificar.
4. Eliminar (/eliminar/{id}) – Borra el registro y redirige al listado.
