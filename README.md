# PHOS

[![Go Report Card](https://goreportcard.com/badge/github.com/B1NARY-GR0UP/phos)](https://goreportcard.com/report/github.com/B1NARY-GR0UP/phos) [![coveralls](https://coveralls.io/repos/B1NARY-GR0UP/phos/badge.svg?branch=main&service=github)](https://coveralls.io/github/B1NARY-GR0UP/phos?branch=main)

> You Can (Not) Redo

![PHOS](images/PHOS.png)

PHOS is a channel with internal handlers and diversified options.

## Install

```shell
go get github.com/B1NARY-GR0UP/phos
```

## Quick Start

```go
package main

import (
    "context"
    "fmt"

    "github.com/B1NARY-GR0UP/phos"
)

func hello(_ context.Context, data string) (string, error) {
    return data + " PHOS", nil
}

func main() {
    ph := phos.New[string]()
    ph.Handlers = append(ph.Handlers, hello)
    ph.In <- "BINARY"
    res := <-ph.Out
    fmt.Println(res.Data)
}
```

## Configuration

| Configuration        | Default                | Description                                                                                    | Example                   |
|----------------------|------------------------|------------------------------------------------------------------------------------------------|---------------------------|
| `WithContext`        | `context.Background()` | Set context for PHOS                                                                           | [example](option_test.go) |
| `WithZero`           | `false`                | Return zero value when handle error happened                                                   | [example](option_test.go) |
| `WithTimeout`        | `time.Second * 3`      | Set timeout for handlers execution                                                             | [example](option_test.go) |
| `WithErrHandleFunc`  | `nil`                  | Set error handle function for PHOS which will be called when error happened                    | [example](option_test.go) |
| `WithErrTimeoutFunc` | `nil`                  | Set error timeout function for PHOS which will be called when timeout happened                 | [example](option_test.go) |
| `WithDoneFunc`       | `nil`                  | Set context done function for PHOS which will be called when context done during data handling | [example](option_test.go) |

## License

PHOS is distributed under the [Apache License 2.0](./LICENSE). The licenses of third party dependencies of PHOS are explained [here](./licenses).

## END

PHOS is a subproject of the [BINARY WEB ECOLOGY](https://github.com/B1NARY-GR0UP)