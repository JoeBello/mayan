# mayan

A port of [maya](https://github.com/ZengineHQ/maya) in NodeJS

[![CircleCI](https://circleci.com/gh/ZengineHQ/mayan.svg?style=svg)](https://circleci.com/gh/ZengineHQ/mayan)

## Install

```
npm install -g @zenginehq/mayan
```

## Using

```
$ mayan

mayan <command>

Commands:
  mayan build [plugin]    Build plugin
  mayan deploy [plugin]   Deploy plugin
  mayan watch [plugin]   Watch plugin(s) and deploy on changes
  mayan publish [plugin]  Publish plugin
  mayan register [plugin]  Register plugin in API
  mayan init [plugin]  Initialize plugin locally

Options:
  --env          Environment name
  --verbose      Display verbose debug output                          [boolean]
  --help         Show help                                             [boolean]
  --show-hidden  Show advanced options                                 [boolean]

For more information, RTFM at https://github.com/ZengineHQ/mayan

```

## Differences from maya

Whereas mayan strives to be as backwards compatible with original maya as possible, there is one breaking change:

- backend service `maya-build` scripts no longer work and have been replaced with 2 new pre/post build scripts

*New Features*

- Write frontend plugins using ES6 features such as arrow functions, let/const, destructuring, rest/spread, etc
- Write frontend plugin styles using SCSS
- You can also keep on using vanilla js and css if that's your thing
- Support for frontend plugin modules directly in the main plugin package.json as regular dependencies (the old `src` dir approach also works)
- Follows symlinks for @zenginehq modules for a great local development experience
- Ability to `--skip-build` when deploying and publishing and `--skip-deploy` when publishing
- Minifies CSS, JS and HTML when `prod` or `production` environment used
- Supports `maya-pre-build` and `maya-post-build` package.json scripts for both backend services and frontend plugins
- The maya build artifact location and folder structure has changed
- `mayan watch [plugin]` will watch your frontend plugin directories and deploy on changes for faster development process (recommended: use `--frontend` flag). Takes all the same commands as `deploy`.
- *coming soon* `register` command to create/update plugins using the Zengine API and maintain your maya.json ids updated
- *coming soon* `init` command to initialize a local dev environment either from a fresh git clone (registers plugin if necessary) or from scratch (programatically invokes yeoman generator and then registers and publishes plugin)


## Contributing


### Fork

```
git clone git@github.com:ZengineHQ/mayan.git
```

### Install dependencies

```
npm install
```

### Test and lint

```
npm test
npm run eslint
```

### Install binary locally

```
npm link
```

### Adding new commands

Follow this [approach/strategy](https://github.com/yargs/yargs/blob/master/docs/advanced.md#example-command-hierarchy-using-commanddir) to organize commands
