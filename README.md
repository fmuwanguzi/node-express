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