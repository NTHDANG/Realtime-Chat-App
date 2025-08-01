# Backend - Realtime Chat Application

## Project Overview

This directory houses the backend application for the Realtime Chat project. Developed with Node.js and Express.js, it provides a robust and scalable API layer, handles real-time communication, manages user authentication, and interacts with the MongoDB database. The backend is designed to be highly performant and secure, forming the backbone of the real-time chat functionality.

## Key Features

*   **RESTful API Endpoints:** Provides well-structured API endpoints for user authentication, message handling, and other core functionalities.
*   **Real-time Communication:** Implements Socket.IO to enable bidirectional, low-latency communication between clients and the server, facilitating instant message delivery and online status updates.
*   **Secure User Authentication:** Utilizes JWT (JSON Web Tokens) for stateless authentication and `bcryptjs` for secure password hashing, ensuring user data integrity and security.
*   **MongoDB Integration:** Leverages Mongoose ODM (Object Data Modeling) for efficient and flexible interaction with the MongoDB NoSQL database, managing user profiles and chat messages.
*   **Cloudinary Integration:** Supports image uploads (e.g., for user avatars) through Cloudinary, a cloud-based media management service.
*   **CORS Management:** Configured to handle Cross-Origin Resource Sharing, allowing secure communication with the frontend application.
*   **Environment Variable Management:** Securely loads sensitive configuration details using `dotenv`.

## Technology Stack

*   **Node.js:** A powerful JavaScript runtime environment for building scalable server-side applications.
*   **Express.js:** A fast, minimalist web framework for Node.js, used for building robust APIs.
*   **Socket.IO:** A library that enables real-time, bidirectional, and event-based communication between web clients and servers.
*   **MongoDB:** A popular NoSQL document database, providing a flexible and scalable data storage solution.
*   **Mongoose:** An elegant MongoDB object modeling tool for Node.js, simplifying data interaction and validation.
*   **JSON Web Tokens (JWT):** A compact, URL-safe means of representing claims to be transferred between two parties, used for authentication.
*   **bcryptjs:** A library for hashing passwords, providing strong cryptographic security.
*   **Cloudinary:** A cloud-based service that offers a comprehensive solution for image and video management.
*   **dotenv:** A zero-dependency module that loads environment variables from a `.env` file into `process.env`.
*   **CORS:** Middleware for Express.js to enable Cross-Origin Resource Sharing.
*   **cookie-parser:** Middleware to parse Cookie headers and populate `req.cookies`.
*   **nodemon:** A utility that monitors for any changes in your source and automatically restarts your server, ideal for development.

## Setup and Installation

To run the backend application locally, follow these steps:

### Prerequisites

*   **Node.js:** Ensure you have Node.js (LTS version recommended) installed.
*   **pnpm:** Install pnpm globally:
    ```bash
    npm install -g pnpm
    ```
*   **MongoDB:** A running MongoDB instance (local or cloud-hosted like MongoDB Atlas).

### Installation Steps

1.  **Navigate to the Backend Directory:**
    ```bash
    cd backend
    ```

2.  **Install Dependencies:**
    ```bash
    pnpm install
    ```

3.  **Environment Configuration:**
    Create a `.env` file in the `backend` directory (`realtime-chat/backend/.env`) with the following variables. Replace placeholder values with your actual credentials.

    ```
    PORT=3000
    MONGODB_URI=<Your MongoDB Connection URI>
    JWT_SECRET=<A strong, unique secret key for JWT>
    NODE_ENV=development # or production
    FRONTEND_URL=http://localhost:5173 # For local development, use your frontend's local URL
    CLOUDINARY_CLOUD_NAME=<Your Cloudinary Cloud Name>
    CLOUDINARY_API_KEY=<Your Cloudinary API Key>
    CLOUDINARY_API_SECRET=<Your Cloudinary API Secret>
    ```
    _Note: Ensure `dotenv.config()` is called early in your `backend/src/index.js` to load these variables._

### Running the Application Locally

From the `backend` directory:

```bash
# Start the backend server in development mode
pnpm dev
```

This will start the backend server, typically listening on `http://localhost:3000`.

## Deployment

The backend application can be deployed as a web service to various cloud providers (e.g., Render, Heroku, AWS EC2). Ensure all environment variables are securely configured on your chosen hosting platform. The `PORT` variable should be set to the port provided by the hosting environment.
