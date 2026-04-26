## Cómo ejecutar localmente

### auth-service
cd microservicios-demoacademico/auth-service
./mvnw spring-boot:run

### consulta-service
cd microservicios-demoacademico/consulta-service
./mvnw spring-boot:run

## Cómo levantar con Docker Compose
cd microservicios-demoacademico
docker compose up --build

## URLs
### auth-service
- Swagger: http://localhost:8081/swagger-ui.html
- H2 Console: http://localhost:8081/h2-console
  - JDBC URL: jdbc:h2:mem:authdb
  - Usuario: sa
  - Contraseña: (vacía)

### consulta-service
- Swagger: http://localhost:8082/swagger-ui.html
- H2 Console: http://localhost:8082/h2-console
  - JDBC URL: jdbc:h2:mem:demoacademico
  - Usuario: sa
  - Contraseña: (vacía)

Nota: en Docker, la consola H2 no permite conexiones remotas,
por lo que solo está disponible al ejecutar localmente.

## Usuarios de prueba
| Usuario     | Contraseña   | Rol        |
|-------------|--------------|------------|
| admin       | Admin2026*   | ADMIN      |
| docente     | Docente2026* | DOCENTE    |
| estudiante1 | Estu2026*    | ESTUDIANTE |

## Flujo de uso del botón Authorize
1. Ir a Swagger de auth-service (http://localhost:8081/swagger-ui.html)
2. Ejecutar POST /auth/login con usuario y contraseña
3. Copiar el valor del campo "token" (sin comillas, sin "Bearer")
4. Ir a Swagger de consulta-service (http://localhost:8082/swagger-ui.html)
5. Hacer clic en el botón Authorize
6. Pegar solo el token (sin el prefijo Bearer)
7. Hacer clic en Authorize y cerrar
8. Ejecutar GET /api/estudiantes
