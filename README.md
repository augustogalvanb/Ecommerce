# Ecommerce Backend API

Backend de una aplicación de ecommerce desarrollada con **NestJS** y **PostgreSQL**. Esta API permite la gestión de usuarios, productos, categorías, órdenes de compra y carga de imágenes, con autenticación basada en JWT y roles de acceso (admin y user). Incluye documentación interactiva mediante **Swagger/OpenAPI**.

El proyecto está diseñado como una base sólida para una tienda online y está pensado para ser escalable y fácil de integrar con un frontend en el futuro.

## Estado del Proyecto

En desarrollo activo (versión inicial). El backend está funcional, pero faltan algunas características avanzadas como la compra de múltiples productos de la misma categoría y un frontend.

## Características Principales

- **Autenticación y Autorización**: Registro e inicio de sesión con JWT. Roles de usuario (admin y user) implementados mediante guardas en los endpoints.
- **Gestión de Usuarios**: CRUD completo para usuarios (admin puede listar, editar y eliminar usuarios).
- **Gestión de Productos**: CRUD de productos con carga de imágenes a través de **Cloudinary**.
- **Órdenes de Compra**: Creación de órdenes con detalles (precio final y descuento de stock).
- **Seguridad**: Contraseñas hasheadas con **bcrypt**.
- **Documentación**: API documentada con Swagger, accesible en `/api`.

## Tecnologías Utilizadas

- **NestJS**: Framework backend de Node.js.
- **PostgreSQL**: Base de datos relacional.
- **JWT**: Autenticación basada en tokens.
- **Bcrypt**: Hashing de contraseñas.
- **Cloudinary**: Almacenamiento de imágenes.
- **Swagger/OpenAPI**: Documentación interactiva de la API.
- **TypeORM**: ORM para la gestión de la base de datos.

## Requisitos Previos

- Node.js (versión 16.x o superior)
- PostgreSQL (instalado y configurado)
- Cuenta en Cloudinary (para la carga de imágenes)
- npm o yarn como gestor de paquetes

## Instalación

1. Clona el repositorio:
   ```bash
   git clone https://github.com/tu-usuario/ecommerce-backend.git
   cd ecommerce-backend

2. Instala las dependencias:
    ```bash
    npm install
    ```

3. Configura las variables de entorno en un archivo .env (basado en .env.example):
    ```js
    DATABASE_HOST=localhost
    DATABASE_PORT=5432
    DATABASE_USER=tu_usuario
    DATABASE_PASSWORD=tu_contraseña
    DATABASE_NAME=ecommerce_db
    JWT_SECRET=tu_secreto_jwt
    CLOUDINARY_CLOUD_NAME=tu_cloud_name
    CLOUDINARY_API_KEY=tu_api_key
    CLOUDINARY_API_SECRET=tu_api_secret
    ```

4. Configura la base de datos:
- Crea una base de datos en PostgreSQL llamada ecommerce_db
- Ejecuta las migraciones (si aplica) o sincroniza manualmente con TypeORM.

5. Inicia el servidor:
    ```bash
    npm start
    ```
6. Accede a la documentación de la API en: http://localhost:3000/api

## Uso

- Usa Swagger (/api) para probar los endpoints directamente desde el navegador.
- Registra un usuario mediante POST /auth/signup y obtén un token JWT con POST /auth/signin.
- Usa el token en el header Authorization: Bearer <token> para acceder a endpoints protegidos.
- Prueba la creación de órdenes con POST /orders o la carga de imágenes con POST /files/uploadImage/:id.

## Endpoints Principales

| Método | Endpoint                  | Descripción                        | Rol Requerido |
|--------|---------------------------|------------------------------------|---------------|
| GET    | /users                   | Lista todos los usuarios          | Admin         |
| GET    | /users/:id               | Obtiene un usuario por ID         | Admin         |
| POST   | /auth/signup             | Registra un nuevo usuario         | Público       |
| POST   | /auth/signin             | Inicia sesión y retorna JWT       | Público       |
| GET    | /products                | Lista todos los productos         | Público       |
| POST   | /products                | Crea un nuevo producto            | Admin         |
| POST   | /orders                  | Crea una nueva orden de compra    | User          |
| POST   | /files/uploadImage/:id   | Carga una imagen para un producto | Admin         |

Consulta la documentación completa en Swagger para más detalles.

## Funcionalidades Pendientes

- Permitir la compra de múltiples productos de la misma categoría (ej. 2 gaseosas).
- Implementar un frontend para consumir la API.
- Agregar filtros y paginación en los endpoints de listado (/users, /products).
- Mejorar la validación de datos y manejo de errores.