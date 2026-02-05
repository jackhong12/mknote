# perf

Perf is a performance analysis tool for Linux systems. It can be used to collect and analyze performance data from various sources, including CPU, memory, and I/O.

```bash
sudo apt update
sudo apt install linux-tools-common linux-tools-generic
```

## Record and Report

- Record performance data for a specific command:
    ```bash
    perf record -g <command>
    perf report
    ```
