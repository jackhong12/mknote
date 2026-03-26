# Debug Tips for LLVM

To enable debug output in LLVM, you can set the `DEBUG_TYPE` environment
variable to the desired debug type. For example:

```
DEBUG_TYPE=debug
```

You can also use the `-debug-only` flag when running LLVM tools to
specify which debug output to enable. For example:
```
clang -debug-only=debug ...
```
