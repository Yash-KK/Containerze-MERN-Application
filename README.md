# MERN Application
This application provides a simple interface for managing employee details, allowing users to perform the following actions:

Create new employee records.
Read and view details of existing employees.
Update employee information.
Delete employee records.


This application includes:

- **Backend**: Node.js + Express server to handle API requests.
- **Frontend**: React client for a user-friendly interface.
- **Database**: MongoDB for data storage.

## Prerequisites

Before running the application, ensure you have:

1. **Docker**: Installed to containerize the application.
2. **Docker Network**: A Docker network named `mern` to enable communication between the frontend, backend, and database containers.

To create the Docker network:
```bash
docker network create mern
```

## Docker Setup
### Step 1: Build the Docker Images
#### **Backend Dockerfile (backend/Dockerfile):**
```bash
FROM node:16.13.2-alpine

WORKDIR /app

COPY package.json .
RUN npm install
COPY . .

EXPOSE 5050
CMD [ "npm", "run", "start" ]
```

#### **Frontend Dockerfile (frontend/Dockerfile):**
```bash
FROM node:16.13.2-alpine

WORKDIR /app

COPY package.json .
RUN npm install
COPY . .

EXPOSE 5173
CMD [ "npm", "run", "dev" ]

```
**To build the images, navigate to each component's directory and run:**

```bash
docker build -t <username>/mern-frontend:v1 ./frontend
docker build -t <username>/backend:v1 ./backend
```

### Step 2: Run the Containers
After building the images, run the containers with the following commands:

**Frontend**
```bash
docker run --name frontend -d -p 5173:5173 --network mern <username>/mern-frontend:v1
```

**Backend**
```bash
docker run --name backend -d -p 5050:5050 --network mern <username>/backend:v1
```


**MongoDB**
```bash
docker run -d --network mern -p 27017:27017 -v mern-db:/data/db --name mongodb mongo
```

### Step 3: Access the Application

With all containers running, the application will be accessible at:
[http://localhost:5173](http://localhost:5173)
