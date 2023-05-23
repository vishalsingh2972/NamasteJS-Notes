# Episode 9 : Block Scope and Shadowing

### What is a block?
- Block a.k.a *compound statement* is used to group JS statements together into 1 group. We group them within {...}
- Why do we need to group all the statements together? - The purpose of grouping all the statements together in a block is so that we can use multiple statements in a place where JS expects only 1 statement.

```
//code example 1

if(true)some statement
```

But if we want to write more statements to execute after if condition; then:

```
//code example 2

if(true){
    statement 1
    statement 2
    ...
}
```

* The {} block treats all the statements as one statement.
* The if doesnt have any curly braces in syntax.

### __BLOCK SCOPE__

* What are the variables and functions that can be accessed inside the block.

```
//code example 3

{
    var a = 10;
    let b = 20;
    const c = 30;
} //line 5

console.log(a);
console.log(b);
```

Outputs:

> 10

> Uncaught ReferenceError: b is not defined

* Behind the Scenes:

    * In the BLOCK SCOPE; we get b and c inside it initialized as *undefined* as a part of hoisting (in a seperate memory space called block)
    * While, a is stored inside a GLOBAL scope. 

* Thus we say, *let* and *const* are BLOCK SCOPED. They are stored in a separate mem space which is reserved for this block. Also, they can't be accessed outside this block.
But var a can be accessed anywhere as it is in global scope.
* Thus, we can't access them outside the Block. (//after executing it reaches line 5 and now after line 5 variables b and c are no longer accessible as after line 5, the block is finished and *let* and *const* are not accessible outside the block)
* Hence, **Variables declared with *let* and *const* are not accessible outside the block in which they are declared. This is called block scope**. 
* But observe we can access var a even outside the block (i.e even after line 5) because var is in the global scope or attactched to the global object (here global object is window). Hence, **Variables declared with var are globally scoped, which means that they can be accessed from anywhere in the JS program**.

```
//code example 4

{
  var a = 10;
  let b = 20;
  const c = 30;

  console.log(a);
  console.log(b);
  console.log(c);
}

  console.log(a);
  console.log(b); //error- will not print as b cannot be accessed out of block, so program will come and stop at this line
  console.log(c); //error- will not print as c cannot be accessed out of block
  
```
Outputs:

> 10

> 20

> 30

> 10

>  Uncaught ReferenceError: b is not defined

### __What is SHADOWING in JS?__

```
//code example 5

var a = 100;
{
    var a = 10; //same name as global var
    let b = 20;
    const c = 30;
    console.log(a); // 10
    console.log(b); // 20
    console.log(c); // 30 
}

console.log(a); // 10 instead of the 100 we were expecting. So block "a" modified val of global "a" as well. 
// In console, only b and c are in block space. a initially is in global space(a = 100), and when a = 10 line is run, a is not created in block space, but replaces 100 with 10 in global space itself. 
```

* If one has same named variable outside the block, the variable inside the block *shadows* the outside variable.
* So, a is reassigned to 10. Since both refers to same memory space i.e GLOBAL SPACE. **This happens only for var**

### Instead of var let us use let
```
//code example 6

let b = 100;
{
    var a = 10;
    let b = 20;
    const c = 30;
    console.log(b);
}

console.log(b);
```

Outputs:

> 20

> 100  // this was what we were expecting in this first place. Both b's are in separate spaces (one in Block(20) and one in Script(another arbitrary mem space)(100))

* In the Scope, we have b in two places. The b outside of the block is in *Script* SCOPE (seperate memory space for let and const)
* The b inside the block is in *Block* scope.
* Thus, when in Block scope, 20 is printed and 100 when outside.
* This concept is called "Shadowing".
* It is also true for *const* declarations.

### Same logic is true even for functions

```
const c = 100;
function x() {
  const c = 10;
  console.log(c);
}
x();
console.log(c);

```
Output:
> 10

> 100

### __What is Illegal Shadowing?__

```
// code example 7

let a = 20;
{
    var a = 20;
}

```

Outputs:

> Uncaught SyntaxError: Identifier 'a' has already been declared

* We cannot shadow let with var. But it is valid to shadow a let using a let.
* However, we can shadow var with let.
* All scope rules that work in function are same in arrow functions too.
* Since var is function scoped, it is not a problem with the code below.

```
// code example 8

let a = 20;
function x() {
    var a = 20;
}

```


