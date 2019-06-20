# Articles
* [Let and const](#let-and-const)
* [React](#React)

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

# React
## Why?
For the 'meesterproef' (final project of the minor), I'm working on a [project](https://github.com/Maikxx/360-wallscope) for [wallscope](https://wallscope.co.uk/) with three fellow students.
In this project we decided to work with the framework: 'React'.
Personnally I had never worked with React before, I knew it existed but had never touched it before this project. 

This will be an article about my view on react which is based on three weeks working with React. So I don't have a lot of experience with it. 

## Basics
React is a component based framework, which means that the entire app is put together by many different parts. Each part/component is made by one of the developers. 

### Pros
* The big advantage of React is that it's **easy to work** on the same project **as a team** in a structured way. We have a [github project](https://github.com/Maikxx/360-wallscope/projects/1), where each task is put on the board. Anyone can pick a card and start working on it. Mostly you'll make a new component and create a new feature branch for it in git. 
* **Less merge conflicts.** So if we use this workflow correctly, the amount of merge conflicts should be brought to a minimum. Because everyone creates their own branch for a component, once it's finished you push it and create a pull request. So we're never working in each other's code. 
* **Recycling components.** When you have to make a form but someone else made a basic form, you can simply reuse it. The best example of this with our own project is with buttons. Since there's mostly only a couple different types of buttons in a design. You only have to make each button once and then just import it into all components that needs a button. 

### Cons
* The big con for me was that it is quite hard to learn in three weeks, this is mainly due to the **'component mindset'.** With every component you have to really think through why you're making it and how others will reuse it in their own components. There's also bigger and smaller components, the smaller components will always work their way up. Which means that bigger components import smaller components and so on until you import the biggest components into the app itself. 
* **HTML in Javascript?!** This was very confusing to me, combined with the component mindset I didn't quite understand where my html was going to end up. Also the syntax for (JSX) HTML in Javascript is a little different, but nothing to big to handle. 

## States 
One of the big concepts in React is States. It is used to keep track of the changes in the component. Mostly it is used when you want something rendered if the state equals a certain value. Simple use case: the date is stored in state and later used to show the date. I see them as global variables which you can use throughout the component. 
```Javascript
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
```

## Properties 
Another big pillar of React is the concept of properties. They are one of the most important things for a component. Since most components are very generic and need some content, classes etc. to bring them to life. Example: This is inside the component itself. 
```Javascript
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```
Here the component is called and content is passed into the component by making use of the property 'name'
```Javascript
function App() {
  return (
    <div>
      <Welcome name="Sara" ></Welcome>
    </div>
  );
}

ReactDOM.render(
  <App />,
  document.getElementById('root')
);
```