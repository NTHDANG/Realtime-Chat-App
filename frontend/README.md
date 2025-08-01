# Frontend - Realtime Chat Application

## Project Overview

This directory contains the frontend application for the Realtime Chat project. Developed with a modern React.js stack, it provides a dynamic, responsive, and intuitive user interface for real-time communication. The frontend is designed to be highly interactive, leveraging efficient state management and a component-based architecture to deliver a seamless chat experience.

## Key Features

*   **Responsive User Interface:** Built with Tailwind CSS and DaisyUI to ensure a consistent and appealing experience across various devices.
*   **Real-time Chat Interface:** Displays messages instantaneously and updates user presence (online/offline) in real-time using Socket.IO client.
*   **User Authentication Flows:** Seamless signup and login processes, integrating with the backend's JWT-based authentication.
*   **User Profile Management:** Allows users to view and potentially update their profile information.
*   **Dynamic Routing:** Utilizes React Router DOM for efficient navigation between different application views (home, login, signup, settings, profile).
*   **Global State Management:** Employs Zustand for a lightweight and performant approach to managing application-wide state, including authentication status and chat data.
*   **Interactive Notifications:** Provides user feedback through toast notifications for actions like successful logins or errors.

## Technology Stack

*   **React.js:** The core JavaScript library for building the user interface.
*   **Vite:** A next-generation frontend build tool that offers incredibly fast hot module replacement and optimized builds.
*   **Tailwind CSS:** A utility-first CSS framework that enables rapid UI development with highly customizable designs.
*   **DaisyUI:** A component library built on top of Tailwind CSS, providing ready-to-use UI components to accelerate development.
*   **Zustand:** A minimalist state management library for React, known for its simplicity and performance.
*   **React Router DOM:** Standard library for routing in React applications, enabling declarative navigation.
*   **Axios:** A popular promise-based HTTP client used for making API requests to the backend.
*   **Lucide React:** A comprehensive icon library providing a wide range of customizable SVG icons.
*   **React Hot Toast:** A simple and elegant library for displaying toast notifications.
*   **Socket.IO Client:** The client-side library for establishing and managing real-time WebSocket connections with the backend.

## Setup and Installation

To run the frontend application locally, follow these steps:

### Prerequisites

*   **Node.js:** Ensure you have Node.js (LTS version recommended) installed.
*   **pnpm:** Install pnpm globally:
    ```bash
    npm install -g pnpm
    ```

### Installation Steps

1.  **Navigate to the Frontend Directory:**
    ```bash
    cd frontend
    ```

2.  **Install Dependencies:**
    ```bash
    pnpm install
    ```

3.  **Environment Configuration:**
    Create a `.env` file in the `frontend` directory (`realtime-chat/frontend/.env`) with the following variable. Replace the placeholder with the URL of your backend API.

    ```
    VITE_BACKEND_URL=http://localhost:3000 # Or your deployed backend URL
    ```

### Running the Application Locally

From the `frontend` directory:

```bash
# Start the frontend development server
pnpm dev
```

This will start the frontend application, typically accessible at `http://localhost:5173`.

## Building for Production

To create a production-ready build of the frontend application:

From the `frontend` directory:

```bash
pnpm run build
```

This command will compile and optimize the frontend assets into the `dist/` directory, ready for deployment.

## Deployment

The frontend application can be deployed as a static site to various hosting providers (e.g., Netlify, Vercel, Render Static Sites). Ensure that the `VITE_BACKEND_URL` environment variable is correctly configured on your hosting platform to point to your deployed backend service.
