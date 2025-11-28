# User Authentication and Authorization API (Node.js + Express + JWT + MongoDB Atlas)

This project is a complete authentication and authorization system built using Node.js, Express.js, JSON Web Tokens (JWT), and MongoDB Atlas. It provides a secure way for users to register, log in, and retrieve protected user information using a Bearer token. The API follows the MVC architecture, includes password hashing using bcrypt, uses JWT for sessionless authentication, and is fully deployable on Render. This project is ideal for beginners learning backend authentication and for developers needing a clean, production-ready user auth module.

---

## 🚀 Features

- User Registration (with hashed password)
- User Login (returns JWT token)
- Protected Route (`/api/users/me`)
- JWT Authorization Middleware
- MongoDB Atlas Database
- Fully deployable on Render
- MVC Folder Structure (Models, Controllers, Routes, Middleware)
- Beginner-friendly and well-documented

---

## 📁 Folder Structure

User Authentication and Authorization/
  - server.js
  - .env
  - package.json
  - config/
      - db.js
  - models/
      - User.js
  - controllers/
      - authController.js
      - userController.js
  - middleware/
      - authMiddleware.js
  - routes/
      - authRoutes.js
      - userRoutes.js
  - README.md

---

## ⚙️ Technologies Used

- **Node.js**
- **Express.js**
- **MongoDB Atlas (Cloud DB)**
- **Mongoose**
- **JWT (jsonwebtoken)**
- **bcrypt**
- **dotenv**
- **Render (Hosting)**

---

## 🔧 Installation

### 1. Clone the repository

```
git clone https://github.com/yourusername/yourrepo.git
cd yourrepo
```

### 2. Install Dependencies

```
npm install
```

### 3. Create `.env` file

```
PORT=5000
MONGODB_URI=your_atlas_connection_string
JWT_SECRET=your_secret_key
JWT_EXPIRES_IN=7d
```

### 4. Start the server

```
npm run dev     # development with nodemon
npm start       # production
```

Server runs at:

```
http://localhost:5000
```

---

## 🌐 MongoDB Atlas Setup

1. Go to https://www.mongodb.com/atlas
2. Create a free M0 cluster
3. Create a database user (username + password)
4. Allow IP Access → 0.0.0.0/0
5. Get your connection string:
   ```
   mongodb+srv://<user>:<password>@cluster0.mongodb.net/<database>?retryWrites=true&w=majority
   ```
6. Put it inside .env under MONGODB_URI

---

## ☁️ Deployment on Render

1. Push your project to GitHub
2. Go to https://render.com
3. Create New → Web Service
4. Select your repo
5. Use these settings:
   - Build Command
     `npm install`
     
   - Start Command
     `npm start`
     
   - Environment -> Node
     
   - Region -> Closest
     
   - Plan -> Free
6. Add Environment Variables:
```
MONGODB_URI=...
JWT_SECRET=...
JWT_EXPIRES_IN=1h
```
7.Deploy

---

## 📘 API Documentation

Base URL (Render):
`https://user-authentication-and-authorization-qavn.onrender.com/`

---

### 🔹 1. REGISTER USER

`POST /api/auth/register`

**Body:**

```
{
  "username": "John Doe",
  "email": "johndoe@example.com",
  "password": "password123"
}
```

### 🔹 2. LOGIN USER

`POST /api/auth/login`

**Body:**

```
{
  "email": "johndoe@example.com",
  "password": "password123"
}
```

**Success Response:**

```
{
  "message": "Login successful",
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6Ikp..."
}
```

### 🔹 3. GET CURRENT USER (Protected)

`GET /api/users/me`

**Headers:**

`Authorization: Bearer <your_jwt_token>`

**Success Response:**

```
{
  "message": "User fetched successfully",
  "user": {
    "_id": "69299977c7229e3d49304cb",
    "username": "John Doe",
    "email": "johndoe@example.com",
    "createdAt": "2024-12-01T12:00:00.000Z",
    "updatedAt": "2024-12-01T12:00:00.000Z",
    "__v": 0
  }
}
```

---

## 🔑 JWT Authentication Flow

1. User registers
2. User logs in → API generates JWT token
3. Token is sent back to the client
4. Client stores token in:
   - LocalStorage (frontend)
   - AsyncStorage (React Native)
   - Session storage
5. For protected routes, client sends:
   `Authorization: Bearer <token>`
6. Middleware verifies token → gives access

---

## 🔬 Testing the API

### ✔ Using Postman

**Register**

`https://user-authentication-and-authorization-qavn.onrender.com/api/auth/register`

**Login**

`https://user-authentication-and-authorization-qavn.onrender.com/api/auth/login`

**Get current user**

```
GET https://your-render-app.com/api/users/me
Authorization: Bearer <token>
```

---

## 🛠 Environment Variables Summary

```
PORT=5000
MONGODB_URI=<Atlas connection string>
JWT_SECRET=<your-secret-key>
JWT_EXPIRES_IN=1h
```







