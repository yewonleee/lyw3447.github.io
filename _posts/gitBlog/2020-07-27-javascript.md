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


참조 사이트 [w3schools.com](https://www.w3schools.com/js/js_intro.asp)






## window.alert()

```ruby
<!DOCTYPE html>
<html>
<body>

<h1>My First Web Page</h1>
<p>My first paragraph.</p>

<script>
window.alert(5 + 6);
</script>

</body>
</html>
```



## onclick

- 버튼 클릭했을 때 밑의 줄에 결과 발생

```ruby
<button onclick="document.getElementById('demo').innerHTML = Date()">The time is?</button>

<p id='demo'></demo>
```

```ruby
<button onclick="displayDate()">The time is?</button>

<script>
function displayDate() {
  document.getElementById("demo").innerHTML = Date();
}
</script>

<p id="demo"></p>
```





- 버튼 속에 결과 발생

```ruby
<button onclick="this.innerHTML=Date()">The time is?</button>
```






- `onchange` `onclick` `onmouseover` `onmousout` `onkeydown` `onload `







## Date objects

```ruby
<p id="demo"></p>

<script>
var d = new Date();
document.getElementById("demo").innerHTML = d;
</script>
```




- 100000000000 milliseconds from Jan 1, 1970, is approximately Mar 3, 1973

```ruby
<p id="demo"></p>

<script>
var d = new Date(100000000000);
document.getElementById("demo").innerHTML = d;
</script>
```




- Set Date Methods

```ruby
<script>
var d = new Date();
d.setFullYear(2020, 11, 3);
document.getElementById("demo").innerHTML = d;
</script>
```

2020/11/03 날짜의 요일까지 나온다






- setMonth()
```ruby
<script>
var d = new Date();
d.setMonth(11);
document.getElementById("demo").innerHTML = d;
</script>
```

'월'만 변경된다.

0부터 count



`setDate()` `setHours()` `setSeconds()`






## Use Strict

`"use strict";` Defines that JavaScript code should be executed in "strict mode".

```ruby
<script>
"use strict";
x = 3.14;  // This will cause an error (x is not defined).
</script>
```




## **this** keyword

```ruby
var person = {
  firstName: "John",
  lastName : "Doe",
  id       : 5566,
  fullName : function() {
    return this.firstName + " " + this.lastName;
  }
};
```


```ruby
<button onclick="this.style.display='none'">
  Click to Remove Me!
</button>
```





## **let**

Global variable  `let`

Redeclaring a var variable with `let`, in the *same scope*, or in the *same block*, is not allowed




## **const**

Variables defined with `const` behave like `let` variables, except they *cannot be reassigned*

```ruby
const PI = 3.141592653589793;
PI = 3.14;      // This will give an error
PI = PI + 10;   // This will also give an error
```

Also, `const` variables must be assigned a value *when they are declared*


However, you can change the properties of a constant object.

```ruby
// You can create a const object:
const car = {type:"Fiat", model:"500", color:"white"};

// You can change a property:
car.color = "red";

// You can add a property:
car.owner = "Johnson";
```


```ruby
const x = 2;       // Allowed
const x = 3;       // Not allowed
x = 3;             // Not allowed
var x = 3;         // Not allowed
let x = 3;         // Not allowed

{
  const x = 2;   // Allowed
  const x = 3;   // Not allowed
  x = 3;         // Not allowed
  var x = 3;     // Not allowed
  let x = 3;     // Not allowed
}
```


- Redeclaring a variable with const, in another scope, or in another block, is allowed

```ruby
const x = 2;       // Allowed
{
  const x = 3;   // Allowed
}

{
  const x = 4;   // Allowed
}
```




## Debugging

```ruby
<h1>My First Web Page</h1>

<script>
a = 5;
b = 6;
c = a + b;
console.log(c);
</script>
```



## JSON

- JSON stands for JavaScript Object Notation
- JSON is a lightweight data interchange format
- JSON is language independent *
- JSON is "self-describing" and easy to understand


```ruby
"employees":[
  {"firstName":"John", "lastName":"Doe"},
  {"firstName":"Anna", "lastName":"Smith"},
  {"firstName":"Peter", "lastName":"Jones"}
]
}
```

This JSON syntax defines an employees object: an array of 3 employee records (objects)
