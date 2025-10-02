# GNU GCC

## Sanitizer

### AddressSanitizer

```bash
g++ -fsanitize=address -g your_program.cpp -o your_program
```

### UndefinedBehaviorSanitizer
```bash
g++ -fsanitize=undefined -g your_program.cpp -o your_program
```

### Keep Checking
Don't stop at the first error (AddressSanitizer):

```bash
export ASAN_OPTIONS=halt_on_error=0
```
