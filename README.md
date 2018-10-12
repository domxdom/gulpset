# gulpset

[![Greenkeeper badge](https://badges.greenkeeper.io/fourdigit/gulpset.svg)](https://greenkeeper.io/)

Gulp based project skeleton with modular tasks.

## tech stack

- gulp (task-runner)
- Webpack + babel + eslint (JS)
- Scss + PostCSS + sasslint (CSS)
- ejs (HTML)
- prettier (beatutifier)
- browser-sync (dev server)
- rsync (deploy)

## want to develop

1. download this repo
2. `yarn`
3. `yarn start`

## want to generate production build(minified)

1. `yarn build:prod`

## each tasks

### js settings

- see `/webpack.config.js`, `/webpack.config.prod.js` & `/gulpset/tasks/scripts/index.js`

#### When you use ES5

1. `/.eslintrc`: modify `@fourdigit/eslint-config-fourdigit/esnext` => `@fourdigit/eslint-config-fourdigit/base`
2. modify `copy` task (add `js` ext)
3. remove `scripts` task from `gulpfile.js`

### scss settings

- see `/gulpset/tasks/scss/index.js`
- some utility scss libs are loaded on `/src/assets/css/app.scss`

### ejs settings

- see `/gulpset/tasks/ejs/index.js`
- some utility functions are included here `/src/_utils.ejs`

### deployrsync settings

1. Open `/gulpset/tasks/deployrsync/index.js`
2. Set target user:hostname to `gulpset.confs.deployrsync.options.hostname`
3. Add private key of target server. e.g. `ssh-add ~/.ssh/xxxxxxxx_rsa`
4. Run `gulp deployrsync`

#### Deploy via bitbucket-pipelines

1. Create private key for target server.
2. Encode it into base 64. e.g `$ base64 gulpset_rsa| pbcopy`
3. On bitbucket web screen, enter repository settings
4. Go Pipelines settings > Enable Pipelines
5. Environment variables > make and set `PRIVATE_KEY` (make sure the to enable checkbox of "encrypt") and `TARGET_HOST`
6. Built files by newly pushed `develop` branch will be deployed to `TARGET_HOST`
7. if you want to use other branches, rewrite `branches` section on `bitbucket-pipelines.yml`
