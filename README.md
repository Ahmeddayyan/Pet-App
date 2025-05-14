# Purrfect Match

A pet adoption platform that connects pet owners with potential adopters.

## Prerequisites

- **For Docker Setup:**

  - Docker Engine 24.0+
  - Docker Compose V2
  - At least 1GB of free RAM

- **For Node.js Setup:**
  - Backend: Node.js 18.x
  - Frontend: Node.js 20.x
  - MongoDB (local or Atlas)
  - npm 9.x+

## Running the Project with Docker

This project provides Dockerfiles for both the backend and frontend, along with a `compose.yaml` for easy orchestration.

### Project-Specific Requirements

- **Node.js Version:**
  - Backend: Node.js 18
  - Frontend: Node.js 20
- **Environment Variables:**
  - Backend: Requires a `.env` file in `./backend`
  - Frontend: Requires a `.env` file in `./frontend` with `VITE_API_URL=http://localhost:5000`
- **Ports Exposed:**
  - Backend API: Host `5000` maps to container `3000`
  - Frontend: Host `5173` maps to container `80` (Nginx)

### Build and Run Instructions

1. Ensure you have Docker and Docker Compose installed.
2. Place your environment variable files at `./backend/.env` and `./frontend/.env`.
3. From the project root, run:
   ```sh
   docker compose up --build -d
   ```

### Special Configuration

- The frontend uses Nginx to serve the built static files
- The frontend uses Vite's preview server for production builds.
- Both services are connected via a custom Docker network (`appnet`).
- The frontend service depends on the backend service and will wait for it to be available before starting.

### Service Summary

| Service     | Build Context | Exposed Port (Host:Container) | Description         |
| ----------- | ------------- | ----------------------------- | ------------------- |
| js-backend  | ./backend     | 5000:3000                     | Node.js backend API |
| js-frontend | ./frontend    | 5173:80                       | Nginx frontend      |

---

## Running the Project with Node.js

If you prefer to run the project without Docker, you can use Node.js directly.

---

### Backend Setup

1. Navigate to the backend directory:

```bash
cd backend
```

2. Install dependencies:

```bash
npm install
```

3. Create a .env file with the required environment variables

4. Start the server:

```bash
npm start
```

The backend will be available at http://localhost:3000

### Frontend Setup

1. Navigate to the frontend directory:

```bash
cd frontend
```

2. Install dependencies:

```bash
npm install
```

3. Create a .env file with:

```bash
VITE_API_URL=http://localhost:3000
```

4. Start the development server:

```bash
npm run dev
```

The frontend will be available at http://localhost:5173

5. For production build:

```bash
npm run build
npm run preview
```

---

## Deploying with Kubernetes

This project includes Kubernetes configuration files in the kubernetes directory for deploying to a Kubernetes cluster.

Kubernetes Resources
The Kubernetes configurations are split between frontend and backend:

### Frontend Setup

1.

---

_This section was updated to reflect the current Docker-based setup for this project. Please ensure your `.env` files are correctly configured for both backend and frontend before running the containers._
