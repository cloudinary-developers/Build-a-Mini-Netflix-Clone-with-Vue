# Deploy to Heroku

Time to show the world what you have have built! To execute this, you can push the project to Heroku in order to showcase a live demo. Once complete you can share your demo with the world.

## Create a Heroku App

Initialize git on your project:

```bash
git init
```

Create a [Heroku account](https://heroku.com/) and install the [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli#download-and-install) tool. Then run the following command on the root of your:

```bash
heroku create <YOUR-PROJECT-NAME-HERE>
```

## Ignoring Dependencies

Heroku will attempt to install needless dependencies in your current project. Run this Heroku command and they will not be installed:

```bash
heroku config:set NODE_ENV=production --app <YOUR-PROJECT-NAME-HERE>
```

## Static Files Server

We need a server that Heroku would run to serve our static app. Install express and serve-static:

```bash
npm install express serve-static
```

Next, create a `server.js` file at the root of your project and add the following:

```javascript
var express = require('express');
var path = require('path');
var serveStatic = require('serve-static');

app = express();
app.use(serveStatic(__dirname + '/dist'));

var port = process.env.PORT || 5000;
app.listen(port, () => console.log('server started ' + port););
```

The code serves a `dist` folder in our project. This folder does not exist unless we run the following command to build:

```text
npm run build
```

The command generates a build version of our app and puts the build in the `dist` folder.

You can test the build by running:

```bash
node server.js
```

> Remove `dist/` from `.gitnore` in the project root. This makes sure the Heroku does not ignore the directory since Heroku works with Git.

## Configure Start Script

Heroku by default, would want to run the `start` script in your `package.json`. Let's set that up:

```javascript
"scripts": {
    "serve": "vue-cli-service serve --open",
    "build": "vue-cli-service build",
    "lint": "vue-cli-service lint",
    "start": "node server.js"
  },
```

## Deploy

To deploy, first commit your changes to Git:

```bash
git add . && git commit -a -m "Deploy"
```

The run the following command to push to Heroku:

```bash
git push heroku master
```

After the deploy process, run the command below to open the app:

```bash
heroku open
```

