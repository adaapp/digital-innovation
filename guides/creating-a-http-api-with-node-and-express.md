# Creating a HTTP API with Node & Express

## Step 1: Create a Node.JS project

If you haven't already got a project started, try following this guide to get going:

{% page-ref page="starting-a-new-node.js-project.md" %}

## Step 2: Install dependencies

There are several npm packages we need to build our API:

* [Express](http://expressjs.com/) - a minimal framework for building HTTP apps
* [Morgan](https://github.com/expressjs/morgan]) - a logger for Express, so we can see what requests get made and how they are handled
* [Body Parser](https://github.com/expressjs/body-parser) - turns JSON or form data that people send to our API into JavaScript objects we can work with

Install them with npm:

```bash
npm install express morgan body-parser
```

## Step 3: Create a server.js file

Create a new file in your Node project called `server.js`. Add a `console.log` and run it with `node server.js` to check it's all working.

Then, we need to `require` our dependencies, set up our Express app with Morgan and Body Parser, and start the server listening.

{% code-tabs %}
{% code-tabs-item title="server.js" %}
```javascript
var express = require('express')
var morgan = require('morgan')
var bodyParser = require('body-parser')

// the port to listen on. choose whatever you want!
var port = 3000

// create a new express app:
var app = express()

// set up logging on our app:
app.use(morgan('dev'))

// turn JSON in requests to something we can work with:
app.use(bodyParser.json())

// turn forms in requests to something we can work with:
app.use(bodyParser.urlencoded({ extended: true }))

// start the app!
app.listen(port, function() {
  console.log('Server listening on http://localhost:' + port)
})
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Start the server with `node server.js`. Try opening the URL in your browser and making some requests. You should see logs printed in your terminal like this:

```text
Server listening on http://localhost:3000
GET / 404 3.627 ms - 139
GET /favicon.ico 404 0.656 ms - 150
```

## Step 4: Start creating routes

Create routes using `app.get`, `app.post`, etc. depending on what you want them to do. Use `res.json()` to send JSON responses. Add your routes **after** your `app.use` bits, but before `app.listen`.

### Simple requests

{% code-tabs %}
{% code-tabs-item title="server.js" %}
```javascript
app.get('/', function(req, res) {
  res.json({
    someData: 'hello, world!'
  })
})
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="server.js" %}
```javascript
app.post('/some-url', function(req, res) {
  var bodyContents = req.body.somethingFromBody
  console.log(bodyContents)
  
  res.status(401)
  res.json({
    error: 'forbidden!!!'
  })
})
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### URL parameters

{% code-tabs %}
{% code-tabs-item title="server.js" %}
```javascript
app.get('/words/:id', function(req, res) {
  var id = req.params.id
  res.json({
    idFromUrl: id,
  })
})
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Complete example

{% code-tabs %}
{% code-tabs-item title="server.js" %}
```javascript
var words = ['hello', 'world']

// get list of words
app.get('/words', function(req, res) {
  res.json({
    words: words,
  })
})

// add a new word
app.post('/words', function(req, res) {
  var wordToAdd = req.body.word
  words.push(wordToAdd)
  res.json({
    addedWord: wordToAdd
  })
})

// get a specific word
app.get('/words/:id', function(req, res) {
  var wordIndex = req.params.id
  var word = words[wordIndex]
  res.json({
    word: word
  })
})
```
{% endcode-tabs-item %}
{% endcode-tabs %}

