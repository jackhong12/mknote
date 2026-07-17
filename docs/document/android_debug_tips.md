# Android Debug Tips

## Command Line Tools ([[android_adb|ADB]])
To access the command line on an Android device, you can use the Android Debug Bridge (ADB) tool. ADB allows you to communicate with your device and execute commands directly on it. To start a shell session on your Android device, run the following command:
```bash
adb shell
```

## Libraries
### Apply Different Libraries
If you want to apply different versions of libraries, you can set the `LD_LIBRARY_PATH` environment variable to point to the directory containing the desired libraries. For example:

```bash
LD_LIBRARY_PATH=/data/local/tmp/lib:$LD_LIBRARY_PATH <your_program>
```

### Check Loaded Shared Libraries
After entering the shell, we can use `LD_DEBUG` to get detailed information about the dynamic linker and the libraries it loads. Because `LD_DEBUG=libs` is not supported in android, we use the optoin `all` and grep the linking information. Run the following command to see the linking process:

```bash
LD_DEBUG=all <your_program> 2>&1 | grep Linking
```
