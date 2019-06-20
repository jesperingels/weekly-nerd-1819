# Articles
The articles can be found in their assigned folders:
* [let and const](./let-and-const/README.md)
* [React](./react/README.md)

# CSS Animations
CSS allows us to add styling to the HTML of websites. But it can do so much more than what most people use it for. One of the remarkable things CSS can do is to animate elements on a webpage, which I will be talking about in this article.

## Basics
So what really happens when something is animated? The way we animate is usually the same throughout different programms. Like some Adobe software: After Effects and Photoshop. In After Effects you can animate an object by placing it somewhere so it has a starting position. Next thing is to add key-frames, which means that you're going to tell it where to move in a certain amount of time. The same principle of key-frames applies to CSS animations

# Why?
I don't think anyone needs a lot of convincing why you would want CSS animations, but I'll do it anyway:
Some links to examples: 
* [Fruit Shop](https://codepen.io/jonitrythall/pen/kzcnC)

# How?
So there's different ways to animate:
* **Transition.** Transition is a property that tells an element how long it takes for 'a change' to complete.
This 'change' can be many different things like: Position, size, rotation, colour etc. This is the same principle of animating that I explained previously.

HTML
```HTML
<div id="element" class="box"></div>
```
CSS
```CSS
#element {
  transition: 1s;
}
```
 Now we only need a starting position (for this example we'll use position, could be anything ofcourse.) and an ending position. This ending position is basically how you want the animation to be executed. In this example I'll use a `hover`.

 ```CSS
 .box {
   height: 50px;
   width: 50px;
   background-color: red;
 }
 #element{
   transition: 1s;
 }

 #element:hover {
   transform: translate(90px);
 }
 ```

 So what will happen is that the browser will render a red square and when the mouse hovers over the square it will move 90 pixels to the right. 

 * **@key-frame and animation**

