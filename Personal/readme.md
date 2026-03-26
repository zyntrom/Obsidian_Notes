# Task Management API  
  
## 📌 Description  
A production-ready Task Management API built with Node.js, Express, and MongoDB.    
Includes performance optimization, in-memory caching, and cloud deployment.  
  
---  
  
## 🚀 Features  
- User Registration & Authentication (JWT)  
- Create, Read, Update, Delete Tasks  
- Optimized database queries using indexes  
- In-memory caching for faster responses  
- Automatic cache invalidation  
- Environment-based configuration  
- Secure production setup  
- Cloud deployment (Render/Railway ready)  
  
---  
  
## 📡 API Documentation  
  
### 1. Register User  
POST /api/auth/register  
  
Request:  
``` 
{  
  "email": "user@example.com",  
  "password": "123456"  
}

Response:

{  
  "message": "User registered successfully"  
}
```
---

### 2. Login

POST /api/auth/login

Response:

```
{  
  "token": "jwt_token"  
}
```

---

### 3. Create Task

POST /api/tasks

```
{  
  "title": "Task 1",  
  "status": "pending",  
  "priority": "high"  
}
```

---

### 4. Get All Tasks

```
GET /api/tasks
```

---

### 5. Update Task

```
PUT /api/tasks/:id
```

---

## ⚡ Performance Optimizations

- Indexed `email` field in User model
- Indexed `userId` in Task model
- Compound index on `status + priority`
- In-memory caching for GET tasks

---

## 🔐 Environment Variables

```
PORT=  
MONGO_URI=  
JWT_SECRET=
```

---

## 🛠 Installation Guide

```
git clone <repo>  
cd project  
npm install  
npm run dev
```

---

## 🌍 Deployment Guide

- Push to GitHub
- Connect to Render/Railway
- Add environment variables
- Deploy

---

## 🧪 Testing Guide

- Use Postman
- Test:
    - Register
    - Login
    - Create Task
    - Get Tasks
    - Update Task

---

## 🔗 Live URL

```
https://your-api-url.com
```
---

## 🧰 Technologies Used

- Node.js
- Express.js
- MongoDB
- Mongoose
- JWT