<h2 align="center">
  <a href="https://github.com/z-shell/zi">
    <img src="https://github.com/z-shell/zi/raw/main/docs/images/logo.svg" alt="Logo" width="80" height="80" />
  </a>
❮ ZI ❯ Package - Amazon ECS CLI
</h2>

<h3 align="center">

| **Package source:** | Source Tarball |            Binary            | Git | Node | Gem |
| :-----------------: | :------------: | :--------------------------: | :-: | :--: | :-: |
|     **Status:**     |      :x:       | :heavy_check_mark: (default) | :x: | :x:  | :x: |

</h3>

- [Available `pack''` invocations](#available-pack-invocations)
- [Default Profile](#default-profile)
- [`Bin-Gem-Node` Profile](#bin-gem-node-profile)

> This repository compatible with [ZI](https://github.com/z-shell/zi)

The [aws/amazon-ecs-cli](https://github.com/aws/amazon-ecs-cli) zsh package than can use the NPM package registry to automatically:

-   get the plugin's Git repository OR release-package URL,
-   get the list of the recommended ices for the plugin,
    -   there can be multiple lists of ices,
    -   the ice lists are stored in _profiles_; there's at least one profile, _default_,
    -   the ices can be selectively overridden.

## Available `pack''` invocations

```zsh
# Download the binary of amazon-ecs-cli command
zi pack for ecs-cli

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

Provides the CLI command `ecs-cli` by creating a forwarder script (a _shim_) in
`$ZPFX/bin` by using the
[bin-gem-node](https://github.com/z-shell/z-a-bin-gem-node) annex. It's the best
method of providing the binary to the command line.

The ZI command executed will be equivalent to:

```zsh
zi as=null id-as="ecs-cli" mv="*latest -> ecs-cli" \
    atclone="chmod +x *"  atpull="%atclone" sbin="ecs-cli"
    is-snippet for \
        https://amazon-ecs-cli.s3.amazonaws.com/ecs-cli-${(M)OSTYPE#(linux|darwin)}-amd64-latest
```
