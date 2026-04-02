# Caching Strategy  
  
## 📌 Endpoint Cached  
```
GET /api/tasks  
```
---  
  
## ⚡ Why This Endpoint?  
- Most frequently called  
- Expensive database query  
- Ideal for caching  
  
---  
  
## 🧠 Implementation  
  
- Store results in memory  
- Cache expires after 60 seconds  
- Structure:  
  
```js  
let cache = {  
  data: null,  
  timestamp: null  
}
```
---

## 🔁 Cache Logic

- If cache exists AND < 60 seconds → return cache
- Else → fetch from DB and update cache

---

## ❌ Cache Invalidation

Cache cleared when:

- Task created
- Task updated
- Task deleted

---

## ⚠️ Limitations

- Lost on server restart
- Not scalable across multiple servers
- Memory usage grows with data

---

## ✅ Summary

In-memory caching improves response time significantly but is best suited for small-scale apps. 