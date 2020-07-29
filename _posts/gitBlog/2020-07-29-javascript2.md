---
title:  "JavaScript 정리2"
excerpt: "2020웹서비스 개발 캠프 Day8"
toc: true
toc_sticky: true

categories:
  - gitBlog
tags:
  - GitHub
  - Blog
  - categories
  - JavaScript
  - Bom
last_modified_at: 2020-07-29
---


참조 사이트 [w3schools.com](hhttps://www.w3schools.com/js/js_window.asp)






## The Browser Object Model (BOM)

The `window` object is supported by all browsers. It represents the browser's window.

All global JavaScript objects, functions, and variables automatically become members of the window object.

Global variables are properties of the window object.

Global functions are methods of the window object.

Even the document object (of the HTML DOM) is a property of the window object:

`window.document.getElementById("header");`
is the same as:

`document.getElementById("header");`




- window size

Both properties return the sizes in pixels:

`window.innerHeight` - the inner height of the browser window (in pixels)
`window.innerWidth` - the inner width of the browser window (in pixels)





For Internet Explorer 8, 7, 6, 5:

`document.documentElement.clientHeight`
`document.documentElement.clientWidth`

or

`document.body.clientHeight`
`document.body.clientWidth`





## Window Location

The  `window.location` object can be written without the window prefix.

Some examples:

`window.location.href` returns the href (URL) of the current page
`window.location.hostname` returns the domain name of the web host
`window.location.pathname` returns the path and filename of the current page
`window.location.protocol` returns the web protocol used (http: or https:)
`window.location.assign()` loads a new document





## Window History

The `window.history` object can be written without the window prefix.

To protect the privacy of the users, there are limitations to how JavaScript can access this object.

Some methods:

`history.back()` - same as clicking back in the browser
`history.forward()` - same as clicking forward in the browser





## Window Navigator

The `window.navigator` object can be written without the window prefix.

Some examples:

`navigator.appName`
`navigator.appCodeName`
`navigator.platform`





## Popup Boxes


- alert box

An alert box is often used if you want to make sure information comes through to the user.

When an alert box pops up, the user will have to click "OK" to proceed.


Syntax
`window.alert("sometext");`


The `window.alert()` method can be written without the window prefix.




- confirm Boxes

A confirm box is often used if you want the user to verify or accept something.

When a confirm box pops up, the user will have to click either "OK" or "Cancel" to proceed.

If the user clicks "OK", the box returns **true**. If the user clicks "Cancel", the box returns **false**


Syntax
`window.confirm("sometext");`


The `window.confirm()` method can be written without the window prefix.





- prompt Box

A prompt box is often used if you want the user to input a value before entering a page.

When a prompt box pops up, the user will have to click either "OK" or "Cancel" to proceed after entering an input value.

If the user clicks "OK" the box returns the input value. If the user clicks "Cancel" the box returns null.


Syntax

`window.prompt("sometext","defaultText");`


The `window.prompt()` method can be written without the window prefix.







## Timing Events

The `window` object allows execution of code at specified time intervals.

These time intervals are called timing events.


The two key methods to use with JavaScript are:


`setTimeout(function, milliseconds)`
Executes a function, after waiting a specified number of milliseconds.

`setInterval(function, milliseconds)`
Same as setTimeout(), but repeats the execution of the function continuously.





- The setTimeout() Method

`window.setTimeout(function, milliseconds);`


The `window.setTimeout()` method can be written without the window prefix.


The first parameter is a function to be executed.

The second parameter indicates the number of milliseconds before execution.




- How to Stop the Execution?

The `clearTimeout()` method stops the execution of the function specified in setTimeout().

`window.clearTimeout(timeoutVariable)`
The `window.clearTimeout()` method can be written without the window prefix.

The `clearTimeout()` method uses the variable returned from `setTimeout():`

`myVar = setTimeout(function, milliseconds);
clearTimeout(myVar);`

If the function has not already been executed, you can stop the execution by calling the `clearTimeout()` method:





- The setInterval() Method

The `setInterval()` method repeats a given function at every given time-interval.

`window.setInterval(function, milliseconds);`

The `window.setInterval()` method can be written without the window prefix.

The first parameter is the function to be executed.

The second parameter indicates the length of the time-interval between each execution.

This example executes a function called "myTimer" once every second (like a digital watch).






## Cookies

- Create a Cookie with JavaScript

JavaScript can create, read, and delete cookies with the document.cookie property.

With JavaScript, a cookie can be created like this:

`document.cookie = "username=John Doe";`







- Read a Cookie with JavaScript

With JavaScript, cookies can be read like this:

`var x = document.cookie;`





- A Function to Set a Cookie

First, we create a function that stores the name of the visitor in a cookie variable:


```ruby
function setCookie(cname, cvalue, exdays) {
  var d = new Date();
  d.setTime(d.getTime() + (exdays*24*60*60*1000));
  var expires = "expires="+ d.toUTCString();
  document.cookie = cname + "=" + cvalue + ";" + expires + ";path=/";
}
```





- A Function to Get a Cookie

Then, we create a `function` that returns the value of a specified cookie:


```ruby
function getCookie(cname) {
  var name = cname + "=";
  var decodedCookie = decodeURIComponent(document.cookie);
  var ca = decodedCookie.split(';');
  for(var i = 0; i <ca.length; i++) {
    var c = ca[i];
    while (c.charAt(0) == ' ') {
      c = c.substring(1);
    }
    if (c.indexOf(name) == 0) {
      return c.substring(name.length, c.length);
    }
  }
  return "";
}
```



- A Function to Check a Cookie

Last, we create the function that checks if a cookie is set.

If the cookie is set it will display a greeting.

If the cookie is not set, it will display a prompt box, asking for the name of the user, and stores the username cookie for 365 days, by calling the `setCookie` function:



```ruby
function checkCookie() {
  var username = getCookie("username");
  if (username != "") {
   alert("Welcome again " + username);
  } else {
    username = prompt("Please enter your name:", "");
    if (username != "" && username != null) {
      setCookie("username", username, 365);
    }
  }
}
```
