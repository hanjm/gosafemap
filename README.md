syncmap
=======

A thread safe map implementation for Golang

## Usage

Install with:

```bash
go get github.com/hanjm/gosafemap
```

Example:

```go
import (
    "fmt"

    "github.com/hanjm/gosafemap"
)

func main() {
    m := syncmap.New()
    m.Set("one", 1)
    v, ok := m.Get("one")
    fmt.Println(v, ok)  // 1, true

    v, ok = m.Get("not_exist")
    fmt.Println(v, ok)  // nil, false

    m.Set("two", 2)
    m.Set("three", "three")

    for item := range m.IterItems() {
        fmt.Println("key:", item.Key, "value:", item.Value)
    }
}
```
