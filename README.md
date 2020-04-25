# Magic Authentication For Passport JS

[![<MagicHQ>](https://circleci.com/gh/MagicHQ/passport-magic.svg?style=shield)](https://circleci.com/gh/MagicHQ/passport-magic)
[![Known Vulnerabilities](https://snyk.io/test/github/MagicHQ/passport-magic/badge.svg?targetFile=package.json)](https://snyk.io/test/github/MagicHQ/passport-magic?targetFile=package.json)

> Integrate [Magic](https://magic.link) passwordless authentication with your Passport.js application.

<p align="center">
  <a href="./LICENSE">License</a> ·
  <a href="./CHANGELOG.md">Changelog</a> ·
  <a href="./CONTRIBUTING.md">Contributing Guide</a>
</p>

## 📖 Documentation

See the [developer documentation](https://docs.magic.link/tutorials/full-stack-node-js) to learn how you can integrate Magic into your Passport.js application in a matter of minutes.

## 🔗 Installation

Integrating your Passport.js application with Magic will require our server-side NPM package:

```bash
# Via NPM:
npm install --save passport-magic

# Via Yarn:
yarn add passport-magic
```

## ⚡️ Quick Start

```ts
const passport = require("passport");
const MagicStrategy = require("passport-magic").Strategy;

const strategy = new MagicStrategy(async function(user, done) {
  const userMetadata = await magic.users.getMetadataByIssuer(user.issuer);
  const existingUser = await users.findOne({ issuer: user.issuer });
  if (!existingUser) {
    /* Create new user if doesn't exist */
    return signup(user, userMetadata, done);
  } else {
    /* Login user if otherwise */
    return login(user, done);
  }
});

passport.use(strategy);
```
