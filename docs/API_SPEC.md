# API Specification for E-commerce Platform

## Overview
This document outlines the API specifications for the E-commerce Platform maintained under the TamHocDev organization.

## Base URL
The base URL for the API is `https://api.ecommerce-platform.com/v1`

## Authentication
All API requests require an authentication token. You can obtain a token by logging into your account and navigating to the API section of your profile.

### Header
- `Authorization: Bearer <your_token>`

## Endpoints

### 1. Products
#### GET /products
- Retrieve a list of products.
- **Query Parameters:**
  - `category` (optional): Filter products by category.
  - `limit` (optional): Number of products to return.

#### POST /products
- Create a new product.
- **Body:**
  ```json
  {
    "name": "Product Name",
    "price": 99.99,
    "category": "Category Name",
    "description": "Product description here."
  }
  ```

### 2. Orders
#### GET /orders
- Retrieve a list of orders for authenticated user.

#### POST /orders
- Create a new order.
- **Body:**
  ```json
  {
    "product_id": 123,
    "quantity": 2,
    "shipping_address": "Address here"
  }
  ```

### 3. Users
#### POST /users/register
- Register a new user.
- **Body:**
  ```json
  {
    "username": "newuser",
    "password": "securepassword",
    "email": "user@example.com"
  }
  ```

#### POST /users/login
- User login.
- **Body:**
  ```json
  {
    "username": "existinguser",
    "password": "securepassword"
  }
  ```

## Error Handling
All error responses will include an HTTP status code and a message.
- **Example:**
  ```json
  {
    "error": "Invalid request",
    "message": "Product ID is required."
  }
  ```

## Rate Limiting
To prevent abuse, all APIs are rate limited to 100 requests per hour per user.

## FAQs
- **How do I get an API token?**
  You can acquire your API token from the API section of your profile after logging in.

- **Where do I report bugs?**
  Bugs can be reported on our GitHub repository under the issues section.

## Conclusion
This API specification should provide developers with a clear understanding of how to interact with the E-commerce Platform API.