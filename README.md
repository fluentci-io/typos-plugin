# Typos Plugin

[![fluentci pipeline](https://shield.fluentci.io/x/typos)](https://pkg.fluentci.io/typos)
[![ci](https://github.com/fluentci-io/typos-plugin/actions/workflows/ci.yml/badge.svg)](https://github.com/fluentci-io/typos-plugin/actions/workflows/ci.yml)

This plugin sets up your CI/CD pipeline with a specific version of [typos](https://github.com/crate-ci/typos).

## 🚀 Usage

Add the following command to your CI configuration file:

```bash
fluentci run --wasm typos setup
```

## Functions

| Name   | Description                                |
| ------ | ------------------------------------------ |
| setup  | Installs a specific version of typos.      |
| check  | Finds typos in the source code.            |

## Code Usage

Add `fluentci-pdk` crate to your `Cargo.toml`:

```toml
[dependencies]
fluentci-pdk = "0.1.9"
```

Use the following code to call the plugin:

```rust
use fluentci_pdk::dag;

// ...

dag().call("https://pkg.fluentci.io/typos@v0.1.0?wasm=1", "setup", vec!["latest"])?;
```

## 📚 Examples

Github Actions:

```yaml
- name: Setup Fluent CI CLI
  uses: fluentci-io/setup-fluentci@v5
  with:
    wasm: true
    plugin: typos
    args: |
      lint
  env:
    GITHUB_ACCESS_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```
