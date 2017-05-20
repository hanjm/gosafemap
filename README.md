fork from <https://github.com/DeanThompson/syncmap>
changes:
- change ShardCount uint8(max255, the max value which can be ShardCount is 128) to uint16(max65535, the max value which can be ShardCount is 32768), 128 is too small.
- NewWithShard():add shard map preSize, pre allocate memory for large map to improve performance.

======
syncmap
=======

A thread safe map implementation for Golang

## Usage

Install with:

```bash
go get github.com/hanjm/syncmap
```

Example:

```go
import (
    "fmt"

    "github.com/hanjm/syncmap"
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
