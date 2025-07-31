# Design Patterns and Guidelines

## Architecture Overview
- **CLI-based Architecture**: Uses Cobra for command-line interface
- **WebSocket Server**: Single-page application communicating via WebSocket
- **Process Management**: Uses PTY (pseudo-terminal) for command execution

## Key Design Patterns

### 1. Command Pattern (Cobra)
- Root command in `cmd/root.go`
- Subcommands in separate files (run.go, version.go)
- Command initialization in `init()` functions

### 2. Server-Client Communication
- JSON message protocol over WebSocket
- Event-based architecture with defined event types:
  - `EventResize`: Terminal resize events
  - `EventSendkey`: Keyboard input events (though defined as "Snedkey" - likely a typo)
  - `EventClose`: Connection close events

### 3. Embedded Assets
- Frontend assets embedded using Go's `embed` package
- HTML and JavaScript served from embedded filesystem

### 4. Concurrent I/O Handling
- Goroutines for bidirectional communication
- Separate goroutine for reading from WebSocket and writing to PTY
- Main goroutine copies PTY output to WebSocket

## Code Guidelines

### Error Handling
- Log errors but don't crash the server
- Graceful degradation for client disconnections
- Return meaningful error messages to clients

### Resource Management
- Proper cleanup with `defer` statements
- Close WebSocket connections and PTY on exit
- Single PTY instance per connection session

### Security Considerations
- Origin checking for WebSocket connections
- Configurable allowed origins
- No authentication mechanism (consider for production use)

## Development Guidelines

### Adding New Features
1. Follow existing command structure for new CLI commands
2. Maintain backward compatibility with message protocol
3. Test with different shells and terminal types

### Frontend Modifications
- Keep JavaScript simple and focused
- Maintain compatibility with xterm.js library
- Test across different browsers

### Performance Considerations
- Minimize message overhead in WebSocket protocol
- Efficient buffer handling for terminal I/O
- Avoid blocking operations in message handlers