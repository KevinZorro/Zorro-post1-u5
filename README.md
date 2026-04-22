## Capturas

# Crear un libro
<img width="660" height="487" alt="image" src="https://github.com/user-attachments/assets/635e1e06-5e7a-4825-9c3c-49d31009308f" />

# Listar todos los libros
<img width="610" height="346" alt="image" src="https://github.com/user-attachments/assets/799c2d4e-6ac8-4cee-a8c2-f2d0bb5ed6d1" />

# Buscar por palabra
<img width="682" height="347" alt="image" src="https://github.com/user-attachments/assets/97dca185-dd72-4c24-b4e8-971355761fec" />

# Eliminar libro con id=1
<img width="606" height="174" alt="image" src="https://github.com/user-attachments/assets/046da4dd-0d58-4ea4-b795-a3ef7ec92bb7" />

# Eliminar libro que no existe
<img width="635" height="271" alt="image" src="https://github.com/user-attachments/assets/16dec3bd-62a6-40ef-9ed1-3e99308ac608" />

# Base de datos en H2
<img width="623" height="263" alt="image" src="https://github.com/user-attachments/assets/84b320d6-d5aa-416c-8708-49056a161e64" />


# biblioteca-api

API REST de gestión de biblioteca construida con **Spring Boot 3.2**, 
**Spring Data JPA** (patrón Repository) y **H2** como base de datos embebida.
Implementa la arquitectura en capas: **Entity → Repository → Service → Controller**.

## Arquitectura
HTTP Request
│
▼
LibroController ← solo maneja HTTP (códigos de estado, ResponseEntity)
│
▼
LibroService ← toda la lógica de negocio (validaciones, unicidad)
│
▼
LibroRepository ← Spring Data JPA genera la implementación en runtime
│
▼
H2 Database ← tabla "libros" creada automáticamente por Hibernate

## Requisitos

- Java 17+
- Maven 3.8+ (o usar `./mvnw` incluido)

## Ejecución

```bash
git clone https://github.com/<KevinZorro>/Zorro-post1-u5.git
cd Zorro-post1-u5
mvn clean package
mvn spring-boot:run
```

La aplicación levanta en **http://localhost:8080**  
Consola H2: **http://localhost:8080/h2-console** (JDBC URL: `jdbc:h2:mem:biblioteca_db`, usuario: `sa`)

## Endpoints REST

| Método | URL                          | Descripción                        | Código |
|--------|------------------------------|------------------------------------|--------|
| GET    | `/api/libros`                | Lista todos los libros             | 200    |
| GET    | `/api/libros/{id}`           | Obtiene un libro por ID            | 200/404|
| POST   | `/api/libros`                | Crea un nuevo libro                | 201    |
| PUT    | `/api/libros/{id}`           | Actualiza un libro existente       | 200/404|
| DELETE | `/api/libros/{id}`           | Elimina un libro                   | 204/404|
| GET    | `/api/libros/buscar?q=texto` | Busca por palabra en el título     | 200    |
| GET    | `/api/libros/autor?nombre=X` | Busca libros por autor             | 200    |
