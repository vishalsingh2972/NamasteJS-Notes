# Episode 6: Undefined vs Not Defined

- In first phase (mem alloc) JS assigns each variable to a placeholder called _undefined_
- _undefined_ is when memory is allocated for the variable, but no value is assigned yet.
- Remember _undefined_ is not equal to empty, we usually assume that _undefined_ means empty because we assume it is not taking up any memory space- this assumpton is wrong, rather in reality _undefined_ is a special keyword and _undefined_ takes up its own memory space, also you can assume _undefined_ to be like a placeholder which is kept for the time being until the variable is assigned some other value to it, so till a value is assigned to a variable until that time the variable will store this value called as _undefined_ in it.
- If an object/variable is not even declared/found in mem alloc phase, and tried to access it then it is _Not Defined_

> When variable is declared but not assigned value, its current value is undefined. But when the variable itself is not declared but called in code, then it is not defined.

```javascript
// code example 1
console.log(a);
var a = 25;

console.log(a);
console.log(x);
```

> undefined <br/>
> 25 <br/>
> Uncaught ReferenceError: x is not defined , Basically no variable x is present in the memory yet so it will give not defined error

```javascript
// code example 2 - until value is assigned to "a" it will remain having value assigned as undefined
var a;

console.log(a);

if (a === undefined) {
  console.log("a is undefined");
  //console.log(a);
} else {
  console.log("a is NOT undefined");
  //console.log(a);
}
```

> undefined <br/>
> a is undefined <br/>

```javascript
// code example 3
var a;

console.log(a);
a = 10;

if (a === undefined) {
  console.log("a is undefined");
  //console.log(a);
} else {
  console.log("a is NOT undefined");
  //console.log(a);
}
```

> undefined <br/>
> a is NOT undefined <br/>

- JS is a loosely-typed / weakly-typed language. It doesn't attach variables to any datatype. We can say var a = 5, and then change the value to bool (a = true) or string
  (a = 'Hello Vishal') later on.

```javascript
// code example 4
var a;

console.log(a);
a = 10;
console.log(a);
a = "Hello Vishal";
console.log(a);

}
```

> undefined <br/>
> 10 <br/>
> Hello Vishal

- **Never** assign _undefined_ to a variable manually. Let it happen on it's own accord. Basically it is not a good practise to manually assign undefined to any variable as it can lead to a lot of inconsistencies so better avoid this practise.

```javascript
// code example 5
var a;

console.log(a);
a = 10;
console.log(a);
a = "Hello Vishal";
console.log(a);

a = undefined; // wrong practise
console.log(a); // you will still get the output as usual but this practise is wrong so avoid using this

}
```

> undefined <br/>
> 10 <br/>
> Hello Vishal

> undefined :x:
