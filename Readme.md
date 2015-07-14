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

jQuery has event handlers that respond to user actions - like clicking or moving the mouse. This allows us to make all sorts of amazing behaviors and websites that respond naturally to user actions.


##JavaScript Events
In JavaScript, events are user actions such as mouse clicks, key presses, or window resizing. We can define code that will be run when those events happen.

JavaScript allows us to bind - or connect - functions to particular events. We create a function, and then tell the browser to run that function whenever that event happens. 

jQuery lets us bind events with a concise, readable syntax. In the example below, we are writing code that will "listen" for a user's mouse click on any element with the "button" class.

```
$('.button').on('click', action);
```
* `$('.button')` - the listener - uses the selector syntax `$()` to get all elements with the class "button"
* `.on()` is the method that attaches an event handler to the selected elements
* `click` is the event we are responding to
* `action` is the event handler - or what we want our response to be


Javascript gives us a few different ways to create the 'action'

We can define a named method, like we are used to, and pass that in:
```
function tellUsWeClicked () {
	console.log("You clicked the button");
}
$('.button').on('click',tellUsWeClicked);
```



##Callback Functions

We can also define an anonymous function as the parameter. It's anonymous because we create it without giving it a name. This is a common pattern, called a callback function. 
```
$('.button').on('click', function() {
	console.log("You clicked the button");
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
  alert("You clicked a button");

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
This works, but we're repeating the lookup for the HTML element with the ID of stuff multiple times. 

Instead we can do this:
```
$("#my_element").css("color", "blue").slideDown(2000).slideUp(2000);
```
Here, we've chained the methods by simply adding the next one to the end of the chain.

##Conclusion / So What?
jQuery and other libraries allow you to do amazingly complex stuff with a simple function call. Any developer worth their salt will want to make a website that responds to the user. jQuery events let you do that.

Now it's time to explore events and event handlers! Try some of the jquery you've been learning to change elements and style when certain actions happen. [Here's a list](http://help.dottoro.com/larrqqck.php) of a ton of browser events that your code can listen for.

Some of the most common are 'click', 'scroll', 'mouseenter' and 'mouseleave', 'focus', 'blur',  and 'keyup'. There are lots and lots of events - what events do popular websites listen for and handle?
