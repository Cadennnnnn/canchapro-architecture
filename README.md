# CanchaPro Architecture

Proyecto desarrollado para la asignatura Desarrollo FullStack I - DSY1103.

CanchaPro es un sistema de gestion de reservas de canchas deportivas desarrollado con arquitectura de microservicios usando Spring Boot, Spring Cloud, Eureka Server, API Gateway, bases de datos independientes y comunicacion REST entre servicios.

---

## 1. Enlaces de entrega

| Recurso                       | Enlace                                  |
| ----------------------------- | --------------------------------------- |
| Version ejecutable sin Docker | Pendiente - agregar link Google Drive   |
| Version con Docker            | Pendiente para Examen Transversal       |
| Video defensa tecnica         | Pendiente - agregar link del video      |
| Repositorio GitHub            | Pendiente - agregar URL del repositorio |

---

## 2. Integrantes

| Nombre                         | Rol                                                                    |
| ------------------------------ | ---------------------------------------------------------------------- |
| Caden Alexander Nieto Gonzalez | Desarrollo de microservicios, testing, documentacion y defensa tecnica |
| Sebastian De La Fuente         | Desarrollo de microservicios, apoyo tecnico y documentacion            |

---

## 3. Objetivo del proyecto

El objetivo del proyecto es implementar un sistema distribuido para gestionar reservas de canchas deportivas.

El flujo principal del sistema es:

Usuario -> Cancha -> Disponibilidad -> Reserva -> Pago -> Notificacion -> Calificacion -> Reportes

---

## 4. Arquitectura general

El sistema utiliza arquitectura de microservicios. Cada servicio tiene responsabilidades separadas y se comunica mediante endpoints REST.

Componentes principales:

* Eureka Server para descubrimiento de servicios.
* API Gateway para centralizar el acceso a los microservicios.
* Microservicios independientes con Spring Boot.
* Bases de datos independientes por servicio.
* Comunicacion REST entre servicios.
* Validaciones con Bean Validation.
* Manejo global de excepciones.
* Documentacion Swagger/OpenAPI.
* Pruebas con JUnit 5, Mockito y MockMvc.

---

## 5. Microservicios del sistema

| Servicio          | Puerto | Responsabilidad                             |
| ----------------- | -----: | ------------------------------------------- |
| eureka-server     |   8761 | Registro y descubrimiento de microservicios |
| api-gateway       |   8080 | Entrada central del sistema                 |
| auth-service      |   8081 | Registro, login, JWT, BCrypt y roles        |
| ms-usuarios       |   8082 | Gestion de usuarios                         |
| ms-canchas        |   8083 | Gestion de canchas deportivas               |
| ms-disponibilidad |   8085 | Gestion de horarios disponibles             |
| ms-pagos          |   8086 | Registro y validacion de pagos              |
| ms-reservas       |   8087 | Gestion de reservas                         |
| ms-notificaciones |   8088 | Gestion de notificaciones                   |
| ms-calificaciones |   8089 | Gestion de calificaciones                   |
| ms-reportes       |   8090 | Generacion y consulta de reportes           |

---

## 6. Tecnologias utilizadas

* Java 21
* Spring Boot 3.5.14
* Spring Cloud
* Spring Web
* Spring Data JPA
* Spring Security
* JWT
* BCrypt
* Eureka Server
* API Gateway
* MySQL
* Maven
* JUnit 5
* Mockito
* MockMvc
* Swagger/OpenAPI
* Postman
* Git y GitHub

---

## 7. Requisitos previos

Para ejecutar el proyecto se necesita:

* Java 21 instalado
* Maven instalado
* MySQL activo en el puerto 3306
* Puerto 8761 disponible para Eureka
* Puerto 8080 disponible para API Gateway
* Puertos 8081, 8082, 8083, 8085, 8086, 8087, 8088, 8089 y 8090 disponibles para microservicios

Configuracion local usada:

* MySQL host: localhost
* MySQL port: 3306
* Usuario: root
* Password: vacio

---

## 8. Ejecucion desde codigo fuente

Desde la raiz del proyecto:

```powershell
mvn clean install
```

Luego levantar los servicios en este orden:

```text
1. eureka-server
2. auth-service
3. ms-usuarios
4. ms-canchas
5. ms-disponibilidad
6. ms-pagos
7. ms-reservas
8. ms-notificaciones
9. ms-calificaciones
10. ms-reportes
11. api-gateway
```

---

## 9. Ejecucion sin Docker

La version sin Docker se entrega en una carpeta externa llamada:

```text
CanchaPro-Distribucion/sin-docker
```

Contenido principal:

```text
arrancar-nativo.bat
apps/eureka-server.jar
apps/api-gateway.jar
apps/auth-service.jar
apps/ms-usuarios.jar
apps/ms-canchas.jar
apps/ms-disponibilidad.jar
apps/ms-reservas.jar
apps/ms-pagos.jar
apps/ms-notificaciones.jar
apps/ms-calificaciones.jar
apps/ms-reportes.jar
```

Para ejecutar:

```powershell
arrancar-nativo.bat
```

El archivo levanta automaticamente Eureka, los microservicios y finalmente el API Gateway.

---

## 10. URLs principales

| Servicio       | URL                   |
| -------------- | --------------------- |
| Eureka         | http://localhost:8761 |
| API Gateway    | http://localhost:8080 |
| Auth Service   | http://localhost:8081 |
| Usuarios       | http://localhost:8082 |
| Canchas        | http://localhost:8083 |
| Disponibilidad | http://localhost:8085 |
| Pagos          | http://localhost:8086 |
| Reservas       | http://localhost:8087 |
| Notificaciones | http://localhost:8088 |
| Calificaciones | http://localhost:8089 |
| Reportes       | http://localhost:8090 |

---

## 11. Swagger/OpenAPI

| Servicio          | Swagger                                     |
| ----------------- | ------------------------------------------- |
| auth-service      | http://localhost:8081/swagger-ui/index.html |
| ms-usuarios       | http://localhost:8082/swagger-ui/index.html |
| ms-canchas        | http://localhost:8083/swagger-ui/index.html |
| ms-disponibilidad | http://localhost:8085/swagger-ui/index.html |
| ms-pagos          | http://localhost:8086/swagger-ui/index.html |
| ms-reservas       | http://localhost:8087/swagger-ui/index.html |
| ms-notificaciones | http://localhost:8088/swagger-ui/index.html |
| ms-calificaciones | http://localhost:8089/swagger-ui/index.html |
| ms-reportes       | http://localhost:8090/swagger-ui/index.html |

---

## 12. Rutas principales por API Gateway

URL base:

```text
http://localhost:8080
```

Endpoints principales:

```text
/api/auth
/api/usuarios
/api/canchas
/api/disponibilidad
/api/pagos
/api/reservas
/api/notificaciones
/api/calificaciones
/api/reportes
```

Pruebas realizadas por Gateway:

```text
GET /api/canchas
GET /api/usuarios
GET /api/disponibilidad
GET /api/pagos
GET /api/reservas
GET /api/notificaciones
GET /api/calificaciones
GET /api/reportes
```

Resultado general:

```text
StatusCode: 200 OK
```

---

## 13. Seguridad

El proyecto implementa seguridad en auth-service mediante:

* Registro de usuarios.
* Login.
* Generacion de token JWT.
* Encriptacion de password con BCrypt.
* Roles de usuario.
* Endpoints publicos para register y login.
* Endpoints protegidos para validar autenticacion y autorizacion.

Endpoints principales:

```text
POST /api/auth/register
POST /api/auth/login
GET /api/auth/test
GET /api/auth/admin
```

---

## 14. Testing

Se implementaron pruebas con:

* JUnit 5
* Mockito
* MockMvc
* Spring Boot Test

Tipos de pruebas:

```text
ApplicationTests: validan que el contexto Spring Boot cargue correctamente.
ServiceTest: validan reglas de negocio, excepciones y uso de repositorios.
ControllerTest: validan endpoints, codigos HTTP, validaciones y respuestas.
```

Servicios con pruebas unitarias y de controller:

```text
auth-service
ms-usuarios
ms-canchas
ms-disponibilidad
ms-reservas
ms-pagos
ms-notificaciones
ms-calificaciones
ms-reportes
```

Ejecucion de pruebas:

```powershell
mvn clean test
```

Resultado obtenido:

```text
BUILD SUCCESS
Total time: 05:48 min
```

Ejecucion de build final:

```powershell
mvn clean install
```

Resultado obtenido:

```text
BUILD SUCCESS
Total time: 05:54 min
```

---

## 15. Evidencias

La documentacion de evidencia se encuentra en:

```text
docs/evidencias-testing-y-ejecucion.md
```

Esta evidencia incluye:

* Resultado de mvn clean test.
* Resultado de mvn clean install.
* Servicios registrados en Eureka.
* Endpoints probados por API Gateway.
* Validacion de Swagger/OpenAPI.
* Distribucion sin Docker con archivos .jar.

---

## 16. Estructura general

```text
CanchaPro(FINAL)
├── eureka-server
├── api-gateway
├── auth-service
├── ms-usuarios
├── ms-canchas
├── ms-disponibilidad
├── ms-reservas
├── ms-pagos
├── ms-notificaciones
├── ms-calificaciones
├── ms-reportes
├── docs
├── pom.xml
├── README.md
└── .gitignore
```

---

## 17. Estado final

Estado del proyecto:

```text
Microservicios implementados: 11
Eureka funcionando: SI
API Gateway funcionando: SI
Swagger/OpenAPI funcionando: SI
Pruebas Maven completas: BUILD SUCCESS
Build final: BUILD SUCCESS
Distribucion sin Docker: generada y probada
Endpoints por Gateway: StatusCode 200 OK
```

---

## 18. Notas para la defensa tecnica

Durante la defensa se puede explicar:

* La arquitectura esta separada por microservicios independientes.
* Eureka registra todos los servicios y permite descubrimiento.
* API Gateway centraliza las peticiones.
* Cada microservicio mantiene su propia responsabilidad.
* Se aplico patron Controller-Service-Repository.
* Se utilizaron DTOs para entrada y salida de datos.
* Se aplicaron validaciones con Bean Validation.
* Se implemento manejo global de excepciones.
* Auth-service usa JWT, BCrypt y roles.
* Se implementaron pruebas unitarias y de controller.
* La distribucion sin Docker permite ejecutar el sistema desde archivos .jar.

---

## 19. Comandos utiles

Compilar y ejecutar pruebas:

```powershell
mvn clean test
```

Generar build final:

```powershell
mvn clean install
```

Ejecutar distribucion sin Docker:

```powershell
arrancar-nativo.bat
```

Probar Gateway:

```powershell
Invoke-WebRequest http://localhost:8080/api/canchas -UseBasicParsing
```

Probar Swagger/OpenAPI:

```powershell
Invoke-WebRequest http://localhost:8081/v3/api-docs -UseBasicParsing
```
