## Product API
This is a RESTful API for managing products built with Express.js. It includes features for product management with filtering, pagination, and search capabilities.
Setup

## Ensure Node.js is installed
## Install dependencies:

npm install express body-parser uuid


## Run the server:

node server.js

The server will run on http://localhost:3000 by default.
API Endpoints
Authentication
## All endpoints require an Authorization header:
Authorization: Bearer mysecrettoken

GET /api/products
Retrieve all products with optional filtering, pagination, and search.
Query Parameters:

## search: Search products by name (string)
category: Filter by category (string)
inStock: Filter by stock status (true/false)
page: Page number for pagination (number, default: 1)
limit: Number of items per page (number, default: 10)

## Example Request:
GET /api/products?search=laptop&category=electronics&inStock=true&page=1&limit=10
Authorization: Bearer mysecrettoken

Example Response:
{
  "total": 1,
  "page": 1,
  "limit": 10,
  "products": [
    {
      "id": "1",
      "name": "Laptop",
      "description": "High-performance laptop with 16GB RAM",
      "price": 1200,
      "category": "electronics",
      "inStock": true
    }
  ]
}

## GET /api/products/:id
Retrieve a specific product by ID.
Example Request:
GET /api/products/1
Authorization: Bearer mysecrettoken

Example Response:
{
  "id": "1",
  "name": "Laptop",
  "description": "High-performance laptop with 16GB RAM",
  "price": 1200,
  "category": "electronics",
  "inStock": true
}

## POST /api/products
Create a new product.
Request Body:
{
  "name": "Tablet",
  "description": "10-inch tablet with 64GB storage",
  "price": 400,
  "category": "electronics",
  "inStock": true
}

## Example Request:
POST /api/products
Authorization: Bearer mysecrettoken
Content-Type: application/json

## Example Response:
{
  "id": "4",
  "name": "Tablet",
  "description": "10-inch tablet with 64GB storage",
  "price": 400,
  "category": "electronics",
  "inStock": true
}

## PUT /api/products/:id
Update an existing product.
Request Body:
{
  "name": "Updated Laptop",
  "description": "High-performance laptop with 32GB RAM",
  "price": 1500,
  "category": "electronics",
  "inStock": true
}

## Example Request:
PUT /api/products/1
Authorization: Bearer mysecrettoken
Content-Type: application/json

## Example Response:
{
  "id": "1",
  "name": "Updated Laptop",
  "description": imitateHigh-performance laptop with 32GB RAM",
  "price": 1500,
  "category": "electronics",
  "inStock": true
}

DELETE /api/products/:id
Delete a product by ID.
Example Request:
DELETE /api/products/1
Authorization: Bearer mysecrettoken

## Example Response:Status: 204 No Content
Error Handling

400: Bad Request - Invalid input data
401: Unauthorized - Invalid or missing authentication token
404: Not Found - Product not found
500: Internal Server Error - Server error

## Middleware

Request logging: Logs all incoming requests with timestamp and method
Authentication: Requires a bearer token
Validation: Ensures all required fields are present and valid
