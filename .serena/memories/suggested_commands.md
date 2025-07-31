# Suggested Commands for Development

## Build and Run
```bash
# Run the server locally
go run . run zsh -p 8080 -v --font "Cica Regular" --font-size 20

# Build the binary
go build

# Install to GOPATH/bin
go install github.com/skanehira/rtty@latest
```

## Testing
```bash
# Run all tests
go test -v ./...

# Run tests with coverage
go test -v -cover ./...
```

## Linting and Code Quality
```bash
# Run golangci-lint (used in CI)
golangci-lint run

# Format code
go fmt ./...

# Check for issues
go vet ./...
```

## Dependency Management
```bash
# Update dependencies
go mod tidy

# Download dependencies
go mod download

# Verify dependencies
go mod verify
```

## Git Commands
```bash
# Check status
git status

# Add changes
git add .

# Commit with message
git commit -m "message"

# Push to remote
git push origin main
```

## Release and Build
```bash
# Create a new release with goreleaser
goreleaser release --clean

# Test release build locally
goreleaser build --snapshot --clean
```

## System Commands (Darwin/macOS)
```bash
# List files
ls -la

# Find files
find . -name "*.go"

# Search in files
grep -r "pattern" .

# Watch file changes
fswatch -o . | xargs -n1 -I{} echo "File changed"
```

## Development Workflow
```bash
# 1. Make changes
# 2. Format code
go fmt ./...

# 3. Run linter
golangci-lint run

# 4. Run tests
go test -v ./...

# 5. Build and test manually
go build && ./rtty run zsh -p 8080 -v
```