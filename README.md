# LightCore
JavaScript Library that adds "easy" features into JS Code

# Heres some examples:
## Quick Access Attributes:
```js
// JS Native
element.style.opacity = 0;
element.style.filter='blur(10px)';
element.addEventListener('click', myFunc)

// LightCore
element.alpha = 0;
element.filter='blur(10px)'; // And all of "styles" attributes
element.listen('click', myFunc)
```
## New Abilities:
```js
// (creating an "border: solid 1px red" for all elements)
debug.hits(); // -> boolean isEnabled
debug.outlinedHits(); // same but using "outline" instead of "border"

find('button.exmaple') // -> same result as document.querySelector 
findAll('button.exmaple') // -> same result as document.querySelectorAll
element.find('img') // fill also work (and findAll too)

log('hello world'); // "hello world!";

body; head; HTML; // -> main DOM elements

element.destroy(); // same as ".remove()" but this was done to copy GUI commands to Java, Python so as not to get confused.

element.cornerRadius = 20; console.log(element.cornerRadius);
```
## Common Functions:
```js
log(random(1, 2)) // -> From 1 to 2 inclusive
sleep(100); // -> Promise
```


I created this library "for myself" to speed up the tedious moments of JS. I can add functionality here as soon as I need it, and I apologize in advance for the "compatibility errors" on different browsers.
