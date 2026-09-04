<p align="center">
  <a href="https://rapira.rs"><img src="https://rapira.rs/logo.svg" alt="Rapira" width="360" /></a>
</p>

<p align="center">A Rust application server for PHP.</p>

<p align="center">
  <a href="https://rapira.rs">Rapira website</a>
  ·
  <a href="https://rapira.rs/docs/intro/">Rapira documentation</a>
  ·
  <a href="https://rapira.rs/docs/intro/quickstart">Rapira quickstart</a>
  ·
  <a href="https://github.com/rapira-rs/rapira/releases">Rapira releases</a>
</p>

## About Rapira

Rapira is a Rust application server for PHP. The maintainers of [RoadRunner](https://github.com/roadrunner-server/roadrunner) develop Rapira. It uses the PHP embed SAPI to load non-thread-safe (NTS) PHP in the server process. Rapira calls the PHP interpreter directly. It does not use FastCGI, a socket between Rapira and PHP, or per-request serialization. Plugins extend Rapira.

Rapira has three execution modes:

- [Classic mode](https://rapira.rs/docs/classic) runs the front controller for each request. It can replace `php-fpm` for an existing PHP application. The application does not need code changes.
- [Worker mode](https://rapira.rs/docs/worker) keeps the application in memory. Rapira initializes the application one time for each worker and calls a handler for each request.
- [Dispatcher mode](https://rapira.rs/docs/execution-modes#dispatcher) keeps the application in memory. It gives each HTTP request to the application as a `Rapira\Http\Exchange` object. Dispatcher is the default mode.

## Getting started

Rapira release packages and tar archives include NTS PHP. You do not need to install PHP separately. Use the [download page](https://rapira.rs/download) to select a file for your operating system, processor architecture, PHP version, and package format. Verify the file before installation. Follow the [installation guide](https://rapira.rs/docs/intro/installation).

After installation, start an existing application in Classic mode:

```sh
rapira serve --mode classic public/index.php
```

Release packages and tar archives contain a fixed set of PHP extensions. See the [current extension list](https://rapira.rs/docs/intro/installation#the-libphp-build). If your application needs other extensions, [build a compatible NTS `libphp` with the required extensions](https://rapira.rs/docs/intro/build-from-source#building-php-yourself). You do not need to rebuild Rapira.

Use the `ghcr.io/rapira-rs/rapira:php8.4` or `ghcr.io/rapira-rs/rapira:php8.5` container image. Each image uses `scratch` as its base. Rapira does not publish a `latest` tag. The image contains Rapira and `libphp.so`. It cannot run by itself. Copy its files into your application image. See the [Docker instructions](https://rapira.rs/docs/intro/installation#docker).

For more information, see the [quickstart](https://rapira.rs/docs/intro/quickstart), [Worker mode guide](https://rapira.rs/docs/worker), and [framework guides for Symfony, Laravel, and Yii 3](https://rapira.rs/docs/frameworks/).

## Main repositories

- The [rapira](https://github.com/rapira-rs/rapira) repository contains the Rust server core and its integration with the PHP embed SAPI.
- The [sdk-php](https://github.com/rapira-rs/sdk-php) repository contains PSR-7 request factories and test utilities. The project publishes each SDK component as a separate Composer package.
- The [yii-runner-rapira](https://github.com/rapira-rs/yii-runner-rapira) repository contains the Yii 3 application runner for Worker mode.
- The [rapira-rs.github.io](https://github.com/rapira-rs/rapira-rs.github.io) repository contains the source for the [rapira.rs](https://rapira.rs) documentation site.

## Contributing

Open PHP SDK issues in the [sdk-php issue tracker](https://github.com/rapira-rs/sdk-php/issues). Open all other issues in the [Rapira issue tracker](https://github.com/rapira-rs/rapira/issues). See the [Rapira contribution guide](https://github.com/rapira-rs/rapira/blob/main/CONTRIBUTING.md) for build and test instructions.
