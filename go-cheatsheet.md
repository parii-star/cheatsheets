# Go Cheat Sheet

> **Goal:** Quick reference for Go basics, commands, and DevOps use cases.

## Go At A Glance

| Topic | Quick Answer |
|---|---|
| What is Go? | A fast compiled language made by Google |
| Main use | Backend, cloud, DevOps, Kubernetes, automation |
| Why use it? | Simple code, fast builds, one binary |
| Main strength | Concurrency |

## How To Read This Sheet

| Pattern | Meaning |
|---|---|
| `[file]` | Replace with a real file name, such as `main.go` |
| `[module]` | Replace with a Go module path, such as `example.com/app` |
| `[package]` | Replace with a package name or import path |

## Core Ideas

| Term | Meaning |
|---|---|
| Compiled language | Code becomes a binary before it runs |
| `package main` | Declares an executable application package |
| `func main()` | Program entry point |
| `import` | Brings in another package |
| `err != nil` | Standard Go error check |
| `go` keyword | Starts a goroutine |
| `defer` | Runs cleanup at the end of a function |

## Minimal Program

```go
package main

import "fmt"

func main() {
	fmt.Println("Hello, world")
}
```

Run it:

```bash
go run main.go
```

## Common Commands

| Command | What It Does |
|---|---|
| `go version` | Show the installed Go version |
| `go env` | Show Go environment settings |
| `go env GOPATH` | Show the Go workspace path |
| `go env GOMOD` | Show the active module file path |
| `go run [file]` | Run one Go file immediately |
| `go run .` | Run the current module if it has a `main` package |
| `go build` | Build an executable binary |
| `go build ./...` | Compile all packages in the module |
| `go test` | Run tests for the current package |
| `go test ./...` | Run tests in all packages |
| `go mod init [module]` | Create a new module |
| `go mod tidy` | Add missing dependencies and remove unused ones |
| `go get [package]` | Add or update a dependency |
| `go list -m all` | List all module dependencies |
| `go fmt ./...` | Format all Go source files |
| `go vet ./...` | Check for common mistakes |
| `go doc [package]` | Show package documentation |
| `go clean` | Remove build artifacts |

## Quick Project Flow

```text
Code -> Format -> Test -> Build -> Run
```

Example:

```bash
go fmt ./...
go test ./...
go build
./app
```

## Start A New Project

```bash
mkdir app
cd app
go mod init example.com/app
touch main.go
go run .
```

Basic `main.go`:

```go
package main

import "fmt"

func main() {
	fmt.Println("Hello from Go")
}
```

## Working With Modules

| Task | Command |
|---|---|
| Create a module | `go mod init example.com/app` |
| Add a dependency | `go get github.com/spf13/cobra` |
| Clean dependencies | `go mod tidy` |
| List dependencies | `go list -m all` |

## Build And Test

| Task | Command |
|---|---|
| Build current package | `go build` |
| Build all packages | `go build ./...` |
| Run current tests | `go test` |
| Run all tests | `go test ./...` |
| Format code | `go fmt ./...` |
| Run static checks | `go vet ./...` |

## Useful Snippets

### Error Check

```go
if err != nil {
	return err
}
```

### Defer Cleanup

```go
file, err := os.Open("config.yaml")
if err != nil {
	return err
}
defer file.Close()
```

### Goroutine

```go
go func() {
	fmt.Println("running in the background")
}()
```

## Where DevOps Engineers Use Go

Use Go when you need fast command-line tools, automation, or backend services.

- Build internal CLIs for deployment and infrastructure tasks.
- Write controllers, agents, and operators for cloud systems.
- Create fast services that fit well in containers and Kubernetes.
- Ship one compiled binary without a large runtime dependency.

## Daily DevOps Commands

| Use Case | Command |
|---|---|
| Check installed Go | `go version` |
| Run a local tool | `go run .` |
| Test before commit | `go test ./...` |
| Format before commit | `go fmt ./...` |
| Build a binary | `go build -o app` |
| Clean module files | `go mod tidy` |
