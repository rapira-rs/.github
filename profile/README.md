<p align="center">
  <a href="https://rapira.rs"><img src="https://github.com/rapira-rs/rapira-rs.github.io/blob/main/public/logo.svg" alt="Rapira" width="360" /></a>
</p>

<p align="center">A post-modern PHP application server.</p>

<p align="center">
  <a href="https://rapira.rs">Website</a>
  ·
  <a href="https://rapira.rs/docs/intro/">Documentation</a>
  ·
  <a href="https://rapira.rs/docs/intro/quickstart">Quickstart</a>
  ·
  <a href="https://github.com/rapira-rs/rapira/releases">Releases</a>
</p>

## 👋 What is Rapira

Rapira is a PHP application server written in Rust, built by the maintainers of [RoadRunner](https://github.com/roadrunner-server/roadrunner). It embeds NTS PHP into the server process through PHP's embed SAPI: the host calls the interpreter directly, with no FastCGI, no sockets, no per-request serialization, and serves HTTP through a bundled [Pingora](https://github.com/cloudflare/pingora)-based front.

Run an existing app unchanged in classic mode (a front controller executed per request, where php-fpm used to sit), or keep it resident in worker mode and pay the bootstrap cost once per worker instead of once per request.

## 📦 Which repo is which

- [rapira](https://github.com/rapira-rs/rapira): the server itself - the Rust core, the embed SAPI integration, and the Pingora HTTP front. Start here.
- [contract](https://github.com/rapira-rs/contract): the PHP-side contract - declares the types the PHP/Rust boundary speaks; the server provides the objects.
- [sdk-php](https://github.com/rapira-rs/sdk-php): development monorepo for the PHP building blocks; each one ships as its own split package:
  - [http-php](https://github.com/rapira-rs/http-php): `rapira/http` - PSR-7 server-request factories for every run mode.
  - [testing-php](https://github.com/rapira-rs/testing-php): `rapira/testing` - provisions the server binary and runs a live server around your test cases.
- [yii-runner-rapira](https://github.com/rapira-rs/yii-runner-rapira): web application runner for Yii3.
- [rapira-windows](https://github.com/rapira-rs/rapira-windows): ZTS Windows build with full feature parity, used for testing purposes.
- [rapira-rs.github.io](https://github.com/rapira-rs/rapira-rs.github.io): source of the documentation site, [rapira.rs](https://rapira.rs).

## 🚀 Getting started

Every [release](https://github.com/rapira-rs/rapira/releases) bundles PHP 8.4 or 8.5 (NTS) - no separate PHP installation needed. Grab the package or tarball for your platform:

```sh
sudo apt install ./rapira-php8.5_<version>_amd64.deb
rapira serve --mode classic public/index.php
```

Docker images live at `ghcr.io/rapira-rs/rapira`, staged for copying into your own image. Full instructions: [installation](https://rapira.rs/docs/intro/installation), [quickstart](https://rapira.rs/docs/intro/quickstart), [worker mode](https://rapira.rs/docs/worker), and framework guides for [Symfony, Laravel, and Yii3](https://rapira.rs/docs/frameworks/).

## 🤝 Contributing

Found a bug or want a feature? Open an issue in the matching repository; when in doubt, [rapira-rs/rapira](https://github.com/rapira-rs/rapira/issues) is the right place. Build and test instructions are in [CONTRIBUTING.md](https://github.com/rapira-rs/rapira/blob/main/CONTRIBUTING.md).
