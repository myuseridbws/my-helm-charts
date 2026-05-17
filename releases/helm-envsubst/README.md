# helm-envsubst Helm Plugin Releases

See: [https://github.com/myuseridbws/helm-envsubst](https://github.com/myuseridbws/helm-envsubst)

## Quick Install Instructions

From any directory (the command installs into Helm's own plugin directory,
so your current working directory does not matter), run:

```sh
helm plugin install https://github.com/myuseridbws/helm-envsubst --verify=false
```

`--verify=false` is required: Helm v4 verifies plugins on install by default,
and this is an unsigned, legacy-format plugin. This only skips Helm's
plugin-signature check — the install hook still verifies the downloaded binary
against its published SHA-256 checksum (step 3 below). Signing the releases is
a possible future enhancement.

This single command:

1. Clones this repository into Helm's plugin directory — the path reported
   by `helm env HELM_PLUGINS`.
2. Reads `plugin.yaml` and runs the install hook, `install-binary.sh`.
3. The hook detects your OS and architecture, downloads the matching
   release tarball from the GitHub Pages site
   (`https://myuseridbws.github.io/my-helm-charts/releases/helm-envsubst/<version>/`),
   verifies its SHA-256 checksum, and extracts the `hsubst` binary into the
   plugin directory.

The version installed is whatever `plugin.yaml` on the default branch
currently declares.

