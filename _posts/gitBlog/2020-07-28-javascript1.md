---
title:  "JavaScript 정리1"
excerpt: "2020웹서비스 개발 캠프 Day6"
toc: true
toc_sticky: true

categories:
  - gitBlog
tags:
  - GitHub
  - Blog
  - categories
  - JavaScript
last_modified_at: 2020-07-27
---


참조 사이트 [w3schools.com](https://www.w3schools.com/js/js_validation.asp)






## Form

```ruby
<form action="/action_page.php" method="post">
  <input type="text" name="fname" required>
  <input type="submit" value="Submit">
</form>

<p>If you click submit, without filling out the text field,
your browser will display an error message.</p>
```




## checkValidity()

```ruby
<p>Enter a number and click OK:</p>

<input id="id1" type="number" min="100" max="300" required>
<button onclick="myFunction()">OK</button>

<p>If the number is less than 100 or greater than 300, an error message will be displayed.</p>

<p id="demo"></p>

<script>
function myFunction() {
  var inpObj = document.getElementById("id1");
  if (!inpObj.checkValidity()) {
    document.getElementById("demo").innerHTML = inpObj.validationMessage;
  } else {
    document.getElementById("demo").innerHTML = "Input OK";
  }
}
</script>
```





## The rangeOverflow Property

```ruby
<input id="id1" type="number" max="100">
<button onclick="myFunction()">OK</button>

<p id="demo"></p>

<script>
function myFunction() {
  var txt = "";
  if (document.getElementById("id1").validity.rangeOverflow) {
    txt = "Value too large";
  }
  document.getElementById("demo").innerHTML = txt;
}
</script>
```





## The rangeUnderflow Property

```ruby
<input id="id1" type="number" min="100">
<button onclick="myFunction()">OK</button>

<p id="demo"></p>

<script>
function myFunction() {
  var txt = "";
  if (document.getElementById("id1").validity.rangeUnderflow) {
    txt = "Value too small";
  }
  document.getElementById("demo").innerHTML = txt;
}
</script>
```





## DOM

>Document Object Model


When a web page is loaded, the browser creates a **Document Object Model** of the page.

In the DOM, all HTML elements are defined as **objects**.

The programming interface is the properties and methods of each object.

A **property** is a value that you can get or set (like changing the content of an HTML element).

A **method** is an action you can do (like add or deleting an HTML element).



```ruby
<html>
<body>

<p id="demo"></p>

<script>
document.getElementById("demo").innerHTML = "Hello World!";
</script>

</body>
</html>
```

In the example above, getElementById is a method, while innerHTML is a property.




- Finding HTML Element by Id

```ruby
<p id="intro">Hello World!</p>
<p>This example demonstrates the <b>getElementsById</b> method.</p>

<p id="demo"></p>

<script>
var myElement = document.getElementById("intro");
document.getElementById("demo").innerHTML =
"The text from the intro paragraph is " + myElement.innerHTML;
</script>
```

This example finds the element with `id="intro"`





- Finding HTML Elements by Tag Name

```ruby
<p>Hello World!</p>
<p>This example demonstrates the <b>getElementsByTagName</b> method.</p>

<p id="demo"></p>

<script>
var x = document.getElementsByTagName("p");
document.getElementById("demo").innerHTML =
'The text in first paragraph (index 0) is: ' + x[0].innerHTML;
</script>
```




- Finding HTML Elements by Class Name

```ruby
<p class="intro">The DOM is very useful.</p>
<p class="intro">This example demonstrates the <b>getElementsByClassName</b> method.</p>

<p id="demo"></p>

<script>
var x = document.getElementsByClassName("intro");
document.getElementById("demo").innerHTML =
'The first paragraph (index 0) with class="intro": ' + x[0].innerHTML;
</script>
```




## Changing HTML

- In JavaScript, `document.write()` can be used to write directly to the HTML output stream

>Date: Tue Jul 28 2020 11:36:45 GMT+0900 (대한민국 표준시)





- The easiest way to modify the content of an HTML element is by using the `innerHTML` property.

`document.getElementById(id).innerHTML = new HTML`





- To change the value of an HTML attribute, use this syntax:

`document.getElementById(id).attribute = new value`







## Changing CSS

- To change the style of an HTML element, use this syntax:

`document.getElementById(id).style.property = new style`





- Using events

The HTML DOM allows you to execute code when an event occurs.

This example changes the style of the HTML element with id="id1", when the user clicks a button:

```ruby
<body>

<h1 id="id1">My Heading 1</h1>

<button type="button"
onclick="document.getElementById('id1').style.color = 'red'">
Click Me!</button>

</body>
```






## Animation

- Create the Animation Using JavaScript

```ruby
function myMove() {
  var elem = document.getElementById("animate");
  var pos = 0;
  var id = setInterval(frame, 5);
  function frame() {
    if (pos == 350) {
      clearInterval(id);
    } else {
      pos++;
      elem.style.top = pos + 'px';
      elem.style.left = pos + 'px';
    }
  }
}
```






## Events

- A JavaScript can be executed when an event occurs, like when a user clicks on an HTML element.

To execute code when a user clicks on an element, add JavaScript code to an HTML event attribute:

`onclick=JavaScript`



```ruby
<body>

<h1 onclick="changeText(this)">Click on this text!</h1>

<script>
function changeText(id) {
  id.innerHTML = "Ooops!";
}
</script>

</body>
```




- Assign Events Using the HTML DOM

```ruby
<p>Click "Try it" to execute the displayDate() function.</p>

<button id="myBtn">Try it</button>

<p id="demo"></p>

<script>
document.getElementById("myBtn").onclick = displayDate;

function displayDate() {
  document.getElementById("demo").innerHTML = Date();
}
</script>
```




- The onload and onunload Events

```ruby
<div onmousedown="mDown(this)" onmouseup="mUp(this)"
style="background-color:#D94A38;width:90px;height:20px;padding:40px;">
Click Me</div>

<script>
function mDown(obj) {
  obj.style.backgroundColor = "#1ec5e5";
  obj.innerHTML = "Release Me";
}

function mUp(obj) {
  obj.style.backgroundColor="#D94A38";
  obj.innerHTML="Thank You";
}
</script>
```

The `onmousedown`, `onmouseup`, and `onclick` events are all parts of a mouse-click. First when a mouse-button is clicked, the onmousedown event is triggered, then, when the mouse-button is released, the onmouseup event is triggered, finally, when the mouse-click is completed, the onclick event is triggered.







## EventListener

- Add an event listener that fires when a user clicks a button:

`document.getElementById("myBtn").addEventListener("click", displayDate);`


```ruby
<p>This example uses the addEventListener() method to attach a click event to a button.</p>

<button id="myBtn">Try it</button>

<p id="demo"></p>

<script>
document.getElementById("myBtn").addEventListener("click", displayDate);

function displayDate() {
  document.getElementById("demo").innerHTML = Date();
}
</script>
```





- syntax

`element.addEventListener(event, function, useCapture);`

The first parameter is the type of the event (like `click` or `mousedown` or any other HTML DOM Event.)

The second parameter is the function we want to call when the event occurs.

The third parameter is a boolean value specifying whether to use event bubbling or event capturing. This parameter is optional.





- Add Many Event Handlers to the Same Element

`addEventListener()` method allows you to add many events to the same element, without overwriting existing events.


```ruby
<p>This example uses the addEventListener() method to add two click events to the same button.</p>

<button id="myBtn">Try it</button>

<script>
var x = document.getElementById("myBtn");
x.addEventListener("click", myFunction);
x.addEventListener("click", someOtherFunction);

function myFunction() {
  alert ("Hello World!");
}

function someOtherFunction() {
  alert ("This function was also executed!");
}
</script>
```




- Add an Event Handler to the window Object

```ruby
window.addEventListener("resize", function(){
  document.getElementById("demo").innerHTML = sometext;
});
```




## Dom Navigation


Node         type             Example

ELEMENT_NODE	1	`<h1 class="heading">W3Schools</h1>`

ATTRIBUTE_NODE	2	 `class = "heading" (deprecated)`

TEXT_NODE	3	`W3Schools`

COMMENT_NODE	8	`<!-- This is a comment -->`

DOCUMENT_NODE	9	`The HTML document itself (the parent of <html>)`

DOCUMENT_TYPE_NODE	10	`<!Doctype html>`





## Collections

The `getElementsByTagName()` method returns an `HTMLCollection` object.

An `HTMLCollection` object is an array-like list (collection) of HTML elements.

The following code selects all `<p>` elements in a document:


```ruby
<p>Hello World!</p>

<p>Hello Norway!</p>

<p id="demo"></p>

<script>
var myCollection = document.getElementsByTagName("p");
document.getElementById("demo").innerHTML =
"The innerHTML of the second paragraph is: " +
myCollection[1].innerHTML;
</script>
```





## Node list

```ruby
<p>Hello World!</p>

<p>Hello Norway!</p>

<p>Click the button to change the color of all p elements.</p>

<button onclick="myFunction()">Try it</button>

<script>
function myFunction() {
  var myNodelist = document.querySelectorAll("p");
  var i;
  for (i = 0; i < myNodelist.length; i++) {
    myNodelist[i].style.color = "red";
  }
}
</script>
```




- The Difference Between an HTMLCollection and a NodeList

An `HTMLCollection` is a collection of **HTML elements**.

A` NodeList` is a collection of **document nodes**.

A NodeList and an HTML collection is very much the same thing.

Both an HTMLCollection object and a NodeList object is an array-like list (collection) of objects.

Both have a length property defining the number of items in the list (collection).

Both provide an index (0, 1, 2, 3, 4, ...) to access each item like an array.

HTMLCollection items can be accessed by their name, id, or index number.

NodeList items can only be accessed by their index number.

Only the NodeList object can contain attribute nodes and text nodes.




- (+ A node list is not an array!)

A node list may look like an array, but it is not.

You can loop through the node list and refer to its nodes like an array.

However, you cannot use Array Methods, like valueOf(), push(), pop(), or join() on a node list.
