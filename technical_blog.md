<img src= "https://images.unsplash.com/photo-1556711240-9d578614d08e?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2070&q=80" width=100% height = 400px />
<h1 style=text-align:center>Two bits on this</h1>
<h6 style = text-align:right> by Gurupriyan Jayakaran </h6>
<br>

#### What is `this` ?
The `this` references the object of which the function is a property. In other words, the this references the object that is currently calling the function.
The keyword `this` in Javascript can be a little slippery to wrap your had around at first. Let's look at an analogy to understand what `this` is.

>Ann is a Software Developer and she teaches at Marcy Lab School.

In the above sentence, we use the pronoun "she" to refer to Ann rather than directly addressing her. Likewise, JavaScript uses `this` to refer to the object in context.<br>
Before starting, let's familiarize with a couple of terms:
- **Invocation** of a function is executing the code that makes the body of a function, or simply calling the function.
- **Execution Context** of an invocation is the value of this within function body.
- **Scope** of a function is the set of variables and functions accessible within a function body.

There are different way we can invoke a function 

#### **1) `this` in a function**
<iframe
  src="https://carbon.now.sh/embed?bg=rgba%28171%2C+184%2C+195%2C+1%29&t=seti&wt=none&l=auto&ds=true&dsyoff=62px&dsblur=68px&wc=true&wa=false&pv=20px&ph=25px&ln=true&fl=1&fm=Hack&fs=14px&lh=131%25&si=false&es=2x&wm=false&code=function%2520valueOfThis%2520%28%29%2520%257B%250A%2520%2520console.log%28this%29%253B%250A%257D%250A%250AvalueOFThis%28%29%253B%2520%252F%252Fwindow%2520object"
  style="width: 649px; height: 206px; border:0; transform: scale(1); overflow:hidden;"
  sandbox="allow-scripts allow-same-origin">
</iframe><br>
In the above code, function in not intialized inside the any object, so the parent object for the function in the window object. Thus, when you call the function `valueOfThis()` in line 5 it will print the window object in the console.<br>

#### **2) `this` in a method**<br>
<iframe
  src="https://carbon.now.sh/embed?bg=rgba%28171%2C+184%2C+195%2C+1%29&t=seti&wt=none&l=auto&ds=true&dsyoff=62px&dsblur=68px&wc=true&wa=false&pv=20px&ph=25px&ln=true&fl=1&fm=Hack&fs=14px&lh=131%25&si=false&es=2x&wm=false&code=const%2520methodExample%2520%253D%2520%257B%250A%2520%2520valueOfThis%2520%253A%2520function%2520%28%29%2520%257B%250A%2520%2520%2520%2520console.log%28this%29%253B%250A%2520%2520%257D%250A%257D%250A%250AmethodExample.valueOfThis%28%29%253B"
  style="width: 649px; height: 242px; border:0; transform: scale(1); overflow:hidden;"
  sandbox="allow-scripts allow-same-origin">
</iframe><br>
Methods are functions that are defined inside an object. In the above code, the method `valueOfThis` resides inside the object `methodExample`. So when we invoke the method in line 7, we are calling the function inside the object with the dot notation, so the function will print the objecy `valueOfThis` since the method lives inside this object and not the window object.<br>

#### **3) `this` in a constructor**<br>
<iframe
  src="https://carbon.now.sh/embed?bg=rgba%28171%2C+184%2C+195%2C+1%29&t=seti&wt=none&l=auto&ds=true&dsyoff=62px&dsblur=68px&wc=true&wa=false&pv=20px&ph=25px&ln=true&fl=1&fm=Hack&fs=14px&lh=131%25&si=false&es=2x&wm=false&code=class%2520constructorExample%2520%257B%250A%2520%2520constructor%2520%28name%252C%2520age%29%2520%257B%250A%2520%2520%2520%2520this.name%2520%253D%2520name%253B%250A%2520%2520%2520%2520this.age%2520%253D%2520age%253B%250A%2520%2520%257D%250A%2520%2520valueOfThis%2520%28%29%2520%257B%250A%2520%2520%2520%2520console.log%28this%29%253B%250A%2520%2520%257D%250A%257D%250A%250Aconst%2520person1%2520%253D%2520new%2520constructorExample%28%2522GP%2522%252C%252023%29%253B%250Aperson1.valueOfThis%28%29%253B%2520%252F%252F%2520prints%2520the%2520object%2520with%2520%2522GP%2522%2520as%2520name%250Aconst%2520person2%2520%253D%2520new%2520constructorExample%28%2522Mo%2522%252C%252022%29%253B%250Aperson2.valueOfThis%28%29%253B%2520%252F%252F%2520prints%2520the%2520object%2520with%2520%2522Mo%2522%2520as%2520name"
  style="width: 649px; height: 371px; border:0; transform: scale(1); overflow:hidden;"
  sandbox="allow-scripts allow-same-origin">
</iframe><br>
Here we are creating an instance of the object in different variables using `class`. In line 2, the role of the constructor function is to initialize the instance. A constructor call creates a new empty object, which inherits properties from the constructor's prototype. In line 11 and 13, we are creating two instances of the prototype object and `this` refers to the individual object rather that the `class constructorExample`. Thus, it prints two objects with different object property values.<br>

#### **Strict vs Non-strict mode**<br>
In the JavaScript, the global object is always the `window` object and when a function in defined and invoked inside the `window` object, `this` always refers to the `window` object unless we use strict mode.<br>

<iframe
  src="https://carbon.now.sh/embed?bg=rgba%28171%2C+184%2C+195%2C+1%29&t=seti&wt=none&l=auto&ds=true&dsyoff=62px&dsblur=68px&wc=true&wa=false&pv=20px&ph=25px&ln=true&fl=1&fm=Hack&fs=14px&lh=131%25&si=false&es=2x&wm=false&code=function%2520valueOfThis%2520%28%29%2520%257B%250A%2520%2520%27use%2520strict%27%253B%250A%2520%2520console.log%28this%29%250A%257D%250A%250AvalueOfThis%28%29%253B%2520%252F%252Fundefined"
  style="width: 649px; height: 224px; border:0; transform: scale(1); overflow:hidden;"
  sandbox="allow-scripts allow-same-origin">
</iframe><br>
In the above code, the strict mode in line 2 affects the execution context, making this to be undefined in a regular function invocation. The execution context is not the global object anymore.<br>

#### **Why `this` doesn't work in arrow functions like we expect?**<br>
arrow functions are designed to declare function in a shorter form. Unlike the other syntaxes of making a function, declaring a function using the arrow syntax does not make its own execution context, so it borrows the context from its parent object.<br>

<iframe
  src="https://carbon.now.sh/embed?bg=rgba%28171%2C+184%2C+195%2C+1%29&t=seti&wt=none&l=auto&ds=true&dsyoff=62px&dsblur=68px&wc=true&wa=false&pv=20px&ph=25px&ln=true&fl=1&fm=Hack&fs=14px&lh=131%25&si=false&es=2x&wm=false&code=const%2520valueOfThis%2520%253D%2520%28%29%2520%253D%253E%2520%257B%250A%2520%2520console.log%28this%29%253B%250A%257D%250A%250AvalueOfThis%28%29%253B%2520%252F%252Fprints%2520the%2520window%2520object%250A%250Aconst%2520object%2520%253D%2520%257B%250A%2520%2520methodThis%2520%253A%2520%28%29%2520%253D%253E%2520%257B%250A%2520%2520%2520%2520console.log%28this%29%250A%2520%2520%257D%250A%257D%250Aobject.methodThis%28%29%253B%2520%252F%252Fprints%2520thw%2520window%2520object"
  style="width: 649px; height: 334px; border:0; transform: scale(1); overflow:hidden;"
  sandbox="allow-scripts allow-same-origin">
</iframe><br>

The above code logs two `window` objects in the console. Because inside the object in line 7, we are declaring a method using the arrow function syntax, so instead of `this` referring to the `example` object, it inherits the execution context from a step above the object, thus `this` becoming the `window` object.<br>

Hope the confusion regarding the keyword `this` has been cleared. Happy coding!!