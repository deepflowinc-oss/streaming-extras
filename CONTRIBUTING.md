# Contribution Guidelines

If you have any issue, please report it to the [GitHub issue tracker for this project][issue].
When you open an issue, please check whether there is alredy similar one(s).

We are also accepting [Pull Requests][pulls] - you can feel free to open pull requests for small changes, e.g. typo correction.
If you are planning a considerably big change, however, please first discuss the change you want to make via an issue.

## Development Tooling

- For simplicity, we use `cabal-install >= 3.10` for build tool.
- GHC version policy: support the most recent minor releases of at least three major releases. We must support the most-recent Stackage LTS.
- We are using [`hpack`](https://github.com/sol/hpack) to generate `*.cabal` from `package.yaml`. Make sure all the `.cabal` files are up-to-date with `package.yaml`.
- We strongly recommend to use the [pre-commit][pre-commit] tool.
  It runs hooks shared across the repository in Git's pre-commit hook.
  Currently, the following hooks are enabled:
  
  + A protection rule for `main` branch preventing making commit to protected branch
  + Runs hpack if it's in `$PATH`.

[pre-commit]: https://pre-commit.com

There is no obligation about editors - you can use any editor of your choice.
We recommend to use [HLS][HLS] as a Language Server when available.

If you use VSCode, it is recommended to install the following extensions (as included in `.vscode/extensions.json`):

- [Haskell](https://marketplace.visualstudio.com/items?itemName=haskell.haskell) extension boosts productivity in writing Haskell.
- [Workspace Config+](https://marketplace.visualstudio.com/items?itemName=swellaby.workspace-config-plus) lets you coexist shared settings and local configs.
- [Run On Save](https://marketplace.visualstudio.com/items?itemName=emeraldwalk.RunOnSave) ensures `*.cabal`s to be up-to-date with `package.yaml`.

All the source code (except `Setup.hs`) MUST be formatted with [Fourmolu][fourmolu].
HLS supports fourmolu as a formatter, so we strongly recommend to use HLS and enable `Format on Save` in your editor.

[issue]: https://github.com/deepflowinc-oss/streaming-extras/issues
[pulls]: https://github.com/deepflowinc-oss/streaming-extras/pulls
[fourmolu]: https://github.com/fourmolu/fourmolu
[HLS]: https://github.com/haskell/haskell-language-server

## Pull Request Requirements

To get PRs merged, following criteria must be met:

- We require [commits to be signed][commit-sign] in order to be merged into main branch.
- The following tests must be all green:
  + `Fourmolu` - to enforce consistent formatting
  + `Build` and `Test` for non-head GHCs
- It is strongly recommended to write commit messages obeying [Conventional Commit][convcom] guidline.

[convcom]: https://www.conventionalcommits.org
[commit-sign]: https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits
