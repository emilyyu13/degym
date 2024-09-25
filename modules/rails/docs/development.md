# Development Environment

## Preparation

### Install packages

```sh
# create secret environment file
$ echo RAILS_MASTER_KEY= > .env.rails.secret
$ docker compose run --rm rails bundle install
```

### Create secret environment variables

master keyを生成します

```sh
$ docker compose run --rm rails bundle exec rails runner "puts ActiveSupport::EncryptedFile.generate_key"
```

生成されたmaster keyを .env.rails.secret に設定します

```
RAILS_MASTER_KEY=<master_key>
```

## Setup databases

```sh
$ docker compose run --rm rails bundle exec rails db:create
```

## Load seed data

```sh
$ docker compose run --rm rails bundle exec rails db:seed
```

## Start servers

```sh
$ docker compose up -d
```

## Run lint

```sh
$ docker compose run --rm rails bundle exec rubocop
# for auto-correct
$ docker compose run --rm rails bundle exec rubocop -a
```

## Run tests

```sh
$ docker compose run --rm rails bundle exec rspec
```
