# QuestDB Web Console

This package contains code of the GUI for interacting with QuestDB.

It is a web application built with TypeScript and React and managed with
Yarn@3 and Webpack.

## Local development setup

In order to run this package locally, you need to do the following steps:

1. Clone and bootstrap repository (by following instructions on [`local-development-setup.md`](../../docs/local-development-setup.md)) 
2. Start development server
3. Run QuestDB in the background
4. Hack!

### 1. Clone and bootstrap repository

Consult instructions on [`local-development-setup.md`](../../docs/local-development-setup.md) document.

### 2. Start development server

```
yarn workspace @questdb/web-console start
```

[localhost:9999](http://localhost:9999) should show web console

### 3. Run QuestDB in the background

This package (`web-console`) is a only GUI for QuestDB, it does not include QuestDB itself.\
GUI will work without it, but because it's a tool to interact with QuestDB, you will need QuestDB as well.

Check [readme.md](https://github.com/questdb/questdb#install-questdb) of QuestDB to learn how to install it.

If you have [`docker`](https://docs.docker.com/get-docker/), then it's simply:

```
docker run -p 9000:9000 -p 9009:9009 -p 8812:8812 questdb/questdb
```

### 4. Hack!

Do your code changes and browser will automatically refresh [localhost:9999](http://localhost:9999).

Happy hacking!

## Build production version

1. Make sure dependencies are set up:

```
yarn
```

2. Run `build` script:

```
yarn workspace @questdb/web-console run build
```

3. Build process emits static HTML, CSS and JS files in `packages/web-console/dist`

## Run tests

### Unit tests

This package uses [Jest](https://jestjs.io/) for unit tests.

To run them locally while developing, run:

```
yarn workspace @questdb/web-console run test
```

This will start jest in watch mode and will rerun tests on file changes.

If you want to run tests once, use:

```
yarn workspace @questdb/web-console run test:prod
```

This command is also used in CI.

### Browser tests

This monorepo contains `browser-tests` package which is used to test
`web-console` package. `browser-tests` does not yet run as part of
`web-console` build on CI, but they can be used to test changes locally.

Tests are written with [Cypress](https://www.cypress.io/) E2E framework.

1. start `web-console` local dev environment as explained above in this document.
2. run tests with
  ```
  yarn workspace browser-tests test
  ```

  or

  ```
  yarn workspace browser-tests run cypress open
  ```
