## pool 提供一些常用的 pool 的封装

### BytesBufferPool

```text
BytesBufferPool 提供了类似 sync.Pool 的功能，但它能永久缓存指定个数的 *bytes.Buffer，不会被 GC 回收。

这个特性在某些场合有一定的作用，比如打印日志的时候，需要一个比较大的 *bytes.Buffer，一般是 16KB 或者更大，
这样写日志的时候就不需要 grow byte slice，也不会被 GC 回收，能够重复的使用！

对于极高并发的请求, BytesBufferPool 的性能要低于 sync.Pool, 请谨慎选择使用，一般都是需要很大的 buffer 的时候考虑使用.
```
