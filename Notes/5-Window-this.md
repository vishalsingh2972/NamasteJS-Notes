# Episode 5: Window and this keyword

### Everywhere JS is run, it is done with a JS execution engine. For Chrome: v8

- Shortest JS program is nothing but an Empty JS file
- Even for this program, JS engine does a lot behind the scenes
- It creates the GEC, the "window" (GLOBAL OBJECT) and the *this* variable
- There is always a GLOBAL OBJECT created when we run a JS program, for eg. even in the case of an Empty JS file program, JS will still create GLOBAL OBJECT even in this case
- Window is a big global object that has a lot of functions and variables. All of these can be accessed from anywhere in the program
- *this* points to *window*
> this === window -> true (at global level)
```
var a = 10;      // not inside any fun. So global object
function b() {    // this fun not inside any function. So global.
  var x = 5;    // not global
 }
console.log(window.a); //gives us "a" value
console.log(this.a); //this points to window so it returns "a" value
console.log(a); //also gives same "a" value. (if we dont put any . in front of variable, it **assumes variable is in global space**
console.log(x); // x is not defined. (tries to find x inside global space, but it isn't there) 
```
- Global object in case of browsers is known as a window. Javascripts is not just run on browsers, JS is running on servers and a lot of other devices as well, and wherever JS is runnning there must be a JS engine present, for example V8 is the name of the JavaScript engine that powers Google Chrome browser, Chakra is the name of the JavaScript engine that powers Internet Explorer browser, SpiderMonkey is the name of the JavaScript engine that powers Mozilla Firefox browser etc., so all these JS engines have a responsibility to create the global object and  in case of a web browser this global object is known as a WINDOW.
- Global space is any code that we write in JS which is not inside a function. Basically anything which is not inside any fucntion is the Global space. 
- When a GEC is made, *this* is also created with it (even for functional(local) EC). Global object provided by the browser engine is the window, so *this* points to window.
