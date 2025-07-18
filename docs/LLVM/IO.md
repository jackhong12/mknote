# Read and Write Files

## raw_fd_ostream
```c++
#include "llvm/Support/raw_ostream.h"

int main() {
    std::error_code EC;

    llvm::raw_fd_ostream File("output.txt", EC, raw_fd_ostream::F_Binary);

    if (EC) {
        llvm::errs() << "Cannot open file: " << EC.message() << "\n";
        return 1;
    }

    File << "Hello, LLVM file output!\n";
    File << "This is another line.\n";

    return 0;
}
```

