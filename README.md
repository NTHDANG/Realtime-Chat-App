# Realtime Chat Application

## Project Overview

This project presents a robust, full-stack real-time chat application engineered with a modern monorepo architecture. It leverages a powerful MERN-like stack (MongoDB, Express.js, React.js, Node.js) complemented by Socket.IO for seamless, instant communication. Designed for scalability and maintainability, this application showcases best practices in web development, including secure authentication, efficient state management, and a responsive user interface. It's an ideal demonstration of building interactive, high-performance web solutions.

## Key Features

### Core Communication

*   **Real-time Messaging:** Instantaneous message delivery and display using WebSocket technology (Socket.IO), ensuring a fluid and responsive chat experience.
*   **User Presence:** Dynamic online/offline status indicators for users, providing immediate insights into contact availability.

### User Management & Experience

*   **Secure Authentication:** Robust user registration and login system powered by JWT (JSON Web Tokens) for secure session management and `bcryptjs` for password hashing.
*   **User Profiles:** Dedicated profile pages allowing users to manage their information.
*   **User Search:** Efficient search functionality to discover and connect with other users within the application.
*   **Personalized Settings:** Customizable user settings to enhance individual experience.
*   **Image Uploads:** Integrated Cloudinary for secure and efficient storage of user avatars and potentially other media.

### Technical Sophistication

*   **Monorepo Structure:** Organized into a `pnpm` monorepo, facilitating streamlined dependency management and cohesive development across frontend and backend.
*   **Modern Frontend Stack:** Built with React.js and Vite for a fast, component-based UI development experience, styled with the utility-first approach of Tailwind CSS and enhanced with DaisyUI components.
*   **Scalable Backend:** A Node.js and Express.js backend designed for high concurrency, handling real-time communication and API requests efficiently.
*   **NoSQL Database:** MongoDB (via Mongoose ODM) provides a flexible and scalable data storage solution for user and message data.

## Technology Stack

### Monorepo Management

*   **pnpm:** Fast, disk space efficient package manager.
*   **concurrently:** Utility to run multiple commands concurrently (for development).

### Frontend

*   **React.js:** A declarative, component-based JavaScript library for building user interfaces.
*   **Vite:** A next-generation frontend tooling that provides an extremely fast development experience.
*   **Tailwind CSS:** A utility-first CSS framework for rapidly building custom designs.
*   **DaisyUI:** A Tailwind CSS component library for faster UI development.
*   **Zustand:** A small, fast, and scalable bear-bones state-management solution.
*   **React Router DOM:** Declarative routing for React.js.
*   **Axios:** Promise-based HTTP client for the browser and Node.js.
*   **Lucide React:** A collection of beautiful and customizable SVG icons.
*   **React Hot Toast:** A lightweight and customizable toast notification library.

### Backend

*   **Node.js:** A JavaScript runtime built on Chrome's V8 JavaScript engine.
*   **Express.js:** A fast, unopinionated, minimalist web framework for Node.js.
*   **Socket.IO:** A library that enables real-time, bidirectional, event-based communication.
*   **MongoDB:** A NoSQL document database.
*   **Mongoose:** An elegant MongoDB object modeling for Node.js.
*   **JSON Web Tokens (JWT):** For secure, stateless authentication.
*   **bcryptjs:** A library to help you hash passwords.
*   **Cloudinary:** Cloud-based image and video management service.
*   **dotenv:** Loads environment variables from a `.env` file.
*   **CORS:** Node.js package for providing a Connect/Express middleware that can be used to enable CORS with various options.
*   **cookie-parser:** Parse Cookie header and populate `req.cookies` with an object keyed by the cookie names.
*   **nodemon:** A tool that helps develop Node.js based applications by automatically restarting the node application when file changes in the directory are detected.

## Architecture

The project adopts a monorepo strategy, housing both the frontend and backend applications within a single repository.

*   **Frontend (`frontend/`):** A React.js application that consumes the backend APIs and handles real-time communication via Socket.IO client.
*   **Backend (`backend/`):** A Node.js/Express.js server that provides RESTful APIs, manages database interactions (MongoDB), handles user authentication, and facilitates real-time messaging through Socket.IO server.

In production, the backend is configured to serve the static build files of the frontend, creating a cohesive deployment unit.

## Setup and Installation

Follow these steps to get the project up and running on your local machine.

### Prerequisites

*   **Node.js:** Ensure you have Node.js (LTS version recommended) installed.
*   **pnpm:** Install pnpm globally:
    ```bash
    npm install -g pnpm
    ```
*   **MongoDB:** A running MongoDB instance (local or cloud-hosted like MongoDB Atlas).

### Installation Steps

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/your-username/realtime-chat.git
    cd realtime-chat
    ```

2.  **Install Dependencies (Monorepo Root):**
    Navigate to the project root and install all dependencies for both backend and frontend:
    ```bash
    pnpm install
    ```

3.  **Backend Configuration:**
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

4.  **Frontend Configuration:**
    Create a `.env` file in the `frontend` directory (`realtime-chat/frontend/.env`) with the following variables:

    ```
    VITE_BACKEND_URL=http://localhost:3000 # For local development, use your backend's local URL
    ```

### Running the Application Locally

From the project root (`realtime-chat`):

```bash
# Start both backend and frontend in development mode concurrently
pnpm dev
```

This command will start both the backend server (typically on `http://localhost:3000`) and the frontend development server (typically on `http://localhost:5173`).

Alternatively, you can start them separately:

```bash
# Start backend (from project root)
pnpm --dir backend dev

# Start frontend (from project root)
pnpm --dir frontend dev
```

## Deployment Strategies

This project is designed for flexible deployment to various cloud platforms. Below are general guidelines and specific considerations for platforms like Render.

### General Deployment Considerations

*   **Environment Variables:** Ensure all necessary environment variables (`MONGODB_URI`, `JWT_SECRET`, `CLOUDINARY_CLOUD_NAME`, etc.) are securely configured on your chosen hosting platform.
*   **Build Process:** The frontend needs to be built (`pnpm --dir frontend run build`) and its static assets served. In a full-stack deployment, the backend can serve these assets.
*   **Port Configuration:** Ensure your application listens on the port provided by the hosting environment (e.g., `process.env.PORT`).
*   **CORS Configuration:** Adjust `FRONTEND_URL` in your backend's `.env` (or environment variables on the platform) to match your deployed frontend URL for proper CORS handling.

### Example: Deployment on Render

Render is a unified platform to build and run all your apps and websites. This project can be deployed as two separate services (a Web Service for the backend and a Static Site for the frontend) or as a single Web Service serving both.

#### Backend Service Deployment (Render Web Service)

*   **Build Command:** `pnpm install && pnpm run build:frontend`
    *   _Explanation:_ This command installs all monorepo dependencies and then builds the frontend, which is crucial for the backend to serve static files in production.
*   **Start Command:** `pnpm start`
    *   _Explanation:_ This command executes the `start` script defined in the root `package.json`, which is configured to run `pnpm --dir backend start`, effectively starting your backend server.
*   **Environment Variables (on Render Dashboard):**
    *   `PORT` (optional, Render provides its own, but `3000` is used as a fallback in code)
    *   `MONGODB_URI` (Your MongoDB connection string)
    *   `JWT_SECRET` (Your JWT secret key)
    *   `NODE_ENV=production`
    *   `FRONTEND_URL=<Your deployed frontend URL>`
    *   `CLOUDINARY_CLOUD_NAME`
    *   `CLOUDINARY_API_KEY`
    *   `CLOUDINARY_API_SECRET`

#### Frontend Service Deployment (Render Static Site)

*   **Build Command:** `pnpm install && pnpm --dir frontend run build`
    *   _Explanation:_ This installs all dependencies and then specifically builds the frontend project.
*   **Publish Directory:** `frontend/dist`
*   **Environment Variables (on Render Dashboard):**
    *   `VITE_BACKEND_URL=<The URL of your deployed backend service on Render>`

## Contributing

Contributions are welcome! Please feel free to fork the repository, create a new branch, and submit a pull request.

## License

This project is licensed under the ISC License.