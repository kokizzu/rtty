# Code Style and Conventions

## Go Code Style
- **Go Version**: 1.23.0+ (go.mod), using Go 1.24.4 toolchain
- **Module Name**: github.com/skanehira/rtty
- **Package Structure**: 
  - Main package in root
  - Command implementations in `cmd` package
  - Embedded assets using `embed` package

## Naming Conventions
- **Files**: Snake_case (e.g., `run.go`, `version.go`)
- **Functions**: CamelCase with exported functions starting with uppercase
- **Variables**: camelCase for private, CamelCase for exported
- **Constants**: CamelCase (e.g., `EventResize`, `EventSendkey`)

## Code Organization
- Commands are implemented using Cobra framework
- Each command has its own file in the `cmd` directory
- Utility functions are centralized in `util.go`
- Embedded frontend assets are stored in `cmd/public`

## Error Handling
- Errors are logged using standard `log` package
- HTTP/WebSocket errors are handled gracefully
- Command execution errors are reported to the client

## Comments and Documentation
- Minimal inline comments (code should be self-documenting)
- Using `//nolint` directives where necessary for linter exceptions
- No extensive function documentation observed

## Dependencies
- Minimal external dependencies
- Main dependencies: cobra (CLI), creack/pty (terminal), websocket
- All dependencies managed via go.mod

## Build Configuration
- CGO_ENABLED=0 for static binaries
- Supports Linux and Darwin (macOS) platforms
- Uses ldflags for version injection during build