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

Rapira is a PHP application server written in Rust, built by the maintainers of [RoadRunner](https://github.com/roadrunner-server/roadrunner). It embeds NTS PHP into the server process through PHP's embed SAPI: the host calls the interpreter directly, with no FastCGI, no sockets, no per-request serialization. Like RoadRunner, the server is extended through plugins.

Run an existing app unchanged in classic mode (a front controller executed per request, where php-fpm used to sit), or keep it resident in worker mode and pay the bootstrap cost once per worker instead of once per request.

## 📦 Which repo is which

- [rapira](https://github.com/rapira-rs/rapira): the server itself - the Rust core, the embed SAPI integration, and the Pingora HTTP front. Start here.
- [sdk-php](https://github.com/rapira-rs/sdk-php): the PHP building blocks - PSR-7 request factories, testing utilities, and helpers, each published as its own package.
- [yii-runner-rapira](https://github.com/rapira-rs/yii-runner-rapira): web application runner for Yii3.
- [rapira-rs.github.io](https://github.com/rapira-rs/rapira-rs.github.io): source of the documentation site, [rapira.rs](https://rapira.rs).

## 🚀 Getting started

Every [release](https://github.com/rapira-rs/rapira/releases) bundles PHP (NTS) - no separate PHP installation needed. Grab the package or tarball for your platform and PHP version:

```sh
sudo apt install ./rapira-php<X.Y>_<version>_amd64.deb
rapira serve --mode classic public/index.php
```

Docker images live at `ghcr.io/rapira-rs/rapira`, staged for copying into your own image. Full instructions: [installation](https://rapira.rs/docs/intro/installation), [quickstart](https://rapira.rs/docs/intro/quickstart), [worker mode](https://rapira.rs/docs/worker), and framework guides for [Symfony, Laravel, and Yii3](https://rapira.rs/docs/frameworks/).

## 🤝 Contributing

Found a bug or want a feature? Open an issue in the matching repository; when in doubt, [rapira-rs/rapira](https://github.com/rapira-rs/rapira/issues) is the right place. Build and test instructions are in [CONTRIBUTING.md](https://github.com/rapira-rs/rapira/blob/main/CONTRIBUTING.md).
