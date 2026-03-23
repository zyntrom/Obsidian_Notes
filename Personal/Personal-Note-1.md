# Task Manager API 🚀  
  
## 📌 Project Description  
A production-ready Task Management API built using Node.js, Express, and MongoDB.    
This API supports user authentication, task management, performance optimization using indexing, and caching for faster responses.  
  
---  
  
## ✨ Features  
- User Registration & Login (JWT Authentication)  
- Secure password hashing  
- Protected routes using middleware  
- Task CRUD operations (Create, Read, Update, Delete)  
- MongoDB indexing for optimized queries  
- In-memory caching for improved performance  
- Environment-based configuration (.env)  
- Error handling middleware  
- RESTful API design  
- Cloud deployment (Render)  
  
---  
  
## 🔗 API Documentation  
  
### 🔐 Auth Routes  
  
#### 1. Register User  
**POST** `/api/auth/register`  
  
**Request Body:**  
```json  
{  
  "email": "test@example.com",  
  "password": "123456"  
}

**Response:**

{  
  "message": "User registered successfully"  
}

---

#### 2. Login User

**POST** `/api/auth/login`

**Request Body:**

{  
  "email": "test@example.com",  
  "password": "123456"  
}

**Response:**

{  
  "token": "jwt_token_here"  
}

---

### 📋 Task Routes

#### 3. Get All Tasks (Cached)

**GET** `/api/tasks`

**Headers:**

Authorization: Bearer <token>

**Response:**

[  
  {  
    "_id": "task_id",  
    "title": "Sample Task",  
    "status": "pending",  
    "priority": "high"  
  }  
]

---

#### 4. Create Task

**POST** `/api/tasks`

**Request Body:**

{  
  "title": "New Task",  
  "status": "pending",  
  "priority": "medium"  
}

**Response:**

{  
  "message": "Task created successfully"  
}

---

#### 5. Update Task

**PUT** `/api/tasks/:id`

**Request Body:**

{  
  "status": "completed"  
}

**Response:**

{  
  "message": "Task updated successfully"  
}

---

#### 6. Delete Task

**DELETE** `/api/tasks/:id`

**Response:**

{  
  "message": "Task deleted successfully"  
}

---

## ⚡ Performance Optimizations

- Indexed `email` field in User model (fast login)
- Indexed `userId` in Task model (fast user-specific queries)
- Compound index on `status + priority`
- In-memory caching for GET `/api/tasks`

---

## 🔐 Environment Variables

Create a `.env` file:

PORT=5000  
MONGO_URI=your_mongodb_uri  
JWT_SECRET=your_secret_key

---

## ⚙️ Installation Guide

1. Clone the repository:

git clone <your-repo-link>  
cd task-manager-api

2. Install dependencies:

npm install

3. Create `.env` file
4. Run server:

npm run dev

---

## ☁️ Deployment Guide (Render)

1. Push project to GitHub
2. Go to Render
3. Create a new Web Service
4. Connect GitHub repo
5. Add environment variables
6. Set:
    - Build Command: `npm install`
    - Start Command: `npm start`
7. Deploy

---

## 🧪 Testing Guide

1. Open Postman
2. Use deployed base URL
3. Test all endpoints
4. Run GET `/api/tasks` multiple times to verify caching

---

## 🌐 Live Deployment

👉 [https://your-render-link.onrender.com](https://your-render-link.onrender.com)

---

## 🛠️ Technologies Used

- Node.js
- Express.js
- MongoDB Atlas
- Mongoose
- JWT Authentication
- Render (Deployment)

---

## 👨‍💻 Author

Alen Lajeesh