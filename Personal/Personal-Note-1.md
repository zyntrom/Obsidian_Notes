# Task Manager API 🚀  
  
## 📌 Features  
  
- User Registration & Login (JWT आधारित authentication)  
- Task CRUD operations (Create, Read, Update, Delete)  
- MongoDB indexing for performance optimization  
- In-memory caching for faster GET requests  
- Environment-based configuration using `.env`  
- Deployed on cloud (Render)  
  
---  
  
## 🔗 API Endpoints  
  
### 🔐 Auth Routes  
- POST `/api/auth/register` → Register user  
- POST `/api/auth/login` → Login user  
  
### 📋 Task Routes  
- GET `/api/tasks` → Get all tasks (cached)  
- POST `/api/tasks` → Create task  
- PUT `/api/tasks/:id` → Update task  
- DELETE `/api/tasks/:id` → Delete task  
  
---  
  
## ⚙️ Setup Guide  
  
### 1. Clone repo  
```bash  
git clone <your-repo-link>  
cd task-manager-api
```

### 2. Install dependencies

```
npm install
```

### 3. Create `.env`

```
PORT=5000  
MONGO_URI=your_mongodb_uri  
JWT_SECRET=your_secret_key
```

### 4. Run server

```
npm run dev

```
---

## ☁️ Deployment

Deployed on Render:

👉 https://your-render-link.onrender.com

---

## 🧪 Testing

Use Postman to test all endpoints.

---

## 📊 Performance Optimizations

- Indexed email field in User model
- Indexed userId, status, priority in Task model
- Implemented caching for GET /tasks

---

## 👨‍💻 Author

Alen Lajeesh