# Let and const
Let and const are two different types of variables. Since [ES6](http://es6-features.org/#Constants) we no longer user `var` to define a variable but `let` and `const`.

## const
`const` is used to declare a variable which has a 'constant' value. This means that the value of a const variable can not be changed ones it's declared. **Usecase:**

HTML: 
```HTML
<div id='greeting'>Hello world!</div>
```
Javascript:
```Javascript
const greeting = document.getElementById('greeting');

greeting.style.color = 'red';
```

The value of the `const` variable: greeting is an HTML element, so it's logical that you can't reassign this variable. When doing some DOM manipulation in Javascript I've found that I use `const` most often. 

## let
`let` is used to declare a variable which has a value that can be reassigned. Like so:
```Javascript
let x = 1;
console.log(x); // output = 1

x = 2;
console.log(x); // output = 2

```

## Scope
Maybe the most important thing of `let` and `const` is that they are block-scoped. This means that when you define a let variable and then redefine it inside for example an if statement, both variables have a different scope. 
Example([MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)):
```Javascript
let x = 1;

if (x === 1) {
  let x = 2;

  console.log(x);
  // expected output: 2
}

console.log(x);
// expected output: 1
```
The same goes for `const` 

## var?
So what's the big difference with `var`? First of all, var says nothing about the variable itself. It's just an empty box where you can put a value in. With `const` you know it is a constant value and with `let` you know it is reassignable. 

Scoping with `var` is less strict than `const` and `let`, since const and let are block-scoped and var is function scoped. Example:
Because de variable is scoped by the function, the `console.log()` does'nt have acces to it. 
```Javascript
function changeValue() {
  var x = 1
}
console.log(x); // output x = undefined
```
Here variable x is declared in a block, but because it's a `var` it isn't scoped by the block and the console will log it. 
```Javascript
var y = true;

if(y) {
  var x = 2
}

console.log(x) // output x = 2
```
