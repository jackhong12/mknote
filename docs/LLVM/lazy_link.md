# Lazy Link

```
getLazyIRModule
  parseModule
    BitcodeReader::parseConstants
    BitcodeReader::resolveGlobalAndIndirectSymbolInits
    BitcodeReader::globalCleanup
    BitcodeReader::parseFunctionRecord
    BitcodeReader::parseValueSymbolTable
    BitstreamCursor::readRecord
```

```
Linker::linkModules
  llvm::IRMover::move
```
