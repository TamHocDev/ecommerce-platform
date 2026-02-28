# Database Schema for Ecommerce Platform

## 1. Users
- **Table Name**: `users`
- **Columns**:
  - `id`: SERIAL PRIMARY KEY
  - `username`: VARCHAR(50) UNIQUE NOT NULL
  - `email`: VARCHAR(100) UNIQUE NOT NULL
  - `password_hash`: VARCHAR(255) NOT NULL
  - `created_at`: TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  - `updated_at`: TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP

## 2. Products
- **Table Name**: `products`
- **Columns**:
  - `id`: SERIAL PRIMARY KEY
  - `name`: VARCHAR(150) NOT NULL
  - `description`: TEXT
  - `price`: DECIMAL(10, 2) NOT NULL
  - `created_at`: TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  - `updated_at`: TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
  - `inventory_id`: INT REFERENCES inventory(id)

## 3. Orders
- **Table Name**: `orders`
- **Columns**:
  - `id`: SERIAL PRIMARY KEY
  - `user_id`: INT REFERENCES users(id)
  - `order_status`: VARCHAR(50) NOT NULL
  - `total_amount`: DECIMAL(10, 2) NOT NULL
  - `created_at`: TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  - `updated_at`: TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP

## 4. Payments
- **Table Name**: `payments`
- **Columns**:
  - `id`: SERIAL PRIMARY KEY
  - `order_id`: INT REFERENCES orders(id)
  - `payment_status`: VARCHAR(50) NOT NULL
  - `payment_method`: VARCHAR(50) NOT NULL
  - `amount`: DECIMAL(10, 2) NOT NULL
  - `created_at`: TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  - `updated_at`: TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP

## 5. Inventory
- **Table Name**: `inventory`
- **Columns**:
  - `id`: SERIAL PRIMARY KEY
  - `product_id`: INT REFERENCES products(id) UNIQUE
  - `quantity`: INT NOT NULL
  - `created_at`: TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  - `updated_at`: TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP

## 6. Relationships
- **One-to-Many**: Users to Orders  
- **One-to-Many**: Orders to Payments  
- **One-to-One**: Products to Inventory  

## 7. Indexes
- **Users**: INDEX on `email` and `username`
- **Products**: INDEX on `name`
- **Orders**: INDEX on `user_id`
- **Payments**: INDEX on `order_id`
- **Inventory**: INDEX on `product_id`