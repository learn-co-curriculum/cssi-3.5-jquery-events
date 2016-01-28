

# Events, Listeners, and Handlers in JQuery

### Objectives
+ Understand what constitutes an event
+ Attach jQuery event handlers (like 'click') to HTML elements
+ Add callback functions to event handlers
+ Use the $(this) selector in event handlers
+ Understand how to chain jQuery methods
+ Use the jQuery documentation as a resource

### Motivation / Why Should You Care?

jQuery has event handlers that respond to user actions - like clicking or moving the mouse. This allows us to make all sorts of amazing behaviors and websites that respond naturally to user actions.


## JavaScript Events
In JavaScript, events are user actions such as mouse clicks, key presses, or window resizing. We can define code that will be run when those events happen.

JavaScript allows us to bind - or connect - functions to particular events. We create a function, and then tell the browser to run that function whenever that event happens. 

jQuery lets us bind events with a concise, readable syntax. In the example below, lets pretend we wanted to do something everytime the user clicked on a header.

```js
$("h1").click(action);
```

* `$("h1")` - the *listener* - uses the selector syntax `$()` to get all the `<h1>` elements
* `click` - the *event* we are responding to
* `action` - the *handler* - or what we want our response to be

Javascript gives us a few different ways to create the 'action', by using a named method or using a callback function.

#### Named Methods as Event Handlers

We can define a named method. Then we can pass that method as a parameter when we call the event:

```js
function tellUsWeClicked () {
    alert("You clicked a header");
}

$("h1").click(tellUsWeClicked);
```    


#### Callback Functions as Event Handlers

We can also use an anonymous function: `function(){}` as the parameter. It's anonymous because we create it without giving it a name. The code for the function will go inbetween the curly brackets. This is a common pattern, called a callback function.

```js
$("h1").click(function(){
    alert("You clicked a header");
});
```
Especially if that function is not going to be used anywhere else, this style of coding makes it easy to read off exactly what will happen when the click event is triggered.

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

```js
$( document ).ready(function() {
  // Here are all the functions that
  // will be run when the document is ready.
});
```

##$(this) inside Event callbacks
 $(this) allows you to easily access the element that fired the event.
For Example:

```js
$("h1").click(function(){
    alert("You clicked a header");
    $(this).fadeOut();
});
```

Here, the $(this) refers to the header that was just clicked.  After the user click on the header, an alert will pop up and then that header will fade out.

##Chaining Methods
Up until this point we've been writing jQuery statements one at a time. However, there's a convenient way to do multiple things to an element without writing so much code - you can chain multiple commands together.

For example, if we wanted an element to turn blue, and then move up and down we could write it this way:

```js
$(this).css("color", "blue");
$(this).slideUp(2000);
$(this).slideDown(2000);
```

This works, but we're repeating the lookup for the HTML element with the ID of stuff multiple times. 

Instead we can do this:

```js
$(this).css("color", "blue").slideUp(2000).slideDown(2000);
```

Here, we've chained the methods by simply adding the next one to the end of the chain.

##Conclusion / So What?
jQuery and other libraries allow you to do amazingly complex stuff with a simple function call. Any developer worth their salt will want to make a website that responds to the user. jQuery events let you do that.

Now it's time to explore events and event handlers! Try some of the jquery you've been learning to change elements and style when certain actions happen. [Here's a list](http://help.dottoro.com/larrqqck.php) of a ton of browser events that your code can listen for.

Some of the most common are 'click', 'scroll', 'mouseenter' and 'mouseleave', 'focus', 'blur',  and 'keyup'. There are lots and lots of events - what events do popular websites listen for and handle?

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/cssi-3.5-jquery-events' title='Events, Listeners, and Handlers in JQuery'>Events, Listeners, and Handlers in JQuery</a> on Learn.co and start learning to code for free.</p>
