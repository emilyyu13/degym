# Development Environment

## Preparation

### Install packages

```sh
$ docker compose run --rm nuxt npm install
```

## Start servers

```sh
$ docker compose up -d
```

## Run lint

```sh
$ docker compose run --rm nuxt npm run lint
# for auto-correct
$ docker compose run --rm nuxt npm run lint:fix
```
