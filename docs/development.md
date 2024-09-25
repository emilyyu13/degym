# Development Environment

## Preparation

### Prerequisites

* [Docker](https://www.docker.com/get-started/)
* [direnv](https://direnv.net/#getting-started)
* [mkcert](https://github.com/FiloSottile/mkcert?tab=readme-ov-file#installation)

### Fetch source code

```sh
$ git clone git@github.com:RubyDevInc/degym.git degym
```

### Create Certificates

```bash
$ cd development/nginx/certs
$ mkcert -cert-file cert.pem -key-file cert-key.pem "*.degym.jp" degym.jp
```

### Register Host Names

hostsファイルに以下を追加します

```
127.0.0.1 degym.jp
```

## Start servers

```sh
$ docker compose up -d
```

nuxtについては、[こちら](../modules/nuxt/docs/development.md)を見てください

railsについては、[こちら](../modules/rails/docs/development.md)を見てください

## Development Flow

以下のような流れで開発を行ってください

* 作業するissueを`In Progress`にする
* [GitHub flow](https://docs.github.com/en/get-started/using-github/github-flow)に従い、mainブランチから作業branchを作成する
* コミットメッセージは[Conventional Commits](https://www.conventionalcommits.org/)に従う
  * typeは以下を使用する (based on the [Angular convention](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#type))
    * build: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)
    * ci: Changes to our CI configuration files and scripts (example scopes: Travis, Circle, BrowserStack, SauceLabs)
    * docs: Documentation only changes
    * feat: A new feature
    * fix: A bug fix
    * perf: A code change that improves performance
    * refactor: A code change that neither fixes a bug nor adds a feature
    * style: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
    * test: Adding missing tests or correcting existing tests
  * ただし、開発初期はBREAKING CHANGEは考慮しない
  * [modules](../modules)以下の変更は、scopeをmodule名にしてコミットを分ける
  * issueを閉じることができるコミットには、`This commit fix #1`のように対応するissue番号のメッセージを追加する
    （pull requestがマージされたらissueが自動でcloseされます）
* mainブランチに向けてpull requestを作成しレビュー依頼をする
* issueを`In Review`にする
