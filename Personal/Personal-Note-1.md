This release introduces a TCP server that allows clients to connect and execute database commands over the network. The server integrates the in-memory database engine with a command parser, enabling interaction through a simple text-based protocol.

### Added

- TCP socket server for client connections
    
- Command parser for processing text-based commands
    
- Integration between server and database engine
    
- Support for basic database commands:
    
    - `SET key value`
        
    - `GET key`
        
    - `DEL key`
        

### Improved

- Persistent client connections allowing multiple commands per session
    
- Modular server and parser components for easier extensibility
    

### Example Usage

Start the server:

```
make run
```

Connect using **OpenBSD netcat**:

```
nc localhost 6379
```

Run commands:

```
SET name Alen  
GET name  
DEL name
```

Example output:

```
OK  
Alen  
1
```

### Technical Details

- Language: C++
    
- Networking: POSIX sockets
    
- Architecture modules:
    
    - Server
        
    - Command Parser
        
    - Database Engine
        

### Next Release

Planned features for **v0.3.0**:

- Key expiration (`EXPIRE key seconds`)
    
- Time-to-live queries (`TTL key`)
    
- Expiration management system