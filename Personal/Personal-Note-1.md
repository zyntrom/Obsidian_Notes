### Overview

Initial release of the project introducing the core in-memory key-value database engine. This version establishes the foundational storage layer that future networking, command parsing, and persistence features will build upon.

### Features

- In-memory key-value storage using `std::unordered_map`
    
- Basic database operations:
    
    - `SET key value`
        
    - `GET key`
        
    - `DEL key`
        
- Modular project structure with `src/` and `include/`
    
- Basic executable demonstrating database functionality
    

### Technical Details

- Language: C++
    
- Data Structure: Hash table (`std::unordered_map`)
    
- Build System: Makefile
    
- Modular database class implementation
    

### Example

SET name Alen  
GET name  
DEL name

### Upcoming in Next Release

- Command parser implementation
    
- TCP server for client connections
    
- Redis-style command interface