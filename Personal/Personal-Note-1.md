This release introduces a key expiration system that allows entries in the database to automatically expire after a specified time. The expiration mechanism uses timestamp tracking and lazy deletion to efficiently manage expired keys.

This update enhances the database by adding time-based key management similar to behavior found in systems like Redis.

---

### Added

- `EXPIRE key seconds` command to set expiration for keys
    
- `TTL key` command to check remaining lifetime of a key
    
- Expiration timestamp tracking for stored keys
    
- Lazy expiration mechanism that removes expired keys when accessed
    

---

### Example Usage

Start the server:

```
make run
```

Set a key and expiration:

```
SET name Alen  
EXPIRE name 5
```

Check remaining time:

```
TTL name
```

Example output:

```
4
```

After expiration:

```
GET name  
(nil)
```

---

### Implementation Details

- Expiration times stored using `std::chrono`
    
- Separate expiration map for efficient lookup
    
- Lazy expiration check performed during key access
    
- Integrated expiration logic into database operations
    

---

### Supported Commands

```
SET key value  
GET key  
DEL key  
EXPIRE key seconds  
TTL key
```

---

### Next Release

Planned features for **v0.4.0**:

- Database persistence (saving key-value data to disk)
- Snapshot-based storage system
- Database loading on server startup