# 📚 School Management API

A Node.js + Express.js + MySQL based backend system to manage school data.  
This API allows users to add schools and retrieve a list of schools sorted by proximity to a given location.

---

## 🚀 Features

- Add a new school with name, address, latitude, and longitude
- Fetch all schools sorted by distance from user location
- Input validation using Joi
- Clean architecture (Controller + Service layer)
- RESTful API design

---

## 🛠️ Tech Stack

- Node.js
- Express.js
- MySQL
- Joi (Validation)
- dotenv

---

## 📁 Project Structure

```
src/
 ├── controllers/
 ├── services/
 ├── routes/
 ├── validators/
 ├── utils/
 ├── db.js
 └── app.js
```

---

## ⚙️ Setup Instructions

### 1. Clone the repository

```bash
git clone https://github.com/chetanmalviya18/slooze_school_node_assignment.git
cd school-api
```

---

### 2. Install dependencies

```bash
npm install
```

---

### 3. Configure Environment Variables

Create a `.env` file in root:

```
PORT=3000

DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=school_db
```

---

### 4. Setup Database

#### Create Database
```sql
CREATE DATABASE school_db;
```

#### Create Table
```sql
CREATE TABLE schools (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255) NOT NULL,
  address VARCHAR(255) NOT NULL,
  latitude FLOAT NOT NULL,
  longitude FLOAT NOT NULL
);
```

---

### 5. Run the project

```bash
npm run dev
```

---

## 🔌 API Endpoints

### ➤ Add School

**Endpoint:**
POST /api/addSchools

**Request Body:**
```json
{
  "name": "ABC School",
  "address": "Jaipur",
  "latitude": 26.9124,
  "longitude": 75.7873
}
```

**Response:**
```json
{
    "success": true,
    "message": "School added successfully",
    "data": {
        "id": 1
    }
}
```

---

### ➤ List Schools (Sorted by Distance)

**Endpoint:**
GET /api/listSchools?latitude=26.9&longitude=75.8

**Response:**
```json
{
    "message": "Schools retrieved and sorted successfully",
    "count": 1,
    "data": [
        {
            "id": 11,
            "name": "Expert International School",
            "address": "Virar",
            "latitude": 4.1234002113342285,
            "longitude": 9.652199745178223,
            "distance": 7970.99
        }
    ]
}
```

---

## 📍 Distance Calculation

Distance between user and school is calculated using the Haversine Formula, which determines the shortest distance between two points on Earth.

---

## 🧪 Testing

Use Postman to test APIs:

Add School → POST request with JSON body
List Schools → GET request with query params

---

## 🌐 Live API

https://slooze-school-node-assignment.onrender.com

---

## 📬 Postman Collection



---

## 📦 Scripts

```
"scripts": {
  "dev": "nodemon src/app.js",
  "start": "node src/app.js"
}
```

---

## ⚠️ Validation Rules

- All fields are required
- Latitude must be between -90 to 90
- Longitude must be between -180 to 180
