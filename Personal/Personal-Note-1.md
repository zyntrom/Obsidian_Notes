# 📄 CACHING.md

# Caching Strategy 🧠  
  
## 📌 Why GET /api/tasks is Cached  
  
Fetching all tasks frequently can slow down performance due to repeated database queries.    
To improve speed and reduce load, we cache the response.  
  
---  
  
## 🧠 Cache Storage  
  
Cache is stored in an in-memory variable:  
  
```js  
let taskCache = {  
  data: null,  
  timestamp: null  
};
```
---

## ⏱️ TTL (Time To Live)

- Cache duration: **60 seconds**
- If data is fresh → return cached response
- If expired → fetch from database

---

## 🔄 Cache Invalidation

Cache is cleared when:

- A new task is created
- A task is updated
- A task is deleted

This ensures users always receive updated data.

---

## ⚠️ Limitations

- Cache is stored in memory (not persistent)
- Data resets when server restarts
- Not suitable for distributed systems

---

## 🚀 Benefits

- Faster API responses
- Reduced database load
- Improved user experience