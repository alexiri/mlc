# Markup Link Checker

[![crates.io](https://img.shields.io/crates/v/mlc.svg?color=orange)](https://crates.io/crates/mlc)
[![downloads](https://badgen.net/crates/d/mlc?color=blue)](https://crates.io/crates/mlc)
[![build status](https://gitlab.com/becheran/mlc_ci/badges/master/pipeline.svg)](https://gitlab.com/becheran/mlc_ci/pipelines)
[![license](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PRs welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/becheran/mlc/blob/master/CONTRIBUTING.md)

[![asciicast](https://asciinema.org/a/299100.svg)](https://asciinema.org/a/299100)

Check for broken links in markup files. Currently `html` and `markdown` files are supported. The Markup Link Checker can easily be integrated in your CI pipeline to prevent broken links in your markup docs.

## Features

* Find and check links in `markdown` and `html` files
* Support HTML links and plain URLs in `markdown` files
* Validated absolute and relative file paths and URLs
* User friendly command line interface
* Easy [CI pipeline integration](#ci-pipeline-integration)
* Very fast execution using [async](https://rust-lang.github.io/async-book/)
* Efficient link resolving strategy which tries with minimized network load
* Throttle option to prevent *429 Too Many Requests* errors

## Install Locally

There are different ways to install and use *mlc*.

### Cargo

Use rust's package manager [cargo](https://doc.rust-lang.org/cargo/) to install *mlc* from [crates.io](https://crates.io/crates/mlc):

``` bash
cargo install mlc
```

### Download Binaries

To download a compiled binary version of *mlc* go to [github releases](https://github.com/becheran/mlc/releases) and download the binaries compiled for `x86_64-unknown-linux-gnu` and `x86_64-apple-darwin`.

## CI Pipeline Integration

### GitHub Actions

Use *mlc* in GitHub using the *GitHub-Action* from the [Marketplace](https://github.com/marketplace/actions/markup-link-checker-mlc).

``` yaml
- name: Markup Link Checker (mlc)
  uses: becheran/mlc@v0.14.2
```

Use *mlc* [command line arguments](./docs/reference.md) using the `with` argument:

``` yaml
- name: Markup Link Checker (mlc)
  uses: becheran/mlc@v0.14.2
  with:
    args: ./README.md
```

### Binary

To integrate *mlc* in your CI pipeline running in a *linux x86_64 environment* you can add the following commands to download the tool:

``` bash
curl -L https://github.com/becheran/mlc/releases/download/v0.14.2/mlc -o mlc
chmod +x mlc
```

For example take a look at the [ntest repo](https://github.com/becheran/ntest/blob/master/.gitlab-ci.yml) which uses *mlc* in the CI pipeline.

### Docker

Use the *mlc* docker image from the [docker hub](https://hub.docker.com/repository/docker/becheran/mlc) which includes *mlc*.

## Usage

Once you have *mlc* installed, it can be called from the command line. The following call will check all links in markup files found in the current folder and all subdirectories:

``` bash
mlc
```

Another example is to call *mlc* on a certain directory or file:

``` bash
mlc ./docs
```

Call *mlc* with the `--help` flag to display all available cli arguments:

``` bash
mlc -h
```

See the [reference](./docs/reference.md) for all available command line arguments.

## Changelog

Checkout the [changelog file](https://github.com/becheran/mlc/blob/master/CHANGELOG.md) to see the changes between different versions.

## License

This project is licensed under the *MIT License* - see the [LICENSE file](https://github.com/becheran/mlc/blob/master/LICENSE) for more details.
