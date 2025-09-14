# Blogging_Application

A Spring Boot-based RESTful API backend for a blogging platform, supporting user management, posts, and categories, with role-based access and modular service structure.

## Features

- User registration, CRUD, and role-based access (admin/user)
- Post creation, editing, deletion, listing, and search with pagination and sorting
- Category management (CRUD)
- Search posts by title keywords
- Modular service, repository, and controller structure
- Uses ModelMapper for DTO/entity conversion
- Prepared for Swagger/OpenAPI docs (Swagger config included)
- Standard exception handling and validation

## REST API Endpoints

### User APIs

- `POST   /api/users/` — Create user
- `PUT    /api/users/{userId}` — Update user
- `DELETE /api/users/{userId}` — Delete user (**admin only**)
- `GET    /api/users/{userId}` — Get user by ID
- `GET    /api/users/` — List all users

### Category APIs

- `POST   /api/categories/` — Create category
- `PUT    /api/categories/{categoryId}` — Update category
- `DELETE /api/categories/{categoryId}` — Delete category
- `GET    /api/categories/{categoryId}` — Get category by ID
- `GET    /api/categories/` — List all categories

### Post APIs

- `POST   /api/user/{userId}/category/{categoryId}/posts` — Create post for a user in a category
- `PUT    /api/posts/{postId}` — Update post
- `DELETE /api/posts/{postId}` — Delete post
- `GET    /api/posts/{postId}` — Get post by ID
- `GET    /api/posts` — Get all posts (pagination, sorting)
    - Query params: `PageNumber`, `PageSize`, `sortBy`, `sortDir`
- `GET    /api/user/{userId}/posts` — Get all posts by user
- `GET    /api/category/{categoryId}/posts` — Get all posts in a category
- `GET    /api/posts/search/{keywords}` — Search posts by title keywords

## Project Structure

```
src/main/java/com/blog/
├── controllers/    // REST controllers for User, Post, Category
├── entities/       // JPA entities (User, Post, Category, Role, etc.)
├── exceptions/     // Custom exceptions (e.g. ResourceNotFoundException)
├── payloads/       // DTOs and API response payloads
├── repositories/   // Spring Data JPA repositories
├── service/        // Service interfaces and implementations
│   └── impl/
├── config/         // App & Swagger configuration
└── BlogAppApisApplication.java // Main entry point
```

## Getting Started

1. **Clone the repo**
   ```bash
   git clone https://github.com/RatnadeepGhosh/Blogging_Application.git
   cd Blogging_Application
   ```
2. **Configure your database** in `src/main/resources/application.properties`
3. **Build & run**
   ```bash
   mvn clean install
   mvn spring-boot:run
   ```
4. **API docs**: Swagger config is included (see `SwaggerConfig.java`), enable as needed.

## Technologies

- Java, Spring Boot, Spring Data JPA, Spring Security
- ModelMapper
- (Prepared for) Swagger/OpenAPI for documentation
