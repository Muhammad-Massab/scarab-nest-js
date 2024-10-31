
# Products API

This is a NestJS application that provides a RESTful API for managing products. The API includes endpoints for creating, retrieving, updating, and deleting products.

## Features

- RESTful API for managing products
- CRUD operations for `/products`
- Docker support for containerized development and deployment

## Prerequisites

Ensure you have the following installed:

- **Docker** (for Docker Compose setup)
- **Node.js** and **npm** (for local setup without Docker)

## Getting Started

### Environment Variables

Update the `.env` file with the necessary environment variables. You may need to specify values for database connection and other settings depending on your environment.

Example `.env`:

```plaintext
DB_HOST=your_database_host
DB_PORT=your_database_port
DB_USERNAME=your_database_user
DB_PASSWORD=your_database_password
DB_NAME=your_database_name
```

### Running with Docker Compose

1. **Build and run** the application using Docker Compose:

   ```bash
   docker-compose up --build
   ```

   This command will build the Docker image and start the application along with any dependencies (e.g., a database if configured in the `docker-compose.yml` file).

2. The API will be available at `http://localhost:3000/products` by default.

### Running Locally (without Docker)

1. Install dependencies:

   ```bash
   npm install
   ```

2. Start the server:

   ```bash
   npm run start
   ```

3. The API will be accessible at `http://localhost:3000/products`.

## API Endpoints

This application only provides endpoints under the `/products` route.

### POST /products

Creates a new product.

- **Request Body**: Partial object of `Product` containing fields like `name`, `price`, `description`, etc.
- **Response**: Created `Product` object.
- **Error**: Returns `400 Bad Request` if creation fails.

### GET /products

Retrieves all products.

- **Response**: Array of `Product` objects.

### GET /products/:id

Retrieves a single product by `id`.

- **URL Parameter**: `id` - ID of the product.
- **Response**: `Product` object.
- **Error**: Returns `404 Not Found` if the product is not found.

### PUT /products/:id

Updates a product by `id`.

- **URL Parameter**: `id` - ID of the product.
- **Request Body**: Partial object of `Product` containing fields to update.
- **Response**: Updated `Product` object.
- **Error**: Returns `404 Not Found` if the product is not found.

### DELETE /products/:id

Deletes a product by `id`.

- **URL Parameter**: `id` - ID of the product.
- **Response**: Returns `200 OK` if deletion is successful.
- **Error**: Returns `404 Not Found` if the product is not found.

---

## Error Handling

Errors are handled with appropriate HTTP status codes:
- **400** - Bad Request (e.g., if creation fails)
- **404** - Not Found (e.g., if a product is not found)
