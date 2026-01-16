# Frankenphp

Website: https://frankenphp.dev/
Docker: https://hub.docker.com/r/dunglas/frankenphp
Github: https://github.com/php/frankenphp
Serversideup-PHP: https://serversideup.net/open-source/docker-php/docs/image-variations/frankenphp

# Serve the public/ directory
docker run -v $PWD:/app/public \
  -p 443:443/tcp -p 443:443/udp \
  dunglas/frankenphp

# Run a command-line script
docker run -v $PWD:/app \
  dunglas/frankenphp php script.php


## Serversideup-PHP features

Image: serversideup/php:8.5-frankenphp
Dockerfile: https://github.com/serversideup/docker-php/blob/main/src/variations/frankenphp/Dockerfile

php:8.5-zts-trixie

docker pull ghcr.io/serversideup/php:8.5-frankenphp-trixie

✅ Secure - Runs as unprivileged user (not root)
✅ Zero Config - Production-ready defaults, customize with environment variables
✅ Tooling - Composer, common extensions, and helpful utilities
✅ Laravel-optimized - Laravel automations (migrations, queues, Horizon, etc.)
✅ Modern Architecture - Native health checks, S6 Overlay, unified logging

## PHP image

https://github.com/docker-library/php/blob/6485b53a1da0f2c4c5b564808de75ae62c023286/8.5/trixie/zts/Dockerfile
https://github.com/docker-library/php/blob/6485b53a1da0f2c4c5b564808de75ae62c023286/8.5-rc/trixie/zts/Dockerfile