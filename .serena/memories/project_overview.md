# rtty Project Overview

## Purpose
rtty (Remote TTY) is a terminal emulator that runs in a web browser via WebSocket. It allows users to access a terminal session through a web interface, making it possible to run command-line tools remotely through a browser.

## Core Features
- Run any command/shell in a browser
- WebSocket-based real-time communication
- Terminal resize support
- Configurable font and font size
- Cross-platform support (Linux and macOS)

## Tech Stack
- **Language**: Go 1.23.0+ (currently using Go 1.24.4)
- **Backend Framework**: 
  - Cobra for CLI commands
  - Standard Go net/http and golang.org/x/net/websocket for WebSocket server
  - creack/pty for pseudo-terminal handling
- **Frontend**: 
  - Vanilla JavaScript
  - xterm.js for terminal emulation in the browser
  - WebSocket API for communication

## Project Structure
```
.
├── cmd/               # Command implementations
│   ├── public/       # Frontend assets (HTML, JS, CSS)
│   ├── root.go       # Root command
│   ├── run.go        # Main run command (WebSocket server)
│   ├── version.go    # Version command
│   └── util.go       # Utility functions
├── main.go           # Entry point
├── go.mod            # Go module definition
├── go.sum            # Go module checksums
├── Makefile          # Build automation
├── .goreleaser.yaml  # Release configuration
└── .github/
    └── workflows/    # CI/CD workflows
```

## Key Components
1. **WebSocket Server**: Handles browser connections and terminal I/O
2. **PTY Management**: Creates and manages pseudo-terminals for running commands
3. **Message Protocol**: JSON-based messaging between browser and server
4. **Event Handling**: Supports resize, key input, and close events