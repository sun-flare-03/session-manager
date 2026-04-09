# session-manager

[![Build Status](https://img.shields.io/github/actions/workflow/status/user/session-manager/ci.yml?branch=main)]()
[![Go Version](https://img.shields.io/badge/go-1.22+-blue.svg)]()
[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

Secure session management with pluggable stores and CSRF protection — designed for production workloads with a focus on reliability and developer ergonomics.

## Features

- Graceful Shutdown: Clean shutdown handling with configurable drain timeout
- Minimal Allocations: Designed to minimize GC pressure in hot paths
- Structured Logging: Built-in structured logging with slog compatibility
- Zero Dependencies: No external packages required for core functionality
- High Performance: Optimized for low-latency, high-throughput workloads

## Getting Started

### Installation

```bash
go get github.com/user/session-manager@latest
```

## Usage

```go
package main

import (
	"fmt"
	"github.com/user/session-manager"
)

func main() {
	client := sessionmanager.New(
		sessionmanager.WithTimeout(30 * time.Second),
	)

	result, err := client.Run(context.Background())
	if err != nil {
		log.Fatal(err)
	}

	fmt.Println(result)
}
```

## Configuration

Configuration can be provided via environment variables, a config file, or programmatically.

| Variable | Description | Default |
|----------|-------------|--------|
| `SESSION_MANAGER_TIMEOUT` | Request timeout in seconds | `30` |
| `SESSION_MANAGER_RETRIES` | Number of retry attempts | `3` |
| `SESSION_MANAGER_LOG_LEVEL` | Log verbosity (debug, info, warn, error) | `info` |

## Contributing

Contributions are welcome! Please read the [contributing guidelines](CONTRIBUTING.md) before submitting a pull request.

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'feat: add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.
