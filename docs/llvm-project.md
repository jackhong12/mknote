# LLVM Project

## Build Code
```bash
cmake -G Ninja -DLLVM_ENABLE_PROJECTS="clang" -DCMAKE_BUILD_TYPE="Debug" <path-to-llvm-project>/llvm
ninja -j$(nproc)
```


## Issue

- [clang:frontend](https://github.com/llvm/llvm-project/issues?q=state%3Aopen%20label%3A%22clang%3Afrontend%22)
- [first good issue](https://github.com/llvm/llvm-project/issues?q=state%3Aopen%20label%3A%22good%20first%20issue%22)

### Work Flow

| Status      | Icons                         | Admonition |
| :---        | :---                          | :---       |
| Track       | :material-format-quote-close: | `quote`    |
| In Progress | :material-fire:               | `tip`      |
| Done        | :material-check:              | `success`  |

### `clang:frontend`

??? Quote "[180313](https://github.com/llvm/llvm-project/issues/180313)"

### Warnings

??? Tip "OnDiskGraphDB"
    ```cpp title="OnDiskGraphDB.cpp" linenums="1421"
    OnDiskGraphDB::FileBackedData
    StandaloneDataInMemory::getInternalFileBackedObjectData(
        StringRef RootPath) const {
      switch (SK) {
      case TrieRecord::StorageKind::Unknown:
      case TrieRecord::StorageKind::DataPool:
        llvm_unreachable("unexpected storage kind");
      case TrieRecord::StorageKind::Standalone:
        return OnDiskGraphDB::FileBackedData{getContent().getData(),
                                             /*FileInfo=*/std::nullopt};
      case TrieRecord::StorageKind::StandaloneLeaf0:
      case TrieRecord::StorageKind::StandaloneLeaf:
        bool IsFileNulTerminated = SK == TrieRecord::StorageKind::StandaloneLeaf0;
        SmallString<256> Path;
        ::getStandalonePath(RootPath, TrieRecord::getStandaloneFilePrefix(SK),
                            IndexOffset, Path);
        return OnDiskGraphDB::FileBackedData{
            getContent().getData(), OnDiskGraphDB::FileBackedData::FileInfoTy{
                                        std::string(Path), IsFileNulTerminated}};
      }
    }
    ```

    ```
    /home/zjackhua/open-source/llvm-project/llvm/lib/CAS/OnDiskGraphDB.cpp: In member function ‘llvm::cas::ondisk::OnDiskGraphDB::FileBackedData {anonymous}::StandaloneDataInMemory::getInternalFileBackedObjectData(llvm::StringRef) const’:
    /home/zjackhua/open-source/llvm-project/llvm/lib/CAS/OnDiskGraphDB.cpp:1441:1: warning: control reaches end of non-void function [-Wreturn-type]
    1441 | }
         | ^
    ```
