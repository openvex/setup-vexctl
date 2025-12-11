# setup-vexctl GitHub Action

This action enables you to install [vexctl](https://github.com/openvex/vexctl)

## Usage

This action currently supports GitHub-provided Linux, macOS and Windows runners (self-hosted runners may not work).

Add the following entry to your Github workflow YAML file:

```yaml
uses: openvex/setup-vexctl@main
with:
  vexctl-release: '0.3.0' # optional
```

Example using a pinned version:

```yaml
jobs:
  test_vexctl_action:
    runs-on: ubuntu-latest

    permissions: {}

    name: Install vexctl and test presence in path
    steps:
      - name: Install vexctl
        uses: openvex/setup-vexctl@main
        with:
          vexctl-release: '0.3.0' # optional
      - name: Check install!
        run: vexctl version
```

Example using the default version:

```yaml
jobs:
  test_vexctl_action:
    runs-on: ubuntu-latest

    permissions: {}

    name: Install vexctl and test presence in path
    steps:
      - name: Install vexctl
        uses: openvex/setup-vexctl@main
      - name: Check install!
        run: vexctl version
```

### Optional Inputs

The following optional inputs:

| Input | Description |
| --- | --- |
| `vexctl-release` | `vexctl` version to use instead of the default. |
| `cosign-release` | `cosign` version to use instead of the default. |
| `install-dir` | directory to place the `vexctl` binary into instead of the default (`$HOME/.vexctl`). |
| `use-sudo` | set to `true` if `install-dir` location requires sudo privs. Defaults to false. |
