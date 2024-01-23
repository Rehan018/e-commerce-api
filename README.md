# E-Commerce API Documentation

## Overview

This repository contains the source code for an E-Commerce API built using Node.js, Express.js, and MongoDB. The API provides functionality for user authentication, managing products, handling shopping carts, processing orders, and more. Below, you'll find detailed documentation on the API's features, technologies used, and instructions for setup.

## Features

### 1. User Authentication

- **Register User**
  - Endpoint: `POST /api/v1/auth/register`
  - Description: Creates a new user account.
  - Request Body:
    ```json
    {
      "username": "example",
      "email": "example@example.com",
      "password": "password123"
    }
    ```
  - Response:
    ```json
    {
      "type": "success",
      "message": "User has been created successfully",
      "user": { ...userDetails }
    }
    ```

- **Login User**
  - Endpoint: `POST /api/v1/auth/login`
  - Description: Logs in an existing user.
  - Request Body:
    ```json
    {
      "username": "example",
      "password": "password123"
    }
    ```
  - Response:
    ```json
    {
      "type": "success",
      "message": "Successfully logged",
      "user": { ...userDetails },
      "accessToken": "eyJhbGciOiJIUzI1NiIsIn..."
    }
    ```

### 2. User Management

- **Get All Users (Admin)**
  - Endpoint: `GET /api/v1/users`
  - Description: Retrieves a list of all users (admin access required).
  - Response:
    ```json
    {
      "type": "success",
      "users": [ ...userList ]
    }
    ```

- **Get User by ID (Admin)**
  - Endpoint: `GET /api/v1/users/:id`
  - Description: Retrieves user details by user ID (admin access required).
  - Response:
    ```json
    {
      "type": "success",
      "data": { ...userDetails }
    }
    ```

- **Get User Statistics (Admin)**
  - Endpoint: `GET /api/v1/users/stats`
  - Description: Retrieves user registration statistics for the past year (admin access required).
  - Response:
    ```json
    {
      "type": "success",
      "data": [ { "month": 1, "total": 10 }, ... ]
    }
    ```

- **Update User**
  - Endpoint: `PUT /api/v1/users/:id`
  - Description: Updates user details.
  - Request Body:
    ```json
    {
      "username": "newusername",
      "email": "newemail@example.com",
      "password": "newpassword123"
    }
    ```
  - Response:
    ```json
    {
      "type": "success",
      "message": "User updated successfully",
      "updatedUser": { ...updatedUserDetails }
    }
    ```

- **Delete User (Admin)**
  - Endpoint: `DELETE /api/v1/users/:id`
  - Description: Deletes a user by ID (admin access required).
  - Response:
    ```json
    {
      "type": "success",
      "message": "User has been deleted successfully"
    }
    ```

### 3. Product Management

- **Get All Products**
  - Endpoint: `GET /api/v1/products`
  - Description: Retrieves a list of all products.
  - Query Parameters:
    - `new`: Get latest products (optional).
    - `category`: Filter by category (optional).
  - Response:
    ```json
    {
      "type": "success",
      "products": [ ...productList ]
    }
    ```

- **Get Product by ID**
  - Endpoint: `GET /api/v1/products/:id`
  - Description: Retrieves product details by ID.
  - Response:
    ```json
    {
      "type": "success",
      "product": { ...productDetails }
    }
    ```

- **Create New Product (Admin)**
  - Endpoint: `POST /api/v1/products`
  - Description: Adds a new product (admin access required).
  - Request Body:
    ```json
    {
      "title": "New Product",
      "description": "Product description",
      "image": "image-url.jpg",
      "categories": ["category1", "category2"],
      "size": "M",
      "color": "Blue",
      "price": 29.99
    }
    ```
  - Response:
    ```json
    {
      "type": "success",
      "message": "Product created successfully",
      "savedProduct": { ...newProductDetails }
    }
    ```

- **Update Product (Admin)**
  - Endpoint: `PUT /api/v1/products/:id`
  - Description: Updates product details (admin access required).
  - Request Body:
    ```json
    {
      "title": "Updated Product",
      "description": "Updated description",
      "price": 39.99
    }
    ```
  - Response:
    ```json
    {
      "type": "success",
      "message": "Product updated successfully",
      "updatedProduct": { ...updatedProductDetails }
    }
    ```

- **Delete Product (Admin)**
  - Endpoint: `DELETE /api/v1/products/:id`
  - Description: Deletes a product by ID (admin access required).
  - Response:
    ```json
    {
      "type": "success",
      "message": "Product has been deleted successfully"
    }
    ```

### 4. Shopping Cart Management

- **Get All Carts (Admin)**
  - Endpoint: `GET /api/v1/carts`
  - Description: Retrieves a list of all shopping carts (admin access required).
  - Response:
    ```json
    {
      "type": "success",
      "carts": [ ...cartList ]
    }
    ```

- **Get User Cart**
  - Endpoint: `GET /api/v1/carts/:userId`
  - Description: Retrieves the shopping cart for a specific user.
  - Response:
    ```json
    {
      "type": "success",
      "cart": { ...userCartDetails }
    }
    ```

- **Add Product to Cart**
  - Endpoint: `POST /api/v1/carts`
  - Description: Adds a product to the user's shopping cart.
  - Request Body:
    ```json
    {
      "userId": "userId123",
      "products": [
        {
          "productId": "product1Id",
          "quantity": 2
        }
      ]
    }
    ```
  - Response:
    ```json
    {
      "type": "success",
      "message": "Product added successfully",
      "savedCart": { ...updatedCartDetails }
    }
    ```

- **Update Cart**
  - Endpoint: `PUT /api/v1/carts/:id`
  - Description: Updates the shopping cart for a user (admin or user access required).
  - Request Body:
    ```json
    {
      "products": [
        {
         

 "productId": "product2Id",
          "quantity": 3
        }
      ]
    }
    ```
  - Response:
    ```json
    {
      "type": "success",
      "message": "Cart updated successfully",
      "updatedCart": { ...updatedCartDetails }
    }
    ```

- **Delete Cart**
  - Endpoint: `DELETE /api/v1/carts/:id`
  - Description: Deletes a user's shopping cart by ID (admin or user access required).
  - Response:
    ```json
    {
      "type": "success",
      "message": "Product has been deleted successfully"
    }
    ```

### 5. Order Management

- **Get All Orders (Admin)**
  - Endpoint: `GET /api/v1/orders`
  - Description: Retrieves a list of all orders (admin access required).
  - Response:
    ```json
    {
      "type": "success",
      "orders": [ ...orderList ]
    }
    ```

- **Get Monthly Income (Admin)**
  - Endpoint: `GET /api/v1/orders/income`
  - Description: Retrieves the monthly income for the past two months (admin access required).
  - Response:
    ```json
    {
      "type": "success",
      "income": [ { "month": 1, "total": 500 }, ... ]
    }
    ```

- **Get User Orders**
  - Endpoint: `GET /api/v1/orders/:userId`
  - Description: Retrieves orders for a specific user.
  - Response:
    ```json
    {
      "type": "success",
      "orders": { ...userOrderDetails }
    }
    ```

- **Create Order**
  - Endpoint: `POST /api/v1/orders`
  - Description: Places a new order.
  - Request Body:
    ```json
    {
      "userId": "userId123",
      "products": [
        {
          "productId": "product1Id",
          "quantity": 2
        }
      ],
      "amount": 50.99,
      "address": {
        "street": "123 Main St",
        "city": "Cityville",
        "zipcode": "12345"
      }
    }
    ```
  - Response:
    ```json
    {
      "type": "success",
      "message": "Order created successfully",
      "savedOrder": { ...newOrderDetails }
    }
    ```

- **Update Order (Admin)**
  - Endpoint: `PUT /api/v1/orders/:id`
  - Description: Updates order details (admin access required).
  - Request Body:
    ```json
    {
      "status": "shipped"
    }
    ```
  - Response:
    ```json
    {
      "type": "success",
      "message": "Order updated successfully",
      "updatedOrder": { ...updatedOrderDetails }
    }
    ```

- **Delete Order (Admin)**
  - Endpoint: `DELETE /api/v1/orders/:id`
  - Description: Deletes an order by ID (admin access required).
  - Response:
    ```json
    {
      "type": "success",
      "message": "Order has been deleted successfully"
    }
    ```

### 6. Payment

- **Process Payment**
  - Endpoint: `POST /api/v1/payment`
  - Description: Processes a payment using the Stripe API.
  - Request Body:
    ```json
    {
      "tokenId": "stripeTokenId",
      "amount": 50.99
    }
    ```
  - Response (Stripe API response):
    ```json
    {
      "id": "ch_1IvAcq2eZvKYlo2C3h8N7eVZ",
      "object": "charge",
      "amount": 5099,
      ...
    }
    ```

## Technologies Used

- Node.js
- Express.js
- MongoDB
- Mongoose
- Stripe API (for payment processing)
- JSON Web Tokens (JWT) for authentication
- Bcrypt.js for password hashing
- Body-parser for handling JSON requests
- ...

## Setup

1. Clone the repository:

   ```bash
   git clone https://github.com/yourusername/ecommerce-api.git
   ```

2. Install dependencies:

   ```bash
   cd ecommerce-api
   npm install
   ```

3. Set up your MongoDB database and update the connection URL in `config/database-config-example.js`.

4. Create a `config/api.js` file and set your JWT secret:

   ```javascript
   module.exports = {
       api: {
           jwt_secret: "yourJWTSecretKey",
       }
   };
   ```

5. Set up your Stripe account and obtain the API key. Set the key as an environment variable or update `controllers/PaymentController.js` with your key.

6. Run the application:

   ```bash
   npm start
   ```

   The server will be accessible at `http://localhost:3000`.

## Contribution

If you would like to contribute to this project, please follow the [contribution guidelines](CONTRIBUTING.md).

## License

This project is licensed under the [Coding Ninja - License](LICENSE).
