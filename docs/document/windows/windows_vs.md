# Visual Studio

## Launch Settings

- Location: `Project Root\.vs\launch.vs.json`

### Arguments
| Property | Description                       |
|----------|-----------------------------------|
| `args`   | Command line arguments to pass to the executable |
| `name`   | Name of the launch configuration |
| `project`| Path to the executable to launch |

```json title="launch.vs.json"
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "bin\\Debug\\qclc.exe",
      "projectTarget": "",
      "name": "qclc-2",
      "args": [
        "--help"
      ]
    },
    {
      ...
    }
  ]
}
```


