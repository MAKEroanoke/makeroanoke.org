
# Docker

`jstart` starts jekyll in docker with `--livereload`. The first argument will specify a separate relative path for the mounted volume.

## Jekyll Environment

The following environment variables are referenced in jekyll's source:

+ JEKYLL_ENV
+ JEKYLL_LOG_LEVEL
+ JEKYLL_NO_BUNDLER_REQUIRE
+ BUNDLE_GEMFILE
+ TZ
+ DEBUG

## Compose

Copy `docker-compose.eg.yml` to `docker-compose.yml` for a basic config

### Multiple Jekyll Instances

To start, run:

```sh
docker compose -f docker-compose.jekyll.yml --env-file .jekyll.env up
```

`.env` file format:

```sh
_JEKYLL_PORT=4001
_JEKYLL_LIVE_RELOAD=35729
```

Docker compose file:

```yaml
---
version: "3.8"
services:
  jekyll:
    image: "bretfisher/jekyll-serve:alpine"
    command: "bundle exec jekyll serve --force_polling -H 0.0.0.0 -P ${_JEKYLL_PORT} --livereload --livereload-port ${_JEKYLL_LIVE_RELOAD} $@"
    ports:
      - "${_JEKYLL_PORT}:${_JEKYLL_PORT}"
      - "${_JEKYLL_LIVE_RELOAD}:${_JEKYLL_LIVE_RELOAD}"
    volumes:
      - './site:/site'
```

This is mostly useful when using `git worktree`, but that requires a lot of setup. Also, each branch to have its own git-ignored files like `.vscode`. `docker-compose.yml` or `node_modules`.

# Chromium

`crstart` starts a chromium browser with the window name set to `makeroanoke`.

The script will launch chrome with a custom profile if `CHROME_USER_DATA` is set. This allows you to apply custom settings like a distinct theme, making the window easier to spot.
