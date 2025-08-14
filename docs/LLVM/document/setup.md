# Setup Environment

## Build Code
```bash
cmake -G Ninja \
    path/to/llvm-project/llvm \
    -DCMAKE_BUILD_TYPE=Debug \
    -DCMAKE_EXPORT_COMPILE_COMMANDS=ON \
    -DLLVM_USE_LINKER="lld"
ninja -j$(nproc)
```

??? Note "Flags"
    - `-DCMAKE_BUILD_TYPE=Debug`: Build in debug mode.
    - `-DCMAKE_EXPORT_COMPILE_COMMANDS=ON`: Generate compile commands for tools like clangd.
    - `-DLLVM_USE_LINKER="lld"`: Use the LLVM linker.
