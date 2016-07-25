# JavaScript

## Good practices
#### Avoid JavaScript where we can handle with pure HTML+CSS
 HTML and CSS are declarative, JavaScript is imperative - that's main reason why you should prefer HTML and CSS.

#### Don't use scripts from external sources
 The same as similar tip from [CSS](/front-end-tips/content/css.html#dont-use-styles-from-external-sources)

#### Add all `<script>` before closing `</body>` tag
 This allow your site to show first content without blocking on code execution

#### All complex boolean instructions should be moved to function
 Avoid instruction with more than 1 operator inside of `if` conditions. Move such code `(allowUpdate) && ((user.isAdmin) || (user.role === item.owner)` to the separate function like `isAdminAndCanUpdate`

#### Don't change the prototypes of built-in constructors
 Of course sometimes it is good move - to extend `String.prototype` или `Function.prototype` but extend it only with standard widely used functions. For example you can create polyfill for `Function.prototype.bind` if you know very good what you are doing

#### Try to not mutate one variable in a lot of functions
  Consider following code:
  ```
  var box = {};

  function addBall(box) {
    box.ball = {radius: 2};
  }
  function addFood(box) {
    box.food = {carrot: 4};
  }
  function addShoes(box) {
    box.shoes = {sneakers: 2};
  }
  addBall(box);
  addFood(box);
  addShoes(box);
  ```
  Here we have to large area of usage for variable `box`. In greater apps that use such patterns we will be confused why some vars eventually will have dozens of carrots and thousands of shoes :)

#### Don't use literals right in code, move it to separate module
 `if (status === 'active') {...}` - this is bad  
 `if (status === constants.ACTIVE_STATUS) {...}` - this is correct

#### Use [Modernizr](https://modernizr.com/) for feature detection
 Don't hope that comparing with user-agent is a better idea

#### Learn how the browser render the page
 This will allow you write applications with better performance and avoid a lot of mistakes while working with native DOM API. The good explanation [is here](http://www.phpied.com/rendering-repaint-reflowrelayout-restyle/)

#### Place public methods first and private methods last
 All methods try to group be their meaning

#### Divide logging to debug level and production level
 Sometimes it is good practice to produce some logs in production - but keep your debug warnigns away from end users

#### Try to change classes for elements, not the direct CSS properties
``` 
var el = document.getElementById(id);

// avoid such code
el.style.color = "red";
el.style.fontSize = "15px";
el.style.backgroundColor = "#FFFFFF";

// use such approach
el.classList.add("outstanding-text")
```


## JQuery
#### Duplicate all classes with prefixes `js-` that you use in JavaScript
 Don't rely on classes that you also use for styling, sometimes you will change them because you will need new appearance. With such action you will break the scripts also! This tip will save you from double event handlers or outdated listeners  
 ```<div class="open-popup-button js-open-popup-button"></div>```  
 In js-files you will use only second class:  
  `$('.js-open-popup-button').click(...);`

#### Cache all possible search results
If there is no need to search elements again - cache results into the variable
```
// this is bad
$('.element').show();
$('.element').find('.children').doSomething();
$('.element').attr('data-id', 123);

// this is correct
var $element = $('.element');
$element.show();
$element.find('.children').doSomething();
$element.attr('data-id', 123);
```

#### Add prefix `$` for all variables with jQuery API
```
var $element = $('.element');
var $this = $(this);
var $lists = $body.find('ul');


var chatBox = document.getElementById('chat-box');  // because it is native DOM element
var firstList = $lists[0];  // because it is also native DOM element
```

#### Concat selectors for elements with common behaviour
```
// bad way
$('form p').addClass('valid');
$('form li').addClass('valid');
$('form span').addClass('valid');

// good way
$('form p, form li, form span').addClass('valid');
```

#### Make as much as possible with virtual elements
When you need to add multiple elements in the DOM - create virtual parent and inject element there. When all work is done you can inject only one parent in the DOM with one instuction:
```
// bad way, we inject each element separately
for (var i=0; i < items.length; i++){ 
  var item = document.createElement("li");
  item.appendChild(document.createTextNode("Option " + i);
  list.appendChild(item); 
}

// good way - we gather all element in the virtual Fragment before appending to the list
var fragment = document.createDocumentFragment();
for (var i=0; i < items.length; i++){
  var item = document.createElement("li"); 
  item.appendChild(document.createTextNode("Option " + i);
  fragment.appendChild(item); 
} 
list.appendChild(fragment);
```

## Libraries
#### Don't edit libraries in the project
If you critically need to change the library - fork it one Github and point new version in dependencies file (e.g. `package.json`)

#### How to choose library
When you need to add new feature to your project (for example new pretty dropdown or URL routing) it is good choice to use some library. Usually they are tested and written much better than your own possible decision. Although it is hard for newbies to detect library with a bad code and choose the best when there are a bunch of candidacies.
Check for each candidacy:
1. Is there a public repository and where it is?
2. Is there a documentation and does it describe how to solve exactly your problem?
3. If there is no detailed documentation learn a source code and understand how it solve your problem?
4. Learn last issues - does it relate to your problems?
5. If there are other front-end developers working on the samke project, make a decision together.




