---
tags: cssi, javascript, jquery
level: 2
languages: javascript
---
# Events, Listeners, and Handlers in JQuery
###Objectives
+ Understand what constitutes an event
+ Attach jQuery event handlers (like 'click') to HTML elements
+ Add callback functions to event handlers
+ Use the $(this) selector in event handlers
+ Understand how to chain jQuery methods
+ Use the jQuery documentation as a resource

###Motivation / Why Should You Care?
What happens when you click a button on site? Can we make code that responds to user actions? What if we want something to turn blue when your mouse moves over it?

jQuery has event handlers that respond to user actions. This allows us to make all sorts of amazing behaviors and websites that respond naturally to user actions.

We've talked about dynamic web pages, where the user can interact with the page, but so far, all of the changes happen when the code is executed, not when a user does something. So, how do we tie the changes we want to make to some user action?

##What are Events
In javascript, Events are user actions such as mouse clicks, key presses, or window resizing. We can define code that will be run when those events happen.

Javascript allows us to bind functions to particular events. We create a function, and then tell the browser to run that function whenever that event happens. This is awesome - otherwise, we wouldn't have websites where things happen when a user does something!

jQuery lets us bind events with a concise, readable syntax:

```
$('.button').on('click', action);
```

In pure javascript, we'd have to use
```
document.querySelectorAll('.button').addEventListener("click", action, false);
```
But, what's that `action`?

We pass a function as a parameter. The function we pass in is then 'attached' to that event listener - we call it an event handler.

Often in javascript, we don't want code executed right away - we want to define something, then run the code when something happens to trigger it. This asynchronous style, with events and listeners and handlers, is called event-driven programming, and javascript is great for it.

Javascript gives us a few different ways to pass the function into the binding method. We can define a named method, like we are used to, and pass that in:
```
function tellUsWeClicked () {
	console.log("You clicked the button");
}
$('.button').on('click',tellUsWeClicked);
```
We can also define an anonymous function as the parameter. It's anonymous because we create it without giving it a name. This is a common pattern you'll see when you look at lots of javascript code:
```
$('.button').on('click', function() {
	console.log("You clicked the button");
});
```
Especially if that function is not going to be used anywhere else, this style of coding makes it easy to read off exactly what will happen when the click event is triggered.

##jQuery Click Handler
One very popular event handler is the click() handler. The code defined in this handler will be run anytime the HTML element that we are listening to is clicked.
Suppose we have HTML that looks like this
```
<html>
  <head>...</head>
  <body>
    <button class="the-button">Push the Button</button>
  </body>
</html>
```
We could attach a click handler to the element with jQuery so that code is run anytime the button is clicked.
```
$(".the-button").click(function()
{
  alert("House Music!! Boots, and Cats, and Boots, and Cats");
});
```
Because we have created a jQuery event handler and attached it to the HTML element with the class the-button, when we click on the button, an alert will pop up that says

>"House Music!! Boots, and Cats, and Boots, and Cats"

##What is a Callback function
A callback function is the function (aka: the code) that is run when an event handler is triggered. In the previous example.click() takes an entire function as its input. If you count the parenthesis you'll see that this function on it's own looks like this:
```
function(){
  alert("House Music!! Boots, and Cats, and Boots, and Cats");
}
```
Let's say we wanted to just have our .click() alert "Hello World". The function to do that looks like this:
```
function(){
  alert("Hello World");
}
```
So the click handler just takes that exact function in between its (), like so:
```
$(".the-button").click(function(){alert("Hello World");});
```
Be Careful!! The (), {}, and ; can look confusing, but if you count where they open and close, you can see which matches with which.
This is called an anonymous function, and is our callback function. It has no name and will only be run when the event handler is triggered. JS/jQuery allows you to also pass in a named function. Our code in this case could look like this:
```
// Define the function
function houseMusic()
{
  alert("House Music!! Boots, and Cats, and Boots, and Cats");
}

// Pass the function to the event handler
$(".the-button").click(houseMusic);
```
A trick to notice here is that when we pass in the function houseMusic we DO NOT include the parenthesis (), because we are not calling the function at this point. We are only telling the event handler where to find it.

##Other Event handlers
jQuery can respond to a wide variety of Events which you should read about in the documentation. Some popular ones are:
+ Mouse clicks
+ Page load finishing
+ Moving the mouse over an element (often used for menu highlights)
+ Submitting an HTML form
+ Pressing the keyboard buttons
+ And MORE!!

##Document Ready as an Event
We often only want to run our javascript when the page has finished loading. Just like we can bind functions to events triggered by the user, we can run certain functions when the document is ready.
```
$( document ).ready(function() {
  // Here are all the functions that
  // will be run when the document is ready.
});
```
##$(this) inside Event callbacks
If you want to do something to the element that fired an event (fade out the button you just clicked, for instance) $(this) allows you to easily access the element that fired the event.
For Example:
```
$(".the-button").click(function()
{
  alert("House Music!! Boots, and Cats, and Boots, and Cats");

  // I don't think they can handle more House Music
  // Let's fade out the element they clicked on.

  $(this).fadeOut();
});
```
Here the $(this) refers to the button that we selected with the jQuery selector `$(".the-button"), since we are inside of its event handler.

##Chaining Methods
Up until this point we've been writing jQuery statements one at a time. However, there's a convenient way to do multiple things to an element without writing so much code - you can chain multiple commands together.

For example, if we wanted an element to turn blue, and then move down and up we could write it this way:
```
$("#my_element").css("color", "blue");
$("#my_element").slideDown(2000);
$("#my_element").slideUp(2000);
```
This works, but we're repeating the lookup for the HTML element with the ID of stuff multiple times. This is not only harder to write but is also computationally expensive (it takes jQuery time to look it up each time). Instead we can do this:
```
$("#my_element").css("color", "blue").slideDown(2000).slideUp(2000);
```
Here, we've chained the methods by simply adding the next one to the end of the chain.

##Conclusion / So What?
jQuery and other libraries allow you to do amazingly complex stuff with a simple function call. Any developer worth their salt will want to make a website that responds to the user. jQuery events let you do that.

Now it's time to explore events and event handlers! Try some of the jquery you've been learning to change elements and style when certain actions happen. [Here's a list](http://help.dottoro.com/larrqqck.php) of a ton of browser events that your code can listen for.

Some of the most common are 'click', 'scroll', 'mouseenter' and 'mouseleave', 'focus', 'blur',  and 'keyup'. There are lots and lots of events - what events do popular websites listen for and handle?
