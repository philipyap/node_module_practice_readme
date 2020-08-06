## First Step,
```
1. fork and clone the assignment.
2. npm init -y
3. touch index.js myModule.js .gitignore
```

## Next,
create favourite food array 
```
module.exports.favFood =()=> ['pizza', 'burger', 'friedrice']

module.exports.array =() => {
    for (let i = 0; i<= 2; i++)
    console.log(i)
}
```

## Then,
create index.js to add console.log(favFood) and add intersting npm we found in the class
```
const myModule = require('./myModule.js')

console.log(myModule.favFood())

var oneLinerJoke = require('one-liner-joke');

var getRandomJoke = oneLinerJoke.getRandomJoke();
console.log(getRandomJoke)
```
## After that,
npm install to package-lock-json
```
npm install one-liner-joke
## First Step,
```
1. fork and clone the assignment.
2. npm init -y
3. touch index.js myModule.js .gitignore
```

## Next,
create favourite food array 
```
module.exports.favFood =()=> ['pizza', 'burger', 'friedrice']

module.exports.array =() => {
    for (let i = 0; i<= 2; i++)
    console.log(i)
}
```

## Then,
create index.js to add console.log(favFood) and add intersting npm we found in the class
```
const myModule = require('./myModule.js')

console.log(myModule.favFood())

var oneLinerJoke = require('one-liner-joke');

var getRandomJoke = oneLinerJoke.getRandomJoke();
console.log(getRandomJoke)
```
## After that,
npm install to package-lock-json
```
npm install one-liner-joke

https://www.npmjs.com/package/one-liner-joke
```
## Finally,
```
node index.js

node_modules_practice git:(master) ✗ node index.js
[ 'pizza', 'burger', 'friedrice' ]
{
  body: "Why do women rub their eyes when they get up in the morning? They don't have balls to scratch!",
  tags: [ 'women' ]
```
```
## Finally,
```
node index.js

node_modules_practice git:(master) ✗ node index.js
[ 'pizza', 'burger', 'friedrice' ]
{
  body: "Why do women rub their eyes when they get up in the morning? They don't have balls to scratch!",
  tags: [ 'women' ]
```

# update Aug 5,2020 

## Set Up a new Express App

1. create a new Express app called 
```mkdir faves-hates-app``` 
2. initialize Node ```npm init -y```
3. set up index.js file ```touch index.js```
4. install Dependencies: 
``` npm i express``` ```npm i ejs```
5. set up ejs in ```views``` folder
6. install ejs layouts ```npm install express-ejs-layouts```
7. set up ejs layout in index.js
```
var express = require('express');
var app = express();
var ejsLayouts = require('express-ejs-layouts');

app.set('view engine', 'ejs');
app.use(ejsLayouts);

app.listen(3000)
```
8. create layouts on layout.ejs
```
<!DOCTYPE html>
<html>
<head>
  <title>Faves&Hates</title>
</head>
<body>
  <%- body %>
</body>
</html>
```
9. create```home.ejs``` in views folder
```
<h1>This is the home page!</h1>
```
10. create a home route in ```index.js```
```
app.get('/', function(req, res) {
  res.render('home');
});
```
11. set up few more views/routes:
index.js
```
app.get('/animals', function(req, res) {
  res.render('animals', {title: 'Favorite Animals', animals: ['sand crab', 'corny joke dog']})
});
```
animal.ejs
```
<h1><%= title %></h1>
<ul>
  <% animals.forEach(function(animal) { %>
    <li><%= animal %></li>
  <% }) %>
</ul>
```
12. add navigation to layout.ejs
```
<!DOCTYPE html>
<html>
<head>
  <title>Faves&Hates</title>
</head>
<body>
  <ul>
    <li><a href='/foods'>Favorite Foods</a></li>
    <li><a href='/animals'>Favorite Animals</a></li>
  </ul>
  <%- body %>
</body>
</html>
```

## Contrllers & Express 
1. Inside the views folder, create a faves folder and move your foods.ejs and animals.ejs files into it.
2. Inside the views folder, create a hates folder that also contains a foods.ejs file and an animals.ejs file, but design these views to display your least favorite foods and animals.
3. Create a controllers folder inside the root directory that will contain all routes except for the home route.
4. Inside the controllers folder, create a file called faves.js with the following routes:
```
app.get('/foods', function(req, res) {
  res.render('faves/foods', {title: 'Favorite Foods', foods: ['coconut', 'avocado']});
});

app.get('/animals', function(req, res) {
  res.render('faves/animals', {title: 'Favorite Animals', animals: ['sand crab', 'corny joke dog']})
});
```
5. Add these wrapper lines of code to faves.js, and replace app with router.
```
var express = require('express');
var router = express.Router();

router.get('/foods', function(req, res) {
  res.render('faves/foods', {title: 'Favorite Foods', foods: ['coconut', 'avocado']});
});

router.get('/animals', function(req, res) {
  res.render('faves/animals', {title: 'Favorite Animals', animals: ['sand crab', 'corny joke dog']})
});

module.exports = router;
```
6. Now back in index.js, we just need to add some middleware to get these routes working again!
index.js
```
app.use('/faves', require('./controllers/faves'));
```