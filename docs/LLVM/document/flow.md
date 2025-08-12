# Flow


Generate LLVM IR with clang:

```bash
clang -S -emit-llvm code.c -o code.ll
```

Run optimizations:

```bash
opt -O3 code.ll -o code_opt.ll
```
