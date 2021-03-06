<table align="center"><tr><td>
  <p><h1 align="center"><a href="https://github.com/z-shell/zi">
  <img align="center" src="https://github.com/z-shell/zi/raw/main/docs/images/logo.svg" alt="Logo" width="60px" height="60px" /></a>
    ❮ ZI ❯ Package - Amazon ECS CLI </p>
</h1>
<h3 align="center">
<table>
    <tr>
        <td><b>Package source:</b></td>
        <td>Source Tarball</td>
        <td>Binary</td>
        <td>Git</td>
        <td>Node</td>
        <td>Gem</td>
    </tr>
    <tr>
        <td><b>Status:</b></td>
        <td>❌</td>
        <td>✔️ (default)</td>
        <td>❌</td>
        <td>❌</td>
        <td>❌</td>
    </tr>
</table></h3>
<!--  <p><img align="center" src="https://user-images.githubusercontent.com/59910950/172339363-8a890ff1-5db7-4aa7-a674-77b72663cbcd.png" alt="zi apr package" width="100%" height="auto" /></p> -->
</td></tr></table>

## Available `pack''` invocations

```shell
# Download the binary of amazon-ecs-cli command
zi pack for ecs-cli
```

```shell
# Download the ecs-cli binary with use of the bin-gem-node annex
zi pack"bgn" for ecs-cli
```

## Default Profile

Provides the CLI command `ecs-cli` by coping it to `$ZPFX/bin`.

The ZI command executed will be equivalent to:

```zsh
zi as=null id-as="ecs-cli" mv="*latest -> ecs-cli" \
  atclone='chmod +x *; cp -vf ecs-cli $ZPFX/bin' \
  atpull="%atclone" sbin="ecs-cli" is-snippet for \
    https://amazon-ecs-cli.s3.amazonaws.com/ecs-cli-${(M)OSTYPE#(linux|darwin)}-amd64-latest
```

## `Bin-Gem-Node` Profile

Provides the CLI command `ecs-cli` by creating a forwarder script (a _shim_) in `$ZPFX/bin` by using the [bin-gem-node](https://github.com/z-shell/z-a-bin-gem-node) annex. It's the best method of providing the binary to the command line.

The ZI command executed will be equivalent to:

```zsh
zi as=null id-as="ecs-cli" mv="*latest -> ecs-cli" \
  atclone="chmod +x *"  atpull="%atclone" sbin="ecs-cli"
  is-snippet for \
    https://amazon-ecs-cli.s3.amazonaws.com/ecs-cli-${(M)OSTYPE#(linux|darwin)}-amd64-latest
```

---

> This repository compatible with [ZI](https://github.com/z-shell/zi)

The [aws/amazon-ecs-cli](https://github.com/aws/amazon-ecs-cli) zsh package that uses the [zsh-string-lib](https://github.com/z-shell/zsh-string-lib) to automatically:

- get the plugin's Git repository OR release-package URL,
- get the list of the recommended ices for the plugin,
  - there can be multiple lists of ices,
  - the ice lists are stored in _profiles_; there's at least one profile, _default_,
  - the ices can be selectively overridden.
