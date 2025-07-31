# Task Completion Checklist

When completing any development task on the rtty project, ensure the following steps are performed:

## 1. Code Quality Checks
- [ ] Run `go fmt ./...` to format all Go files
- [ ] Run `golangci-lint run` to check for linting issues
- [ ] Fix any linting warnings or errors

## 2. Testing
- [ ] Run `go test -v ./...` to ensure all tests pass
- [ ] Add new tests for any new functionality (if applicable)
- [ ] Verify test coverage for critical paths

## 3. Build Verification
- [ ] Run `go build` to ensure the project builds successfully
- [ ] Test the built binary with basic functionality

## 4. Manual Testing
- [ ] Run the server: `./rtty run zsh -p 8080 -v`
- [ ] Open browser and verify WebSocket connection works
- [ ] Test terminal functionality (typing, resize, etc.)

## 5. Dependencies
- [ ] Run `go mod tidy` to clean up dependencies
- [ ] Commit both go.mod and go.sum if changed

## 6. Documentation
- [ ] Update README.md if functionality changes
- [ ] Update inline comments if complex logic is added

## 7. Git Hygiene
- [ ] Ensure commits follow TDD approach (test first, then implementation)
- [ ] Use clear commit messages with [STRUCTURAL] or [BEHAVIORAL] prefix
- [ ] Verify no secrets or sensitive data in commits

## Important Notes
- The project currently has no test files, so writing tests for new features is especially important
- Always use `ghost` for managing background processes during development
- Follow the established code style (minimal comments, self-documenting code)