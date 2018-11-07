# Starting a new Node.js project

## Step 1: Create & clone a repo

* On GitHub, click the small plus icon in the top-right of the screen - next to your profile image.
* Enter a name for the project and if you like, a description.
* Initialise the project with a README and chose 'Node' from the 'Add .gitignore' dropdown - that will mean `node_modules` gets ignored automatically.
* Press create repository. You'll be taken to your new repo's page.
* Clone the repo to your projects folder and `cd` into it. If you `ls -a`,  you should see your .gitignore and README files have been created for you.

## Step 2: Set up npm

* Make sure you're in your project folder. You could run `pwd` to check.
* Run `npm init` to create a `package.json`
* It'll ask you a series of questions. For most, you can accept the default suggested value \(in `()` parenthesis\) by just pressing enter. To change a value from the default, type it in and press enter.
* Entry point is the main file in your project. It usually makes sense to leave it as something like `index.js`
* For test command, if you're planning on using mocha + chai, enter 'mocha'
* If you like, you can enter your name for author
* At the end, it'll show you your new package.json file. Make sure it all looks correct, then press enter to accept.
* Use git to add, commit, and push your changes.

## Step 3: Install dependencies

* We can use `npm` to install some of our projects dependencies
* If you're using [Mocha](https://mochajs.org/) and [Chai](https://www.chaijs.com/), try `npm install mocha chai`
* For making HTTP requests, [SuperAgent](https://visionmedia.github.io/superagent/) is a good option: `npm install superagent`
* For testing HTTP APIs using Mocha, try [SuperTest](https://github.com/visionmedia/supertest): `npm install supertest`
* For making HTTP APIs or web services, [Express](https://expressjs.com/) is considered the standard: `npm install express`

## Step 4: Check everything's working

* Add an `index.js` containing just a `console.log` and check it runs
* Add a sample test file like `test/test.js` and run `npm test` to check mocha is set up correctly:

{% code-tabs %}
{% code-tabs-item title="test/test.js" %}
```javascript
var chai = require('chai')
var expect = chai.expect

// delete this when you're ready to start writing actual tests
it('works', function() {
  expect(2 + 2).to.equal(4)
})
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Step 5: Start coding!

Good luck ✨

