# Contributing to open-virbicoin

Thank you for helping improve `ovbc`, the Rust client for the VirBiCoin
network.

## Questions

Ask on the VirBiCoin [Discord](https://discord.virbicoin.com). GitHub issues are
for bug reports and feature requests.

## Reporting bugs

Please **do not** open a public issue for a suspected security vulnerability.
Report it privately to the maintainers instead, for example by direct message
on [Discord](https://discord.virbicoin.com).

For anything else,
[open an issue](https://github.com/virbicoin/open-virbicoin/issues/new) and
include:

- the output of `ovbc --version`
- your operating system and CPU architecture
- how you installed `ovbc` (release binary or built from source)
- whether the node is fully synchronized
- the steps to reproduce the problem, and the actual versus expected behavior

## Pull requests

1. Fork the repository, branch off `main`, and open the pull request against
   `main`.
2. Keep the change focused. `ovbc` is a fork of OpenEthereum: preserve the
   upstream code structure and license headers, and keep VirBiCoin-specific
   changes in the few places that already hold them (`bin/oe/params.rs`,
   `bin/oe/cli/`, `crates/ethcore/res/chainspec/virbicoin.json`,
   `crates/util/version/` and `crates/util/dir/`).
3. Build with the pinned toolchain (Rust 1.75.0 from `rust-toolchain.toml`).
   Many dependencies are pinned on purpose; if you change one, also run the
   built binary, because a passing `cargo check` does not prove that it starts.
4. Format the code with `cargo fmt` and make sure CI passes. The repository's
   git hooks run the same checks locally; enable them once per clone:

   ```shell
   git config core.hooksPath .githooks
   ```

   `pre-commit` runs `cargo fmt --all -- --check`, and `pre-push` runs
   `cargo check --locked --all` and validates the chain specs.

Consensus rules (the chain spec, block rewards and fork blocks) must stay in
lockstep with [go-virbicoin](https://github.com/virbicoin/go-virbicoin);
otherwise `ovbc` nodes fork off the network.

## License

By contributing, you agree that your contributions are licensed under the
licenses of the code you change (see [LICENSE](../LICENSE) and the header of
each file).
