# XDCPay Browser Extension

## Introduction

Test of New Wallet Features

## Building locally

 - Install [Node.js](https://nodejs.org/en/) version 14.17.3 and npm version 6.14.16
   - If you are using [nvm](https://github.com/creationix/nvm#installation) (recommended) running `nvm use` will automatically choose the right node version for you.
   - Select npm 6.14.16: ```npm install -g npm@6.14.16```
 - Install dependencies: ```npm install```
 - Install gulp globally with `npm install -g gulp-cli`.
 - Build the project to the `./dist/` folder with `gulp build`.
 - Optionally, to rebuild on file changes, run `gulp dev`.
 - To package .zip files for distribution, run `gulp zip`, or run the full build & zip with `gulp dist`.

 Uncompressed builds can be found in `/dist`, compressed builds can be found in `/builds` once they're built.

## Contributing

You can re-generate the docs locally by running `npm run doc`, and contributors can update the hosted docs by running `npm run publish-docs`.

### Running Tests

Requires `mocha` installed. Run `npm install -g mocha`.

Then just run `npm test`.

You can also test with a continuously watching process, via `npm run watch`.

You can run the linter by itself with `gulp lint`.

## Architecture

[![Architecture Diagram](./docs/architecture.png)][1]

## Development

```bash
npm install
npm start
```

## Build for Publishing

```bash
npm run dist
```

#### Writing Browser Tests

To write tests that will be run in the browser using QUnit, add your test files to `test/integration/lib`.

## Other Docs

- [How to add custom build to Chrome](./docs/add-to-chrome.md)
- [How to add custom build to Firefox](./docs/add-to-firefox.md)
- [How to develop a live-reloading UI](./docs/ui-dev-mode.md)
- [How to develop an in-browser mocked UI](./docs/ui-mock-mode.md)
- [How to live reload on local dependency changes](./docs/developing-on-deps.md)
- [How to manage notices that appear when the app starts up](./docs/notices.md)
- [How to use the TREZOR emulator](./docs/trezor-emulator.md)
- [How to generate a visualization of this repository's development](./docs/development-visualization.md)

[1]: http://www.nomnoml.com/#view/%5B%3Cactor%3Euser%5D%0A%0A%5Bmetamask-ui%7C%0A%20%20%20%5Btools%7C%0A%20%20%20%20%20react%0A%20%20%20%20%20redux%0A%20%20%20%20%20thunk%0A%20%20%20%20%20ethUtils%0A%20%20%20%20%20jazzicon%0A%20%20%20%5D%0A%20%20%20%5Bcomponents%7C%0A%20%20%20%20%20app%0A%20%20%20%20%20account-detail%0A%20%20%20%20%20accounts%0A%20%20%20%20%20locked-screen%0A%20%20%20%20%20restore-vault%0A%20%20%20%20%20identicon%0A%20%20%20%20%20config%0A%20%20%20%20%20info%0A%20%20%20%5D%0A%20%20%20%5Breducers%7C%0A%20%20%20%20%20app%0A%20%20%20%20%20metamask%0A%20%20%20%20%20identities%0A%20%20%20%5D%0A%20%20%20%5Bactions%7C%0A%20%20%20%20%20%5BaccountManager%5D%0A%20%20%20%5D%0A%20%20%20%5Bcomponents%5D%3A-%3E%5Bactions%5D%0A%20%20%20%5Bactions%5D%3A-%3E%5Breducers%5D%0A%20%20%20%5Breducers%5D%3A-%3E%5Bcomponents%5D%0A%5D%0A%0A%5Bweb%20dapp%7C%0A%20%20%5Bui%20code%5D%0A%20%20%5Bweb3%5D%0A%20%20%5Bmetamask-inpage%5D%0A%20%20%0A%20%20%5B%3Cactor%3Eui%20developer%5D%0A%20%20%5Bui%20developer%5D-%3E%5Bui%20code%5D%0A%20%20%5Bui%20code%5D%3C-%3E%5Bweb3%5D%0A%20%20%5Bweb3%5D%3C-%3E%5Bmetamask-inpage%5D%0A%5D%0A%0A%5Bmetamask-background%7C%0A%20%20%5Bprovider-engine%5D%0A%20%20%5Bhooked%20wallet%20subprovider%5D%0A%20%20%5Bid%20store%5D%0A%20%20%0A%20%20%5Bprovider-engine%5D%3C-%3E%5Bhooked%20wallet%20subprovider%5D%0A%20%20%5Bhooked%20wallet%20subprovider%5D%3C-%3E%5Bid%20store%5D%0A%20%20%5Bconfig%20manager%7C%0A%20%20%20%20%5Brpc%20configuration%5D%0A%20%20%20%20%5Bencrypted%20keys%5D%0A%20%20%20%20%5Bwallet%20nicknames%5D%0A%20%20%5D%0A%20%20%0A%20%20%5Bprovider-engine%5D%3C-%5Bconfig%20manager%5D%0A%20%20%5Bid%20store%5D%3C-%3E%5Bconfig%20manager%5D%0A%5D%0A%0A%5Buser%5D%3C-%3E%5Bmetamask-ui%5D%0A%0A%5Buser%5D%3C%3A--%3A%3E%5Bweb%20dapp%5D%0A%0A%5Bmetamask-contentscript%7C%0A%20%20%5Bplugin%20restart%20detector%5D%0A%20%20%5Brpc%20passthrough%5D%0A%5D%0A%0A%5Brpc%20%7C%0A%20%20%5Bethereum%20blockchain%20%7C%0A%20%20%20%20%5Bcontracts%5D%0A%20%20%20%20%5Baccounts%5D%0A%20%20%5D%0A%5D%0A%0A%5Bweb%20dapp%5D%3C%3A--%3A%3E%5Bmetamask-contentscript%5D%0A%5Bmetamask-contentscript%5D%3C-%3E%5Bmetamask-background%5D%0A%5Bmetamask-background%5D%3C-%3E%5Bmetamask-ui%5D%0A%5Bmetamask-background%5D%3C-%3E%5Brpc%5D%0A



--------------------
