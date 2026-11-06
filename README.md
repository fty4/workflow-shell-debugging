# workflow-shell-debugging

GitHub Action to debug workflow runs interactively in a shell via an [upterm](https://github.com/owenthereal/upterm) server (WebSocket).

## Usage

```yaml
steps:
  - uses: actions/checkout@v4

  - name: Debug with shell
    if: failure()
    uses: fty4/workflow-shell-debugging@main
    with:
      server: wss://upterm.example.com
```

The connection string is printed in the log of the `wait for upterm server to start` step. If nobody connects within 10 minutes the step ends and the workflow continues.

## Inputs

| Input      | Description                                                    | Default  |
|------------|----------------------------------------------------------------|----------|
| `server`   | Upterm server URL incl. scheme (`ws://` or `wss://`), required | -        |
| `continue` | Continue the workflow when the shell session is closed         | `true`   |
| `debug`    | Print additional debug output                                  | `false`  |
