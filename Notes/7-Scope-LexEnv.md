# Episode 7 : Scope and Lexical Environment

```
(Case-1)

function a() {
//var b = 25;

    console.log(b); // surprisingly instead of printing not defined it prints 10. 
    //So somehow this b(present in local EC) could access the b outside the func.(present in GEC) 
}

var b = 10;
a();
```
> 10
---------------------
```
Another case: (Case-2)

function a() {
  c();
  function c() {
  console.log(b); // when cursor comes here, it still prints out 10 somehow!!
  }
 }
 var b = 10;
 a();
 
 //var b = 44;
 //console.log(b); 
 ```
 > 10
 --------------------
 ```
 Another one (DJ KHALED!) (Case-3)
 
 function a() {
  var b = 10;
  c();
  function c() {
    console.log("andar wala b - " + b); //it prints the right value. How? See ans below Summary part
  }
 }
 
 a();
 console.log(b); // now when cursor comes here, it prints NOT DEFINED!
```
> 10 <br/>
> b is not defined
 --------------------
 
- This is the intuition behind **scope**
- Scope is directly dependent on the lexical environment
- **Lexical Environment** : local memory + lexical env of its parent; so suppose c is a function inside function a and a is a function inside GEC, so  total memory of c =  local memory of c  + reference to the lexical environment of parent a and lexical environment of a = total memory of a = local memory of a + reference to the lexical environment of parent GEC
- Whenever an EC is created, a Lexical environment(LE) is also created and is referenced in the local EC(in memory space)
- Lexical means hierarchy. In the DJ KHALED (xD) code, function c is lexically inside function a. 
- So in EC of c() in the memory column- variables and func. in c (none) + reference of lexical env of parent a() is there 
i.e ***total memory of func. c = local memory of c (variables and func. in c (none)) + reference of lexical env of parent a()***
- LE of a() in turn is its memory space + reference to LE of parent (Global EC) i.e ***LE of a() = local memory of a (variables and func. in a) + reference to LE of parent (Global EC)***
- LE of parent (Global EC) in turn is its memory space + reference to LE of parent of Global EC i.e ***LE of parent (Global EC) = local memory of (Global EC) + reference to LE of parent of GEC***
- LE of parent of GEC points to *null* //because (Global EC) has no parent

 ```
    To summarize the above points:
    
    call_stack = [GEC, a(), c()]

    Now lets also assign the memory sections of each execution context in call_stack.

    c() = [[lexical environment pointer pointing to a()]]

    a() = [b:10, c:{}, [lexical environment pointer pointing to GEC]]

    GEC =  [a:{},[lexical_environment pointer pointing to null]]

 ```
  ### For Case-3 
  - First JS engine searches for b in local mem of c(). Nothing is there. 
  - So it goes to the reference of Lexical env of parent a(). Here b = 10 is here. So it takes this value, goes back to c() and console prints it.
  - Had b not been in a(), then pointer would have gone to a()'s parent (Global EC and searched there). Had b not been there too, then it goes to LE of global's parent
  which is null. Now JS engine stops and says b is NOT DEFINED. 
  - **Lexical env of c = Local memory of c + LE of A + LE of Global**
  - This process of going one by one to parent and checking is called **scope chain**
 --------------------
```
  Another Trial Example
 
function a() {
  var b = 2;
  c();

  function c() {
    //var b = 3;
  console.log(b);
  }
 }

 var b = 1;
 a();
```
> 2
 --------------------
  
  







