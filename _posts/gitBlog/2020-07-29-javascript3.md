---
title:  "JavaScript 정리3"
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
  - Ajax
last_modified_at: 2020-07-29
---


참조 사이트 [w3schools.com](https://www.w3schools.com/js/js_validation.asp)




## Introduction

- What is AJAX?

AJAX = Asynchronous JavaScript And XML.

AJAX is not a programming language.

AJAX just uses a combination of:

A browser built-in `XMLHttpRequest` object (to request data from a web server)
JavaScript and HTML DOM (to display or use the data)






## The XMLHttpRequest Object

All modern browsers support the `XMLHttpRequest` object.

The `XMLHttpRequest` object can be used to exchange data with a web server behind the scenes. This means that it is possible to update parts of a web page, without reloading the whole page.





- Create an XMLHttpRequest Object

All modern browsers (Chrome, Firefox, IE7+, Edge, Safari, Opera) have a built-in `XMLHttpRequest` object.


Syntax for creating an XMLHttpRequest object:

`variable = new XMLHttpRequest();`


```ruby
var xhttp = new XMLHttpRequest();
```



- XMLHttpRequest Object Methods

|Method|Description|
|new XMLHttpRequest()||	Creates a new XMLHttpRequest object|
|abort()||	Cancels the current request|
|getAllResponseHeaders()|	Returns header information|
|getResponseHeader()|	Returns specific header information|
|open(method, url, async, user, psw)|	Specifies the request
method: the request type GET or POST
url: the file location
async: true (asynchronous) or false (synchronous)
user: optional user name
psw: optional password|
|send()|	Sends the request to the server
Used for GET requests
|send(string)	Sends the request to the server.
Used for POST requests|
|setRequestHeader()|	Adds a label/value pair to the header to be sent|





- Property	Description

onreadystatechange	Defines a function to be called when the readyState property changes

readyState	Holds the status of the XMLHttpRequest.
0: request not initialized
1: server connection established
2: request received
3: processing request
4: request finished and response is ready

responseText	Returns the response data as a string

responseXML	Returns the response data as XML data

status	Returns the status-number of a request
200: "OK"
403: "Forbidden"
404: "Not Found"
For a complete list go to the Http Messages Reference

statusText	Returns the status-text (e.g. "OK" or "Not Found")





## Send a Request To a Server

Send a Request To a Server

To send a request to a server, we use the open() and send() methods of the `XMLHttpRequest` object:

`xhttp.open("GET", "ajax_info.txt", true);
xhttp.send();`




- The url - A File On a Server
The url parameter of the open() method, is an address to a file on a server:

`xhttp.open("GET", "ajax_test.asp", true);`

The file can be any kind of file, like .txt and .xml, or server scripting files like .asp and .php (which can perform actions on the server before sending the response back).







- Asynchronous - True or False?
Server requests should be sent asynchronously.

The async parameter of the open() method should be set to true:

`xhttp.open("GET", "ajax_test.asp", true);`
By sending asynchronously, the JavaScript does not have to wait for the server response, but can instead:

execute other scripts while waiting for server response
deal with the response after the response is ready






- The onreadystatechange Property
With the XMLHttpRequest object you can define a function to be executed when the request receives an answer.


The function is defined in the onreadystatechange property of the XMLHttpRequest object:

```ruby
xhttp.onreadystatechange = function() {
  if (this.readyState == 4 && this.status == 200) {
    document.getElementById("demo").innerHTML = this.responseText;
  }
};
xhttp.open("GET", "ajax_info.txt", true);
xhttp.send();
```




## Server Response

- The onreadystatechange Property


The `readyState` property holds the status of the XMLHttpRequest.

The `onreadystatechange` property defines a function to be executed when the readyState changes.

The `status` property and the `statusText` property holds the status of the XMLHttpRequest object.

```ruby
function loadDoc() {
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      document.getElementById("demo").innerHTML =
      this.responseText;
    }
  };
  xhttp.open("GET", "ajax_info.txt", true);
  xhttp.send();
}
```





- Using a Callback Function

A callback function is a function passed as a parameter to another function.

If you have more than one AJAX task in a website, you should create one function for executing the `XMLHttpRequest` object, and one callback function for each AJAX task.

The function call should contain the URL and what function to call when the response is ready.



```ruby
loadDoc("url-1", myFunction1);

loadDoc("url-2", myFunction2);

function loadDoc(url, cFunction) {
  var xhttp;
  xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      cFunction(this);
    }
  };
  xhttp.open("GET", url, true);
  xhttp.send();
}

function myFunction1(xhttp) {
  // action goes here
}
function myFunction2(xhttp) {
  // action goes here
}
```






## XML Example

When a user clicks on the "Get CD info" button above, the `loadDoc()` function is executed.

The `loadDoc()` function creates an `XMLHttpRequest`object, adds the function to be executed when the server response is ready, and sends the request off to the server.

When the server response is ready, an HTML table is built, nodes (elements) are extracted from the XML file, and it finally updates the element "demo" with the HTML table filled with XML data:


```ruby
function loadDoc() {
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
    myFunction(this);
    }
  };
  xhttp.open("GET", "cd_catalog.xml", true);
  xhttp.send();
}
function myFunction(xml) {
  var i;
  var xmlDoc = xml.responseXML;
  var table="<tr><th>Artist</th><th>Title</th></tr>";
  var x = xmlDoc.getElementsByTagName("CD");
  for (i = 0; i <x.length; i++) {
    table += "<tr><td>" +
    x[i].getElementsByTagName("ARTIST")[0].childNodes[0].nodeValue +
    "</td><td>" +
    x[i].getElementsByTagName("TITLE")[0].childNodes[0].nodeValue +
    "</td></tr>";
  }
  document.getElementById("demo").innerHTML = table;
}
```






## 
