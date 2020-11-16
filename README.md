# Practice with node

Created a new repository `https://github.com/fmuwanguzi/node-express`

Cloned it into a new folder in my labs

Input  `npm init`  and at the end of the prompts I added an `index.js`

First step was to set up myModule.js with a function

```javascript
function multiply(num1, num2){
    return num1 * num2;
}
```
Export that function

```javascript
module.exports = {
    multiply,
}
```
To use the function in index.js 
```javascipt
const { multiply } = require('./myModule')
```
Finally is tried 2 numbers 
```javascript
console.log(multiply(2 , 3))
```

To open this in my terminal I used the follwing prompt
` node index.js ` and I got the number 6

More examples have been added in my code. 

You can also import node module for example this NBA one.

In terminal `npm install nba`

then in you `index,js`

```javascript

const NBA = require("nba");
const curry = NBA.findPlayer('Stephen Curry');
console.log(curry);

```
when you `node index.js` in terminal you would get

`{
  firstName: 'Stephen',
  lastName: 'Curry',
  playerId: 201939,
  teamId: 1610612744,
  fullName: 'Stephen Curry',
  downcaseName: 'stephen curry'
}
`
It gets a lot more specific when you add this in `index.js`

```javascript
NBA.stats.playerInfo({ PlayerID: curry.playerId }).then(console.log);
```

now when you `node index.js` in your terminal you get 

`
commonPlayerInfo: [
    {
      personId: 201939,
      firstName: 'Stephen',
      lastName: 'Curry',
      displayFirstLast: 'Stephen Curry',
      displayLastCommaFirst: 'Curry, Stephen',
      displayFiLast: 'S. Curry',
      playerSlug: 'stephen-curry',
      birthdate: '1988-03-14T00:00:00',
      school: 'Davidson',
      country: 'USA',
      lastAffiliation: 'Davidson/USA',
      height: '6-3',
      weight: '185',
      seasonExp: 11,
      jersey: '30',
      position: 'Guard',
      rosterstatus: 'Inactive',
      gamesPlayedCurrentSeasonFlag: 'Y',
      teamId: 1610612744,
      teamName: 'Warriors',
      teamAbbreviation: 'GSW',
      teamCode: 'warriors',
      teamCity: 'Golden State',
      playercode: 'stephen_curry',
      fromYear: 2009,
      toYear: 2020,
      dleagueFlag: 'N',
      nbaFlag: 'Y',
      gamesPlayedFlag: 'Y',
      draftYear: '2009',
      draftRound: '1',
      draftNumber: '7'
    }
  ],
  playerHeadlineStats: [
    {
      playerId: 201939,
      playerName: 'Stephen Curry',
      timeFrame: 'career',
      pts: 23.5,
      ast: 6.6,
      reb: 4.5,
      allStarAppearances: 6
    }
  ],
  availableSeasons: [
    { seasonId: '12009' }, { seasonId: '22009' },
    { seasonId: '12010' }, { seasonId: '22010' },
    { seasonId: '12011' }, { seasonId: '22011' },
    { seasonId: '12012' }, { seasonId: '22012' },
    { seasonId: '42012' }, { seasonId: '12013' },
    { seasonId: '22013' }, { seasonId: '32013' },
    { seasonId: '42013' }, { seasonId: '12014' },
    { seasonId: '22014' }, { seasonId: '32014' },
    { seasonId: '42014' }, { seasonId: '12015' },
    { seasonId: '22015' }, { seasonId: '32015' },
    { seasonId: '42015' }, { seasonId: '12016' },
    { seasonId: '22016' }, { seasonId: '32016' },
    { seasonId: '42016' }, { seasonId: '12017' },
    { seasonId: '22017' }, { seasonId: '32017' },
    { seasonId: '42017' }, { seasonId: '12018' },
    { seasonId: '22018' }, { seasonId: '32018' },
    { seasonId: '42018' }, { seasonId: '22019' }
  ]
}
`

All of his information which leads to more information.

We can push all this information back up to git hub but before we do that we need to `touch .gitignore` in our terminal.

When then open `.gitignore` in our vscode and input `node_modules` this ensures when we push it back up it doesn't bring all the external module with it.

## Setting up express app 

Install express using your terminal `npm i express` you can use install instead of i

Import the express module for your use into your js file 
and set up your app

```javascript
const express = require('express');
const app = express();
```
## Routes

Example of a home route set app

```javascript 
app.get('/', function(req, res) {
    res.send('Here is your home route');
});

app.listen(8000);

```
If you use google chrome you can now type in 
`localhost:8000` you should see `"Here is your home route"` or home page.

You can also set up routes to otther pages for example an about(or an name you'd like to give it) page

```javascript

app.get('/about', function(req, res){
    res.send('All about me goes here');
    
});

```

To send information to your client now that you have an about route you can set up a `about.js` file.

Simple add some simple HTML

ie `<h3>I am learning about express</h3>`


## Views

Create a views folder and place your home page and about page there

You can now call each file using 

```javascript
app.get('/about', function(req, res) {
  res.sendFile(__dirname+'/views/about.html');
});

```

## Templates

Lets try using a template engine called ejs
So lets `npm install ejs`


Set it up with your app like so 

`app.set('view engine', 'ejs');`