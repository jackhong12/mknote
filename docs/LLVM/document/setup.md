# Setup Environment

## Build Code
```bash
cmake -G Ninja path/to/llvm-project/llvm -DCMAKE_BUILD_TYPE=Debug
ninja -j$(nproc)
```
