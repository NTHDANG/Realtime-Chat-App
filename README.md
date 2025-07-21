# Realtime Chat Application

This is a full-stack real-time chat application with a separate backend (Node.js, Express, Socket.IO, MongoDB) and frontend (React, Vite, Tailwind CSS) within a pnpm monorepo.

## Features

- Real-time messaging
- User authentication (signup, login)
- User search
- Online/offline status

## Technologies Used

### Backend

- Node.js
- Express.js
- Socket.IO
- MongoDB (via Mongoose)
- JWT for authentication
- bcryptjs for password hashing
- Cloudinary for image uploads (if implemented)

### Frontend

- React.js
- Vite
- Tailwind CSS
- Zustand (state management)

## Setup and Installation

    ```

2.  **Install Dependencies (Monorepo Root):**
    Navigate to the project root and install all dependencies for both backend and frontend:

    ```bash
    pnpm install
    ```

3.  **Backend Configuration:**
    Create a `.env` file in the `backend` directory (`realtime-chat/backend/.env`) with the following variables:

    ```
    PORT=3000
    MONGODB_URI=<Your MongoDB URI>
    JWT_SECRET=<Your JWT Secret>
    NODE_ENV=development # or production
    FRONTEND_URL=http://localhost:5173 # For local development, use your frontend's local URL
    CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
    CLOUDINARY_API_KEY=your_cloudinary_api_key
    CLOUDINARY_API_SECRET=your_cloudinary_api_secret
    ```

    _Note: Ensure `dotenv.config()` is called early in your `backend/src/index.js` to load these variables._

4.  **Frontend Configuration:**
    Create a `.env` file in the `frontend` directory (`realtime-chat/frontend/.env`) with the following variables:

    ```
    VITE_BACKEND_URL=http://localhost:3000 # For local development, use your backend's local URL
    ```

5.  **Run Locally:**
    From the project root (`realtime-chat`):

    ```bash
    # Start both backend and frontend in development mode
    pnpm dev
    ```

    Alternatively, you can start them separately:

    ```bash
    # Start backend (from project root)
    pnpm --dir backend dev

    # Start frontend (from project root)
    pnpm --dir frontend dev
    ```

## Deployment on Render

This project is configured for deployment on Render as two separate services (or a single web service if you prefer, but the current setup implies separate services for backend and frontend).

### Backend Service Deployment (on Render)

- **Build Command:** `pnpm install && pnpm run build:frontend`
  - _Explanation:_ This command installs all monorepo dependencies and then builds the frontend, which is necessary for the backend to serve static files in production.
- **Start Command:** `pnpm start`
  - _Explanation:_ This command executes the `start` script defined in the root `package.json`, which is configured to run `pnpm --dir backend start`, effectively starting your backend server.
- **Environment Variables (on Render Dashboard):**
  - `PORT` (optional, Render provides its own, but `3000` is used as a fallback in code)
  - `MONGODB_URI` (Your MongoDB connection string)
  - `JWT_SECRET` (Your JWT secret key)
  - `NODE_ENV=production`
  - `FRONTEND_URL=`
  - `CLOUDINARY_CLOUD_NAME`
  - `CLOUDINARY_API_KEY`
  - `CLOUDINARY_API_SECRET`

### Frontend Service Deployment (on Render)

- **Build Command:** `pnpm install && pnpm --dir frontend run build`
  - _Explanation:_ This installs all dependencies and then specifically builds the frontend project.
- **Publish Directory:** `frontend/dist`
- **Environment Variables (on Render Dashboard):**
  - `VITE_BACKEND_URL=` (The URL of your deployed backend service on Render)
