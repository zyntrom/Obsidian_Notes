This release introduces **basic support for the Redis Serialization Protocol (RESP)**, enabling structured client-server communication similar to Redis.

The command parser has been upgraded to handle both traditional text-based commands and RESP formatted requests. This lays the foundation for compatibility with Redis-style clients and tools.

## Added

- Basic **RESP protocol parsing**
- Support for **RESP Array** command format
- `PING` command for connectivity testing

## Improved

- Command parser now supports **both plain text and RESP input**
- Internal command handling updated to use argument vectors
- Improved modular separation between parser and database engine

## Example Usage

Start the server:

```
make run
```

Test plain text commands:

```
SET name Alen  
GET name  
PING
```

Test RESP protocol manually:

```
printf "*1\r\n$4\r\nPING\r\n" | nc localhost 6379
```

Response:

```
PONG
```

## Supported Commands

- `SET key value`
- `GET key`
- `DEL key`
- `EXPIRE key seconds`
- `TTL key`
- `PING`