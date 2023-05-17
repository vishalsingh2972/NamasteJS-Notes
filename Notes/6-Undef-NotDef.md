# Episode 6: Undefined vs Not Defined

- In first phase (mem alloc) JS assigns each variable to a placeholder called *undefined*
- *undefined* is when memory is allocated for the variable, but no value is assigned yet.
- Remember *undefined* is not equal to empty, we usually assume that *undefined* means empty because we assume it is not taking up any memory space- this assumpton is wrong, rather in reality *undefined* is a special keyword and *undefined* takes up its own memory space, also you can assume *undefined* to be like a placeholder which is kept for the time being until the variable is assigned some other value to it, so till a value is assigned to a variable until that time the variable will store this value called as *undefined* in it.
- If an object/variable is not even declared/found in mem alloc phase, and tried to access it then it is *Not Defined*

> When variable is declared but not assigned value, its current value is undefined. But when the variable itself is not declared but called in code, then it is not defined. 

```
console.log(a);
var a = 25;

console.log(a);
console.log(x);

```
>undefined <br/>
>25 <br/>
>Uncaught ReferenceError: x is not defined , Basically no variable x is present in the memory yet so it will give not defined error


- JS is a loosely-typed / weakly-typed language. It doesn't attach variables to any datatype. We can say var a = 5, and then change the value to bool (a = true) or string
(a = 'hello') later on. 
- **Never** assign *undefined* to a variable manually. Let it happen on it's own accord.
