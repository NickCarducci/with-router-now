copied from github.com/jaredpalmer/razzle
https://github.com/jaredpalmer/razzle/tree/master/examples/with-now-v2

# Razzle Now v2 Example

## How to use

Download the example [or clone the whole project](https://github.com/jaredpalmer/razzle.git):

```bash
mkdir yourFolder
cd yourFolder
git clone https://github.com/NickCarducci/with-router-now
cd with-router-now
```

Install it and run:

```bash
yarn install
yarn start
```

Install now:

```
npm i -g now
```

Build and deploy:

```bash
yarn build
now
```

Open the link written in the console.

## Idea behind the example

Take a look at `now.json`. We are uploading the result of the razzle build, and setting up the routes for the app entry point and all static resources.

We are also setting the `NODE_ENV` environment variable. Most likely, your app will use other environment variables, beware you should not commit secrets like api keys and others into your repository. Take a look at now's documentation to understand what you should do in such cases.

## Documentation

* [Zeit Now v2 Documentation](https://zeit.co/docs/v2/)
  * [@now/node-server](https://zeit.co/docs/v2/deployments/official-builders/node-js-server-now-node-server/)
  * [Environment Variables and Secrets](https://zeit.co/docs/v2/deployments/environment-variables-and-secrets/)
  
  I replaced server.js, app.test.js, client.js and package.json at least from the with-react-router example. This seems to work, but I am using this to test from instead of recreating it during development integrating my client code
  
  It's blank because I erased the react-router Route in Switch to Home and About, idk why I did but I did and that is why it is blank white screen when it works
  
  now.json - https://github.com/jaredpalmer/razzle/issues/900#issuecomment-504701394
  
  ````
  {
  "version": 2,
  "builds": [
    {
      "src": "build/public/**/*",
      "use": "@now/static"
    },{
      "src": "build/server.js",
      "use": "@now/node-server"
    }
  ],
  "routes": [{
    "src": "/static/(.*)/(.*)/(.*)",
    "dest": "build/public/static/$1/$1/$1"
  },{
    "src": "/static/(.*)/(.*)",
    "dest": "build/public/static/$1/$1"
  },{
      "src": "/static/(.*)",
      "dest": "build/public/static/$1"
    },
    {
      "src": "/favicon.ico",
      "dest": "favicon.ico"
    },
    {
      "src": "/robots.txt",
      "dest": "robots.txt"
    },
    {
      "src": "/(.*)",
      "dest": "build/server.js"
    }
  ],
  "env": {
    "NODE_ENV": "production"
  }
  ````
  trying... https://wavv.art
  trying... https://wavvart.nickcarducci.vercel.app/
