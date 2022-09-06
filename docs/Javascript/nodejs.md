# Node.js

## Links

[express.js middlewares](https://expressjs.com/en/resources/middleware/body-parser.html)
https://www.geeksforgeeks.org/best-way-to-learn-node-js-a-complete-roadmap/
https://nodejs.dev/learn/get-http-request-body-data-using-nodejs

## The Best Boilerplates

<https://github.com/hagopj13/node-express-boilerplate/>
<https://github.com/danielfsousa/express-rest-boilerplate/>

## Packages

`body-parser`: You will use this dependency to convert the body of incoming requests into JavaScript objects.
`cors`: You will use this dependency to configure Express to add headers stating that your API accepts requests coming from other origins. This is known as Cross-Origin Resource Sharing (CORS).
`express`: This is the Express library itself.
`helmet`: This library helps to secure Express APIs by defining various HTTP headers.
`morgan`: This library adds some logging capabilities to your Express API.
`mongodb-memory-server`: Spins up a MongoDB instance programmatically for testing or mocking during development. It holds the data in memory.ser
`express-validator`
`jsonwebtoken`
`connect-mongo`
`bcrypt`
`morgan`
`node-cron`

## Web Scraper

https://www.section.io/engineering-education/build-a-web-scraper-using-cheerio/
https://www.amazon.pl/robots.txt

## RealWorld Applications

[GitHub - gothinkster/realworld: "The mother of all demo apps" — Exemplary fullstack Medium.com clone powered by React, Angular, Node, Django, and many more 🏅](https://github.com/gothinkster/realworld#backends)

### Express

[GitHub - gothinkster/node-express-realworld-example-app](https://github.com/gothinkster/node-express-realworld-example-app)

### Nest js

[GitHub - lujakob/nestjs-realworld-example-app: Exemplary real world backend API built with NestJS + TypeORM / Prisma](https://github.com/lujakob/nestjs-realworld-example-app)

[GitHub - Vivify-Ideas/nestjs-boilerplate: NestJS Boilerplate 😻(Authentication, TypeORM, Configuration, Swagger)](https://github.com/Vivify-Ideas/nestjs-boilerplate)

## Security

[Learn JWT Authentication step by step with Node.js with Vanilla JavaScript client – Teach YourSelf Coding](https://teachyourselfcoding.com/articles/learn-jwt-authentication-step-by-step-with-node-js-with-vanilla-javascript-client/)

## How to create executable node.js file

Add to the top of file:

```js
#!/usr/bin/env node
```

## How to read file content?

```js
const fs = require('fs-extra');

const fileContent = await fs.readFile('../usage-instruction.txt', 'utf8');
```

## How to server static files

It's very simple on express.js and you need to declare express.static method and create folder called `public`:

```js
app.use(express.static('public'));
```

<https://expressjs.com/en/starter/static-files.html>

Now you can use in html files for example `<link rel="stylesheet" href="style.css">`.

## How to execute bash command

https://github.com/davidtheclark/locate-chrome/blob/master/index.js

```js
var fs = require('fs');
var exec = require('child_process').exec;
var Promise = require('es6-promise').Promise;

exec(mdFindCmd, function(err, stdout) {
    if (err || !stdout) next();
    else finisher(stdout.trim() + toExec);
})

function tryLocation(p, success, next) {
  fs.exists(p, function(exists) {
    if (exists) success(p);
    else next();
  });
}
```

## Cookies

Example of save and clear cookie:

```js
const express = require('express');
const cookieParser = require('cookie-parser');

const server = express();

server.use(cookieParser());
server.use(express.json());

server.get('/', (req, res) => {
    res.send({
        status: JSON.stringify(req.cookies)
    });
})

server.get('/setCookie', (req, res) => {
    res.cookie("foo", "bar");
    res.send({
        status: 'set'
    });
})

server.get('/clearCookie', (req, res) => {
    res.clearCookie("foo");
    res.send({
        status: 'clear'
    });
})

server.on('error', (err) => {
    console.error(err);
});

server.listen(1234, () => console.log(`This app is listening on port ${1234}`));
```

### How to set up new cookie

```js
app.get('/', (req, res) => {
    res.cookie('foo', 'bar');
})
```

### How to read cookie/cookies from request

```js
app.get('/', (req, res) => {
    console.log(req.headers.cookie);
})
```

Or if you want easier manage cookies and store them is js object install package `cookie-parser` using special middleware and parse it to `cookie` object

```js
const cookieParser = require('cookie-parser');
app.use(cookieParser());
app.get('/', (req, res) => {
    console.log(req.headers.cookie);
})
```

## If you have issues with parsing json from request add middleware `express.json()`

```js
app.use(express.json());
```

## Parse incoming body from requests

Use `body-parser` which extracts the entire body portion of an incoming request stream and exposes it on req.body.

```js
const express = require('express');
const bodyParser = require('body-parser');

const server = express();

server.use(bodyParser.json());

server.post('/', (req, res) => {
    console.log(req.body);
    res.send(req.body);
});

server.listen(3001);

## How to add cors to express server and filter servers IPs / Proxy requests

https://localcoder.org/cors-error-google-oauth-from-react-to-express-passportjs-validation

https://create-react-app.dev/docs/proxying-api-requests-in-development/

```js
// IP's allowed all access this server
let whitelist = ['http://localhost:3000', 'http://127.0.0.1:3000'];

let corsOptions = {
  origin: function (origin, callback) {
    if (whitelist.indexOf(origin) !== -1) {
      callback(null, true);
    } else {
      callback(new Error('Not allowed by CORS'));
    }
  }
};

// Cross-Origin Resource Sharing
app.use(cors(corsOptions));
```

## How to upgrade node

<https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-16-04>

1 option:

```sh
cd ~
curl -sL https://deb.nodesource.com/setup_16.x -o nodesource_setup.sh
sudo bash nodesource_setup.sh
sudo apt-get install nodejs
node -v
```
