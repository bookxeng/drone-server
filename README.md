# Drone Data API Server

This project is a RESTful API developed using **Node.js** and **Express.js** to manage drone information and log data. It enables retrieval of drone configuration details, status, operational logs, and allows the creation of new log entries. The system integrates with external API endpoints and employs environment variables for secure configuration management.

---

## 1. Project Overview

The Drone Data API Server is designed to act as a middleware layer between client applications and remote drone databases. Its primary purpose is to simplify data access, improve security, and standardize communication between different services involved in drone management systems.

---

## 2. System Features

- Retrieve drone configurations based on drone ID.
- Obtain the current status of a specific drone.
- Fetch drone operational logs with pagination support.
- Create and store new drone log entries.
- Environment variable–based configuration for flexibility and security.

---

## 3. Technologies Used

- **Node.js** – JavaScript runtime environment.
- **Express.js** – Web framework for building REST APIs.
- **dotenv** – For environment variable management.
- **CORS** – For handling cross-origin requests.
- **Fetch API** – For external API communication.

---

## 4. Installation and Setup

### Step 1: Clone the repository

```bash
git clone https://github.com/yourusername/drone-api-server.git
cd drone-api-server
```

### Step 2: Install required dependencies

```bash
npm install
```

### Step 3: Configure environment variables

Create a `.env` file in the project root directory and specify the following:

```
PORT=3001
DRONE_URL=https://example.com/api/drone-configs
DRONE_LOG=https://example.com/api/drone-logs
API_TOKEN=your_api_token_here
```

### Step 4: Start the server

To run the application:

```bash
npm start
```

If you have **nodemon** installed globally, you may use:

```bash
nodemon index.js
```

The server will be accessible at:

```
http://localhost:3001
```

---

## 5. API Endpoints

### **GET** `/configs/:id`
Fetch the configuration details of a specific drone.

**Example Request:**
```
GET /configs/1
```

**Response:**
```json
{
  "drone_id": 1,
  "drone_name": "Falcon X",
  "light": true,
  "country": "USA",
  "weight": 12.5
}
```

---

### **GET** `/status/:id`
Retrieve the operational condition of a specific drone.

**Example Request:**
```
GET /status/1
```

**Response:**
```json
{
  "condition": "active"
}
```

---

### **GET** `/logs/:id`
Retrieve a list of log entries for a specific drone, with pagination options.

**Query Parameters:**
- `page` — (optional) default `1`
- `perPage` — (optional) default `12`

**Example Request:**
```
GET /logs/1?page=2&perPage=10
```

**Response:**
```json
[
  {
    "drone_id": 1,
    "drone_name": "Falcon X",
    "created": "2025-11-06T12:34:56Z",
    "country": "USA",
    "celsius": 35
  }
]
```

---

### **POST** `/logs`
Create a new drone log entry.

**Request Body:**
```json
{
  "drone_id": 1,
  "drone_name": "Falcon X",
  "country": "USA",
  "celsius": 35
}
```

**Response:**
```json
{
  "id": "xyz123",
  "drone_id": 1,
  "drone_name": "Falcon X",
  "country": "USA",
  "celsius": 35,
  "created": "2025-11-06T12:34:56Z"
}
```

