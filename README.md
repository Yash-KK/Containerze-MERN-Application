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

Before running the application, ensure you have **Docker** and **Docker Compose** installed.

### Step 1: Clone the Repository

#### **Backend Dockerfile (backend/Dockerfile):**
```bash
git https://github.com/Yash-KK/Containerze-MERN-Application.git
cd Containerze-MERN-Application

```
### Step 2: Run the Application
Start all services (frontend, backend, and MongoDB) using Docker Compose:
```bash
docker-compose up -d
```

### Step 3: Stop the Application
```bash
docker-compose down
```