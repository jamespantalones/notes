### Sorting interface

* requires `Len`, `Swap`, `Less`

```go
func (a ByAge) Len() int           { return len(a) }
func (a ByAge) Swap(i, j int)      { a[i], a[j] = a[j], a[i] }
func (a ByAge) Less(i, j int) bool { return a[i].Age < a[j].Age }
```


```
Receivers           Values
--------------------------------
(t T)               T and *T
(t *T)              *T
