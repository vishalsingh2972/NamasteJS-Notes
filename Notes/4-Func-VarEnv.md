# Episode 4 : Functions and Variable Environments

```javascript
var x = 1;
a();
b(); // we are calling the functions before defining them. This will work properly, as seen in Hoisting (Ep3)
console.log(x);

function a() {
  var x = 10;
  console.log(x);
}

function b() {
  var x = 100;
  console.log(x);
}
```

Outputs:

> 10

> 100

> 1

### Code Flow

- The Global Execution Context (GEC) is created (the big box with Memory and Code subparts). Also GEC is pushed into Call Stack
  > Call Stack : GEC
- In first phase of GEC (memory phase), variable x:undefined and a and b have their entire function code as value initialized
- In second phase of GEC (execution phase), After x = 1 assigned to GEC x, a() is called. So local EC for a is made inside code part of GEC.

> Call Stack: [GEC,a()], now control goes to local EC so a() is added in the call stack

- For local EC, a totally different x variable assigned undefined(x inside a()) in phase 1 , and in phase 2 it is assigned 10 and printed in console log., and here using console.log javascript engine will look for the value of x in the local memory space i.e in this case the local execution context of a, so it prints x=10 because in this case currently value of x in local memory = value of x in the local execution
  context of a() function i.e x=10, so console.log(x); prints 10;
- After printing, no more commands to run, so a() local EC gets deleted and is removed/popped out from from the Call stack and only GEC remains in the call stack, control goes back from a() to GEC

> Call Stack: GEC

- Now control back to GEC from a(), cursor currently back at line 5, all sorted here so cursor goes to next line i.e line number 6

> Call Stack :[GEC, b()] -> GEC (after printing yet another totally different x value as 100 in console log).
> -Now that cursor is at line number 6, control goes from GEC to b() and same steps repeat as we did in case of a() function.

- After printing, no more commands to run, so b() local EC gets deleted and is removed/popped out from from the Call stack and only GEC remains in the call stack, control goes back from b() to GEC

> Call Stack: GEC

- Now control back to GEC from b(), cursor currently back at line 6, all sorted here so cursor goes to next line i.e line number 7
- Next control reaches line 7 console.log(x); so again javascript engine will look for the value of x in the local memory space but in this case it is the global execution context i.e where x=1, so console.log(x); prints 1;
- Finall after line 7, javascript engines sees that there is nothing else to execute in the lines below after line 7 i.e basically there is nothing more to execute in the remaining program after line number 7
- Now that whole code is executed so now the GEC is alse deleted and GEC also gets removed/popped out from the call stack. (so now call stack is currently empty)
- So now GEC deleted and call stack is empty. Program ends.
