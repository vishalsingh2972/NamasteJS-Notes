# Episode 10 : Closures in JS

### Important Interview Question

**Closure :** Function bundled together with its lexical environment/scope. //Function along with its lexical scope forms a closure.

```
//Example 1

function x(){
  var a = 7;
  function y(){
    console.log(a);
  }
  y();
}

x();
```
```
//Example 2 - Assigning entire function to a variable

function x(){
  var a = function y(){
    console.log(a);
  };
  
  y();
}

x();
```
```
//Example 3 - Passing an entire function as a parameter inside another function

function x(){
  var a = 7;
  
  y();
}

x(function y(){
    console.log(a);
  });
```
```
//Example 4 - return a function from a function

function x(){
  var a = 7;
  function y(){
    console.log(a);
  }
  return y;
}

x();
```
```
//Example 5 - extension of Example 4

function x(){
  var a = 7;
  function y(){
    console.log(a);
  }
  return y;
}

//console.log(z);
var z = x();
console.log(z);
```
-----------------------
When functions are returned from another fun, they still maintain their lexical
scope.
 ```
function x(){
  var a = 7;
  function y(){
    console.log(a);
  }
  return y;
}

var z = x(); //line 9
console.log(z);
//....................after 1000 lines of code
z();
```
- When y is returned, not only is the function returned but the entire closure (func. y + its lexical scope) is returned and put inside z. So when z is used somewhere else in program, it still remembers var a inside x() //so even though after line 9 evn though x() function or x EC no longer exists in the memory but the y() function still remembers its lexical scope/environment or basically where it came from //so even though x is lost y still has strong binding with its parent x
- Even though the x function is no longer accessible after line 9, the y function still has a strong binding with it. This is because the y function is a closure. A closure is a function that has access to the variables of its enclosing scope, even after the enclosing scope has been closed.
- Closure is a very powerful concept of JS, just because this function remembers things even if they are not in their lexical scope

### Uses of Closure

Module Design Pattern, Currying, Functions like once(fun that can be run only
once), memoize, maintaining state in async world, setTimeout, iterators...
