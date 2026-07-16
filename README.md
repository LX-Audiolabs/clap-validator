# clap-validator

A validator and automatic test suite for [CLAP](https://github.com/free-audio/clap) plugins. Clap-validator can automatically test one or more plugins for common bugs and incorrect behavior.

> **This is a maintained fork** of [free-audio/clap-validator](https://github.com/free-audio/clap-validator) with DAW-typical lifecycle tests, updated dependencies, and Rust 2024 edition.

### Usage

Simply pass the path to one or more `.clap` plugins to `clap-validator validate`
to run the validator on those plugins. The `--only-failed` option can be used to
hide the output from all successful and skipped tests. Running `clap-validator
validate --help` lists all available options:

```shell
clap-validator validate /path/to/the/plugin.clap
clap-validator validate /path/to/the/plugin.clap --only-failed
clap-validator validate --help
```

### Debugging

clap-validator runs tests in separate processes by default so plugin crashes can
be treated as such instead of taking down the validator. If you want to attach a
debugger to debug the plugin's behavior during a specific test, you can tell the
validator to run the that test in the current process. Use `clap-validator list tests`
to list all available tests.

```shell
clap-validator validate --in-process --test-filter <test-case-name> /path/to/the/plugin.clap
```

## Building

Requires [Rust](https://rustup.rs/). Build and install:

```shell
cargo install --path .
```

Or run directly without installing:

```shell
cargo run --release -- validate /path/to/the/plugin.clap
```
