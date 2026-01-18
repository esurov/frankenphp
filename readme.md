# Frankenphp

This is a docker image for frankenphp, heavily inspired by [PHP official docker image](https://github.com/docker-library/php) and [ServerSide UP_ PHP](https://serversideup.net/open-source/docker-php/docs/image-variations/frankenphp). 

This image provides latest version of PHP 8.5.2 and uses `debian:trixie-slim` as a base image.

## License

GNU GENERAL PUBLIC LICENSE v3

## Links

* Website: https://frankenphp.dev/
* Docker: https://hub.docker.com/r/dunglas/frankenphp
* Github: https://github.com/php/frankenphp
* Serversideup-PHP: https://serversideup.net/open-source/docker-php/docs/image-variations/frankenphp

## Serversideup-PHP features

* Image: serversideup/php:8.5-frankenphp
* Dockerfile: https://github.com/serversideup/docker-php/blob/main/src/variations/frankenphp/Dockerfile

* ✅ Secure - Runs as unprivileged user (not root)
* ✅ Zero Config - Production-ready defaults, customize with environment variables
* ✅ Tooling - Composer, common extensions, and helpful utilities
* ✅ Laravel-optimized - Laravel automations (migrations, queues, Horizon, etc.)
* ✅ Modern Architecture - Native health checks, S6 Overlay, unified logging

## PHP image

* https://github.com/docker-library/php/blob/6485b53a1da0f2c4c5b564808de75ae62c023286/8.5/trixie/zts/Dockerfile
* https://github.com/docker-library/php/blob/6485b53a1da0f2c4c5b564808de75ae62c023286/8.5-rc/trixie/zts/Dockerfile

## Params

 * PHP version (current: 8.5.2)
 * PHP source download URL
 * PHP source SHA256 hash

## Step-by-step explanation

1. Use `debian:trixie-slim` image as a base
2. [Prevent Debian's PHP packages](https://github.com/docker-library/php/pull/542) from being installed by excluding php* packages in apt settings.
3. Install "phpize" dependencies:
  * autoconf
  * dpkg-dev
  * file
  * g++
  * gcc
  * libc-dev
  * make
  * pkg-config
  * re2c
4. Install persistent / runtime dependency packages:
  * ca-certificates
  * curl
  * xz-utils
5. [Allow running as an arbitrary user](https://github.com/docker-library/php/issues/743) by setting `www-data` as owner for `/var/www/html`
6. Set PHP version to 8.5.2, set the download URL, SHA256
7. Download PHP source and check SHA256 checksum
8. Tweak PHP compilation settings (optimizations and security)
9. GnuPG signature verified by:
  * install gnupg
  * use GPG_KEYS
  * import a public signing key from a keyserver.ubuntu.com
  * verify PHP tarball with GnuPG using ASC file
  * remove gnupg and it's dependencied
10. Install the build dependencies (removed after building):
  * libargon2-dev
  * libcurl4-openssl-dev
  * libonig-dev
  * libreadline-dev
  * libsodium-dev
  * libsqlite3-dev
  * libssl-dev
  * libxml2-dev
  * zlib1g-dev
11. Build PHP as zts (configure, make, make install)
12. Prepare pecl, copy docker-php-ext-* scripts for extension management
13. [Enable sodium extension](https://github.com/docker-library/php/issues/598)
14. Copy `/usr/local/go` from `golang:1.25`
15. Copy xcaddy from the caddy:builder image
16. Install dependencies:
  * libargon2-dev
  * libcurl4-openssl-dev
  * libonig-dev
  * libreadline-dev
  * libsodium-dev
  * libsqlite3-dev
  * libssl-dev
  * libxml2-dev
  * zlib1g-dev
  * cmake
  * git
  * libbrotli-dev
  * libcap2-bin
  * mailcap
17. Download and build e-dant/watcher for watching file changes
18. Clone frankenphp project: https://github.com/php/frankenphp.git
19. Build frankenphp with xcaddy
20. Install composer from Composer's official Docker image
21. Copy frankenphp caddyfiles into container /etc/frankenphp/
22. Install dependencies:
  * procps
  * libstdc++6
  * zip
23. Install php extensions:
  * opcache
  * pcntl
  * pdo_mysql
  * pdo_pgsql
  * redis
  * zip
24. Sets entrypoint, cmd and healthcheck.
