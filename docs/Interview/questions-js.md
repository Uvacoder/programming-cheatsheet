# Interview - JS

Javascript is a scripting, prototype based, dynamic typing language.

Senior powinien myśleć na poziomie całego projektu a nie pojedynczej funkcji.

clean code
paradygmaty
architektura
wzorce projektowe
złożoność obliczeniowa
jakiego algorytmu/biblioteki użyć

[Dispatching custom events](https://javascript.info/dispatch-events)

???
- Programowanie funkcyjne a programowanie obiektowe?
- What is the Difference Between Class and Prototypal Inheritance?
- Asynchronous: Promises, async/await
- What is Server Side Rendering? Why do we need it?
- Why Google crawlers are unable to crawl Client Side Rendered applications?
- How does browser renders HTML on screen?
- Rodzaje komponentów
- revealing module pattern
- jak można zmienić kontekst wywołania funkcji?
- [!] What is closure? Examples. When we define variable in internal function, is it visible in the scope above?
  -	są to funkcję które mają dostęp do zmiennych na zewnątrz,
  -	funkcja wewnętrzna ma dostęp do swoich zmiennych oraz w blokach nadrzędnych,
  -	parent funkcji nie ma dostępu do zmiennych funkcji wewnątrz jego bloku,
  -	użyteczne aby uzyskac cos na ksztalt zmiennych prywatnych, co zabezpiecza dane
- What is a Promise?
- What is npm?
- Service Worker API
- convert nodeList to Array
- FOUC
- BABEL jak działa
- js throttle
- Typescrtipt
- anonymous functions
- functional/block scope
- Data structures
???

## Concepts

- Closure
- Prototypes
- Prototype and Prototype Chain

### JS Methods

- document
  - querySelector('css-selector')

- Object
    - keys
    - defineProperty
    `Object.defineProperty(obj, 'x', {
      value : '1'
     }); `
    - values
    - entries
    `const [key, value] = Object.entries(elemens);`
        - Object.entries(obj)
        - Object.fromEntries(array)
    - for...of
    `for (const [key, value] of Object.entries(elements))`

- Loops
    - for...of (for (const [key, value] of Object.entries(elements)) {)

- Coercion
    - to Number (Number(...))
    - to String (String(...))

- Array
    - sort
    - join
    - split
    - concat
    - splice (if we add 0 as second param then it is insert)
    - filter
    - arr.length
    - reduce
    - indexOf
    - push/pop
    - shift/unshift
    - reverse

- String
    - String()
    - split
    - indexOf
    - lastIndexOf

- Number
    - Number()

- two array diff
https://stackoverflow.com/questions/1187518/how-to-get-the-difference-between-two-arrays-in-javascript

### Functional Programming in JS

[6 fundamental terms in functional JavaScript - Frontend Weekly - Medium](https://medium.com/front-end-weekly/6-fundamental-terms-in-functional-javascript-e25d50d40b2c)
In javascript there are 6 fundamental terms:
  - Arrow Functions
  - First-class function
  - Hight-order function
  - Unary function
  - Currying
  - Pure Functions

[YouTube](https://www.youtube.com/watch?v=e-5obm1G_FY)

#### Arrow Functions (Lambda)

One obvious benefit of arrow functions is to simplify the syntax needed to create functions, without a need for the function keyword. The this within arrow functions is also bound to the enclosing scope which is different compared to regular functions where the this is determined by the object calling it. Lexically-scoped this is useful when invoking callbacks especially in React components.

Lambda expressions are the cornerstone of functional programming. If it helps you, just think of them as a new shorter syntax for your functions. However, be careful about using them in your objects or classes as they use lexical this.

```js
// this is your regular named function in JavaScript
function namedFunction (a, b) {
  return a + b;
}
// this is a lambda, i.e. an arrow function
const lambda = (a, b) => a + b;
```

Without arrow functions, every function defines a this value. No more will you need to reassign this.

#### First-class function

First-class type means simply, that the type can be used as a value of a variable. A string is a first-class type as well as a function is a first-class type in JavaScript and so your functions can accept other functions as their arguments and return functions as their return values.

You have already been using functions as first class when assigning handlers to listeners:

```js
const handler = () => console.log ('I am function');

document.addEventListener ('click', handler);

```

#### Hight-order function

Higher-order function is a function that accepts other function as an argument or returns a function as a return value.

First-order function is a function that doesn’t accept other function as an argument and doesn’t return a function as its return value.

```js
const firstOrder = () => console.log ('First order strikes back!');

const higherOrder = whoStrikesBack => whoStrikesBack ();
higherOrder (firstOrder);
```

#### Unary function

The term relates to arity of a number of arguments accepted by a function. Unary function (i.e. monadic) is a function that accepts exactly one argument.

```js
const unaryFunction = message => console.log (message);

const binaryFunction = (color, message) =>
  console.log (`%c${message}`, `color:${color}`);

const ternaryFunction = (fnc, color, message) =>
  fnc (`%c${message}`, `color:${color}`);
```

#### Currying

Currying is the process of taking a function with multiple arguments and turning it into a sequence of functions each with only a single argument. This technique can be useful for making code written in a functional style easier to read and compose. Therefor with currying you take a n-ary function and you turn it into a unary function:

```js
const binaryFunction = (a, b) => a + b;
const curryUnaryFunction = a => b => a + b;
curryUnaryFunction (1); // returns a function: b => 1 + b
curryUnaryFunction (1) (2); // returns the number 3
```

Curried functions are great to improve code reusability and functional composition.

[JavaScript ES6 curry functions with practical examples \| by Martin Novák | Frontend Weekly | Medium](https://medium.com/front-end-weekly/javascript-es6-curry-functions-with-practical-examples-6ba2ced003b1)

#### Pure Functions

A pure function is a function where the return value is only determined by its arguments without any side effects.

That means that if you give a pure function the same argument a hundred times in a hundred different places of your whole application, the function will always return the same value. No external states will be changed or read by the pure function.

```js
let myArray = [];

const impureAddNumber = number => myArray.push (number);

const pureAddNumber = number => anArray =>
  anArray.concat ([number]);

console.log (impureAddNumber (2)); // returns 1
console.log (myArray); // returns [2]
console.log (pureAddNumber (3) (myArray)); // returns [2, 3]
console.log (myArray); // returns [2]
myArray = pureAddNumber (3) (myArray);
console.log (myArray); // returns [2, 3]
```

Push function is impure itself and it alters the array it is called on and as such produces a side effect. The return value of push is a number index.

Concat on the other hand takes the array and concatenates it with the other array producing a whole new array without side effects. The new array as concatenation of the previous array is then returned.

Pure functions are important as they simplify unit testing (no side effects and no need for dependency injection), they avoid tight coupling and by removing side effects, they make your application harder to break.

[8 steps to turn imperative JavaScript class to a functional declarative code \| by Martin Novák | Frontend Weekly | Medium](https://medium.com/front-end-weekly/8-steps-to-turn-imperative-javascript-class-to-a-functional-declarative-code-862964faf46c)

### Immutability - Side Effects - Immutable objects

> A `pure function` produces no `side effects`, which means that it can’t alter any external state. JavaScript’s object arguments are references, which means that if a function were to mutate a property on an object or array parameter, that would mutate state that is accessible outside the function. Pure functions must not mutate external state.

- Mutable

```js
const addToCart = (cart, item, quantity) => {
  cart.items.push({
    item,
    quantity
  });
  return cart;
};
```

- Immutable

```js
const addToCart = (cart, item, quantity) => {
  const newCart = lodash.cloneDeep(cart);

  newCart.items.push({
    item,
    quantity
  });
  return newCart;

};
```
[Master the JavaScript Interview: What is a Pure Function?](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-pure-function-d1c076bec976)

### Execution Context

Is the "environment of code" that is currently executing. The Execution Context has two phases compilation and execution.

**Compilation** - in this phase it gets all the function declarations and hoists them up to the top of their scope so we can reference them later and gets all variables declaration (declare with the var keyword) and also hoists them up and give them a default value of undefined.

**Execution** - in this phase it assigns values to the variables hoisted earlier and it executes or invokes functions (methods in objects).

```js
console.log(y);
y = 1;
console.log(y);
console.log(greet("Mark"));

function greet(name) {
  return 'Hello ' + name + '!';
}

var y;

// AFTER COMPILATION:

function greet(name) {
  return 'Hello ' + name + '!';
}
var y; //implicit "undefined" assignment
//waiting for "compilation" phase to finish
//then start "execution" phase
console.log(y);
y = 1;
console.log(y);
console.log(greet("Mark"));
```

### Hoisting (var, let, const)

> Hoisting is the concept where Javascript moves all declarations to the top of the current scope. As such, a variable can be used before it has been declared. There are two types of hoisting:
1. variable hoisting - rare
2. function hoisting - more common

Note that Javascript only hoists declarations and not initializations.

`let` and `const` behave the same in terms of scope, both being block scoped . On the other hand, `var` behaves differently by being function scoped, meaning `var` declarations inside a block scope will also be available to the nearest outer function block.

- use function before declare
using function before is more common practice and names `function hoisting`

- use variable before declare

`var` shows undefined
`const` and `let` shows and error 'Cannot access ... before initialization'

- declaring variable multiple times

`var` can be declared multiple times.
`let` shows an error 'Identifier .. has already been declared'
we can not redeclare `const` and `let` varaibles

- redefine variable

we can not redefine `const` variable shows an error TypeError: Assignment to constant variable
but we can redefine `var` and `let` variable

```js
// Function Declaration
hoisted(); // Output: "This function has been hoisted."
function hoisted() {
  console.log('This function has been hoisted.');
};

// Function Expression
expression(); // Output: "TypeError: expression is not a function
var expression = function() {
  console.log('Will this work?');
};

// Combination of a function declaration and expression
expression(); // Ouput: TypeError: expression is not a function
var expression = function hoisting() {
  console.log('Will this work?');
};
```

```js
var x = function () {
    return a;
    var a = 1;
    function a() {
        return 'hello';
    }
};

console.log(x()()); // hello
```

```js
function hoist() {
  console.log(message);
  var message='Hoisting is all the rage!'
}

// Is visible for interpreter as:

function hoist() {
  var message;
  console.log(message);
  message='Hoisting is all the rage!'
}
```

```js
// Variable assignment over function declaration
var double = 22;
function double(num) {
  return (num*2);
}
console.log(typeof double); // Output: number

// Function declarations over variable declarations
var double;
function double(num) {
  return (num*2);
}
console.log(typeof double); // Output: function
```

[front-end-interview-handbook/javascript-questions.md at master · yangshun/front-end-interview-handbook · GitHub](https://github.com/yangshun/front-end-interview-handbook/blob/master/contents/en/javascript-questions.md#explain-hoisting)

### Scope

Each function gets its own scope. Scope is basically a collection of variables as well as the rules for how those variables are accessed by name. Only code inside that function can access that function's scoped variables.

A variable name has to be unique within the same scope. A scope can be nested inside another scope. If one scope is nested inside another, code inside the innermost scope can access variables from either scope.

We have:
- global scope
- function scope
- block scope


- block scope vs function scope

`var` has a function scope and can be visible
```js
for (var i = 0; i < 10; i++) {
  var saySomething = 'yeah!';
}
console.log(i); // 10
console.log(saySomething); // yeah!
```

`let` and `const` have a block scope and they are not visible outside of scope
```js
for (let i = 0; i < 10; i++) {
    let saySomething = 'yeah!';
}
console.log(i); // ReferenceError: i is not defined
console.log(saySomething); // ReferenceError: saySomething is not defined
```

<!-- ![Zrzut ekranu 2020-06-26 o 00.37.49.png](:storage/283dbcd3-dac7-41f5-8c4c-83739bcb6319/904828d0.png) -->

[GitHub - kennymkchan/interview-questions-in-javascript: A mostly reasonable collection of technical software development interview questions solved in Javascript](https://github.com/kennymkchan/interview-questions-in-javascript#javascript--hosting)
[30secondsofcode - javascript-variable-scope](https://www.30secondsofcode.org/blog/s/javascript-variable-scope)

### ES6 Features - ECMAScript 6
[!] **Favourite es6 features**

ES6 or ECMAScript 6 or ECMAScript 2015 is a set of rules (standard) designed by Ecma International. The names "JavaScript" and "ECMAScript" are essentially different names for the same thing.

#### Versions:
(...)
5.1	June 2011		This edition 5.1 of the ECMAScript standard is fully aligned with third edition of the international standard ISO/IEC 16262:2011
6	June 2015	ECMAScript 2015 (ES2015)	See 6th Edition – ECMAScript 2015
7	June 2016	ECMAScript 2016 (ES2016)	See 7th Edition – ECMAScript 2016
8	June 2017	ECMAScript 2017 (ES2017)	See 8th Edition – ECMAScript 2017
9	June 2018	ECMAScript 2018 (ES2018)	See 9th Edition – ECMAScript 2018
10	June 2019	ECMAScript 2019 (ES2019)	See 10th Edition – ECMAScript 2019
11	June 2020	ECMAScript 2020 (ES2020)	See 11th Edition – ECMAScript 2020

#### ES6 Features:
- classes and class declaration
- arrow function expressions
- modules imports/exports
- block scoping (`let` keyword for local declaration)
- promises
- spread operator
- strict mode
- iterators
- for...of
- generators
- `const` keyword for constant local declaration
- template literals
- typed arrays
- maps, sets, WeakMap
- math enhancements
- reflection
- proxies

##### Classes and class declaration

ES6 introduces language support for classes (class keyword), constructors (constructor keyword), and the extend keyword for inheritance.  The developer’s intent is much more clear using the ES6 syntax.

##### Arrow function expressions

Arrow functions provide two features: lexical scoping of the this keyword and less ceremony when defining an anonymous function.

Without arrow functions, every function defines a this value.

##### Modules imports/exports

It is a way to load and manage dependencies via the new `import` and `export` keywords.

- refactoring from global code to modular code
- fast compilation
- simplicity and usability
- standardized protocol for sharing libraries
- compatibility with browser and non-browser environments
- easy asynchronous external loading

`require` is based on the commonjs module (cjs) specifications. because this is implemented by node, you can use it in node. however, the browser does not understand require at all, so you cannot use it in the browser.

##### Block scoping

In ES6, you can use the new let keyword to achieve block scoping. Related with hoisting subject.

```js
var num = 0; //globally scoped

for (let i = 0; i < 10; i++) { //i is block scoped
  num += i;
  console.log('value of i in block: ' + i);
}

console.log('Is i defined here?: ' + (typeof i !== 'undefined')); //Is i defined here?: false
```

##### Promises

Mechanism to handle the results and errors from asynchronous operations. You can accomplish the same thing with callbacks, but promises provide improved readability via method chaining and succinct error handling.

[5 Great Features in EcmaScript 6 (ES6 Harmony) - Wintellect](https://www.wintellect.com/5-great-features-in-es6-harmony/)

##### Spread Operator

Spread syntax effectively goes one level deep while copying an array (it's the same with Object.assign()).

Expand an iterable object into the list of arguments. Can also:

- Copying an array
- Concatenating or combining arrays
- Using Math functions
- Using an array as arguments
- Adding an item to a list
- Adding to state in React
- Combining objects
- Converting NodeList to an array


```js
function sum(x, y, z) {
  return x + y + z;
}

const numbers = [1, 2, 3];

console.log(sum(...numbers));
// expected output: 6

console.log(sum.apply(null, numbers));
// expected output: 6
```

#### Strict Mode

```js
'use strict';
```

JavaScript was designed to be easy for novice developers, and sometimes it gives operations which should be errors non-error semantics. Strict mode makes it easier to write "secure" JavaScript.

It intentionally has different semantics from normal code and converting mistakes into errors. Strict mode makes several changes to normal JavaScript semantics:

- eliminates some JavaScript silent errors by changing them to throw errors
- can sometimes be faster than identical code that's not strict mode
- prohibits some syntax likely to be defined in future versions of ECMAScript

**Examples:**
- makes it impossible to accidentally create global variables, setting a value to an undeclared variable

```js
// ReferenceError: mistypeVariable is not defined
'use strict';
mistypeVariable = 17;
```

```js
function foo(arg) {
    bar = "this is a hidden global variable";
}
// or
function foo() {
    this.variable = "potential accidental global";
}
// is in fact
function foo(arg) {
    window.bar = "this is an explicit global variable";
}
```

- duplications of property names

```js
'use strict';
var o = {
  p: 1,
  p: 2
};
```

- unique functions parameters names

```js
// SyntaxError: Duplicate parameter name not allowed in this context
function sum(a, a, c) { // !!! syntax error
  'use strict';
  return a + a + c; // wrong if this code ran
}
```

- forbids setting properties on primitive values

```js
(function() {
  'use strict';

  false.true = '';         // TypeError
  (14).sailing = 'home';   // TypeError
  'with'.you = 'far away'; // TypeError
})();
```

- using delete on a variable name delete myVariable

```js
//SyntaxError: Delete of an unqualified identifier in strict mode
'use strict';
var variableName = '';
delete variableName;
```

- Octal syntax var n = 023;
- Using eval or arguments as variable or function argument name
- Using one of the newly reserved keywords (in prevision for ECMAScript 2015): implements, interface, let, package, private, protected, public, static, and yield
- `this` in function calls:
In function calls like f(), the this value was the global object. In strict mode, it is now undefined. When a function was called with call or apply, if the value was a primitive value, this one was boxed into an object (or the global object for undefined and null). In strict mode, the value is passed directly without conversion or replacement.

```js
var global = this; // in the top-level context, "this" always
                   // refers to the global object
function f(x) {
  'use strict';
  var a = 12;
  global.b = a + x * 35;
}
f(42);
```

## Questions

**What is Vanilla JS?**

Using "VanillaJS" means using plain JavaScript without any additional libraries like jQuery.

**What is a Function?**

It is a process which takes some input, called arguments, and produces some output called a return value.
    - Mapping: Produce some output based on given inputs. A function maps input values to output values.
    - Procedures: A function may be called to perform a sequence of steps. The sequence is known as a procedure, and programming in this style is known as procedural programming.
    - I/O: Some functions exist to communicate with other parts of the system, such as the screen, storage, system logs, or network.

---

### Typical use cases for anonymous functions?

- `IIFE` - They can be used in IIFEs to encapsulate some code within a local scope so that variables declared in it do not leak to the global scope.

```js
(function () {
  // Some code here.
})();
```

- `Callbacks` - where name is not needed and code is clear

```js
setTimeout(function () {
  console.log('Hello world!');
}, 1000);
```

- `Functional programming`

```js
const arr = [1, 2, 3];
const double = arr.map(function (el) {
  return el * 2;
});
console.log(double); // [2, 4, 6]
```

### Difference between host objects and native objects?

Native objects are objects that are part of the JavaScript language defined by the ECMAScript specification, such as String, Math, RegExp, Object, Function, etc.

Host objects are provided by the runtime environment (browser or Node), such as window, XMLHTTPRequest, etc.

### What is AJAX?

Ajax (asynchronous JavaScript and XML). The XMLHttpRequest API is frequently used for the asynchronous communication or these days, the fetch API. With Ajax, web applications can send data to and retrieve from a server asynchronously (in the background) without interfering with the display and behavior of the existing page.

### What is Pure Function?

[Master the JavaScript Interview: What is a Pure Function?](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-pure-function-d1c076bec976)
Functions should pass principle from KISS design pattern (Keep It Simple, Stupid).
Special type of functions, which cover cases:
  - for given the same input, will always return the same output
  - produces no side effects
  - arguments are fully determined before any output is generated
  - are completely independent of outside state, and as such, they are immune to entire classes of bugs that have to do with shared mutable state.
  - easy to move around
  - refactor, and reorganize in your code
  - making your programs more flexible and adaptable to future changes
  - `Math.random()` is not pure.

---

**What is a coersion?**

`Corecion` - another name for type conversion types in JS.

`Implicit Coercion` Type conversion is done implicitly by JavaScript.
`Explicit Coercion` Type conversion is done explicitly in code using the inbuilt functions like Number(), String(), Boolean(), etc.

```js
var a = "42";
var a1 = Number(a);

console.log( a ); // "42"
console.log( a1 ); // 42

var b = 42;
var b1 = String(b);

console.log( b ); // 42
console.log( b1 ); // "42"
```

---

**[!] What is the difference between =, ==, === ?**

Equality

```js
/**
==  (loose-equals - double equals)
=== (strict-equals - triple equals - identity)
!=  (loose not-equals)
!== (strict not-equals)
*/
```

We cannot say that `double equals` check values and `triple equals` check values and types, because it is wrong answer. Correct answer is first one `allow coresion` and can equal different types (`abstract`) and second one `disallow coercion` can equal only the same types (`strict`).

[Javascript : The Curious Case of Null >= 0 \| by Abinav Seelan | campvanilla](https://blog.campvanilla.com/javascript-the-curious-case-of-null-0-7b131644e274)
[ECMAScript Spec: 11. Expressions](http://interglacial.com/javascript_spec/a-11.html#a-11.9.3)

---

**[!] Explain the usage of bind, call, apply.**

All functions are used to override value of `this` word within the function scope using passed object.

`bind` return new function which should be called below
`apply` call function with usage of apple and arguments passed to function should be located as second parameter in array
`call` works like apply but passed parameters should be a separated arguments

```js
var vehicle = {
  name: 'BMW',
  model: '1M'
}

function showVehicleName(freeToRent) {
  console.log(`${this.vehicle.name} ${this.vehicle.model} - ${freeToRent}`);
}

const newVehicle = {
  vehicle: {
    name: 'Mercedes',
    model: 'SLS'
  }
}

var isVehicleFree = 'yes';
showVehicleName(isVehicleFree); //BMW 1M - false
const bindFunction = showVehicleName.bind(newVehicle, isVehicleFree);
bindFunction(); //Mercedes SLS - false
showVehicleName.apply(newVehicle, [isVehicleFree]); //Mercedes SLS - false
showVehicleName.call(newVehicle, isVehicleFree); //Mercedes SLS - false
```

### What means `this` word and what is this?

`this` is a reference to current execution context.

`this` is the current execution context
 - window (browsers)
 - global (node.js)

`this` is reference to object where function is comming from. In arrow function is global or undefined in stict mode.

  -	jeżeli wywołano funkcję ze słowem new this odnosi się do nowo utworzonego obiektu,
  -	jeżeli zostało użyte jedno z apply, call lub bind zostało użyte do wywołania funkcji, this odnosi się do funkcji przekazanej jako argument,
  -	jeżeli funkcja została zdefiniowana w obiekcie i użyta poprzez zapis obiekt.funkcja() this odnosi się do obiektu który zdefiniował funkcję,

### IIFE - Immediately invoked function expression

The function is executed right after it's created, not after it is parsed. The entire script block is parsed before any code in it is executed. Also, parsing code doesn't automatically mean that it's executed, if for example the IIFE is inside a function then it won't be executed until the function is called.

Using it allow us encapsulate bunch of scope and change scope of functions. Protect outside of scope.

```js
// Using regular function

(function() {
  'use strict';
}());

// Using arrow function

((foo) => {
  'use strict';
})('foo value')
```


---

### [!] Object.freeze vs const - difference

`const` applies to bindings ("variables"). It creates an immutable binding, i.e. you cannot assign a new value to the binding.

`Object.freeze` works on values, and more specifically, object values. It makes an object immutable, i.e. you cannot change its properties. Doesn't work on primitives types,

### Difference between `Object.preventExtensions()`, `Object.seal()` and `Object.freeze()`

`Object.preventExtensions()` - If you want to prevent an object from having new properties added to it, but otherwise leave the rest of the object's properties alone.

`Object.seal()` - It essentially calls Object.preventExtensions() on it, but also marks all its existing properties as configurable: false. So, not only can you not add any more properties, but you also cannot reconfigure or delete any existing properties (though you can still modify their values).

`Object.freeze()` - It prevents any changes to the object or to any of its direct properties. It takes an existing object and essentially calls Object.seal() on it, but it also marks all "data accessor" properties as writable:false. Freezing an object does not allow new properties to be added to an object and prevents from removing or altering the existing properties.

---

**HOC High Order Functions**
  -	funkcja która przyjmuje inna funkcje jako parametr lub zwraca inna funkcje,
  -	przykłady z js. np. map, reduce, filter, forEach,
  -	łatwiejsze do testowania

---

**Progressive enhancement**
  -	poświęcenie wykorzystania nowych technologii na rzecz działania na starszych urządzeniach, następnie dodanie opcjonalnych rozszerzeń na węższe grono urządzeń/przeglądarek

---

**Graceful degradation**
  -	wykorzystanie nowych technologii podczas tworzenia aplikacji,
  -	następnym etapem jest dostosowanie do starszych przeglądarek/urządzeń,
  -	przykład: youtube i filmy wyświetlane w html5 w nowych przeglądarkach oraz flash w starszych

---

**Dziedziczenie (Prototype a proto)**

  Prototype a proto (Właściwość prototype obiektu function wskazuje inny obiekt. Ma ona znaczenie tylko, jeśli funkcja jest wywoływana jako konstruktor. Wszystkie obiekty utworzone za pomocą funkcji przechowują referencję do właściwości prototype i mogą korzystać z jej właściwości jak z własnych. JavaScript jest prototypowym językiem obiektowym. Funkcje w języku JavaScript są obiektami  osiadającymi właściwości i metody. Niektóre z nich już znasz, na przykład metody apply() i call() oraz właściwości length i constructor. prototype jest kolejną właściwością obiektu Function. W JavaScripcie obiekty są przekazywane przez referencję, więc prototype nie jest kopiowany z każdą nową instancją obiektu. Co to oznacza w praktyce? Oznacza to, że można modyfikować prototype w dowolnym momencie, a wszystkie obiekty, nawet te utworzone wcześniej, dostrzegą te zmiany. )

[Inheritance and the prototype chain - JavaScript \| MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)

---

**Notacja (w programowaniu)**

Jest umownym sposobem zapisu nazw: stałych, zmiennych, metod, klas itp. Notacja ta ma na celu stosowanie się do określonych uniwersalnych zasad, aby kod programu, był uniwersalnie dla każdego przejrzysty i zrozumiały. W naszej grupie, przyjęliśmy mieszaninę dwóch notacji. CamelCase oraz notację węgierską.
https://github.com/gelldur/Kino-Time-Tracker/wiki/Notacje-(w-programowaniu)

---

**What is Function Composition?**
-	sposób pisania kodu - pisanie funkcji która posiada one job only
-	następnie tworzenie bardziej skomplikowanych funkcji na podstawie wcześniej zdefiniowanych podstawowych funkcji
-	kod latwo testowalny
-	glownie chodzi o rozdzielenie funkcji synchronicznych od asynchronicznych

---

**[!] What is hoisting in JS? Key word this**
  -	jeżeli wywołano funkcję ze słowem new this odnosi się do nowo utworzonego obiektu,
  -	jeżeli zostało użyte jedno z apply, call lub bind zostało użyte do wywołania funkcji, this odnosi się do funkcji przekazanej jako argument,
  -	jeżeli funkcja została zdefiniowana w obiekcie i użyta poprzez zapis obiekt.funkcja() this odnosi się do obiektu który zdefiniował funkcję,

**Memory Management | Garbage collector | Memory leaks**

```js
function makeABigObject() {
  var bigArray = new Array(20000);
}

[Avoiding Memory Leaks in Node.js: Best Practices for Performance \| AppSignal Blog](https://blog.appsignal.com/2020/05/06/avoiding-memory-leaks-in-nodejs-best-practices-for-performance.html)
```

When you call that function, the JScript component creates an object (named bigArray) that is accessible within the function. As soon as the function returns, though, you "lose track" of bigArray because there's no way to refer to it anymore. Well, the JScript component realizes that you've lost track of it, and so bigArray is cleaned up--its memory is reclaimed.

JavaScript's objects are garbage collected periodically when there are no references remaining to the object. It is something that happens automatically, but if you want to see more about how it works, at the C++ level.

Types of memory leaks:
- Accidental global variables
- Forgotten timers or callbacks
- Out of DOM references
- Closures

[Understanding JavaScript Memory Management using Garbage Collection \| by Kewal Kothari | Frontend Weekly | Medium](https://medium.com/front-end-weekly/understanding-javascript-memory-management-using-garbage-collection-35ed4954a67f)

[4 Types of Memory Leaks in JavaScript and How to Get Rid Of Them](https://auth0.com/blog/four-types-of-leaks-in-your-javascript-code-and-how-to-get-rid-of-them/)

[Avoiding Memory Leaks in Node.js: Best Practices for Performance \| AppSignal Blog](https://blog.appsignal.com/2020/05/06/avoiding-memory-leaks-in-nodejs-best-practices-for-performance.html)

---

**Concurrency model**

JavaScript has a concurrency model based on an event loop, which is responsible for executing the code, collecting and processing events, and executing queued sub-tasks.

---

### Closure

A closure is the combination of a function and the lexical environment within which that function was declared. The word "lexical" refers to the fact that lexical scoping uses the location where a variable is declared within the source code to determine where that variable is available. Closures are functions that have access to the outer (enclosing) function's variables—scope chain even after the outer function has returned.

Using for:
- Data privacy / emulating private methods with closures. Commonly used in the module pattern.
- Partial applications or currying.

### [!] Concurency model

Responsible for executing code, collecting events, processing events, executing queued sub-tasks.

Examples of practise work:
- add variable to memory
- create execution context
- run code
- return value of function to global context

Elements:

- Heap
- Callback Queue
- Event Loop
- Job Queue

[Understanding Event Loop, Call Stack, Event & Job Queue in Javascript \| by Rahul Sagore | Medium](https://medium.com/@Rahulx1/understanding-event-loop-call-stack-event-job-queue-in-javascript-63dcd2c71ecd)

#### Heap

This is where V8 stores objects or dynamic data. This is the biggest block of memory area and it’s where Garbage Collection(GC) takes place.

#### Call Stack

JS keep track of what function is currently runnig (where is the thread of execution).

This is where static data, including method/function frames, primitive values, and pointers to objects are stored. This space is managed by the operating system (OS).

##### Execution context

Has 2 parts:
- `thread of execution` (ability to go throught the code line by line and do it)
- `memory` (storage for variables, functions, constants)

##### Callback Queue (macrotasks) (task queue)

Can be run for:
- `setTimeout()``

##### Job Queue (microtasks) (job queue)

Can be run for:
- `queueMicrotask()`
- promises handlers

#### [!] Event Loop

FIFO

The event loop is a single-threaded loop that monitors the call stack and checks if there is any work to be done in the task queue. If the call stack is empty and there are callback functions in the task queue, a function is dequeued and pushed onto the call stack to be executed.

To better understand event loop we should present two terms:
- macrotask (use zero delayed setTimeout(f))
- microtask (use queueMicrotask(f) or promise handlers)

Algorihm of event loop:
1. Dequeue and run the oldest task from the macrotask queue (e.g. “script”).
2. Execute all microtasks:
- While the microtask queue is not empty:
- Dequeue and run the oldest microtask.
3. Render changes if any.
4. If the macrotask queue is empty, wait till a macrotask appears.
5. Go to step 1.

There’s no UI or network event handling between microtasks: they run immediately one after another.

For long heavy calculations that shouldn’t block the event loop, we can use Web Workers. Web Workers can exchange messages with the main process, but they have their own variables, and their own event loop. Web Workers do not have access to DOM, so they are useful, mainly, for calculations, to use multiple CPU cores simultaneously. A web worker or a cross-origin iframe has its own stack, heap, and message queue.

Immediately after every macrotask, the engine executes all tasks from microtask queue, prior to running any other macrotasks or rendering or anything else.

There is a popular saying:
> Keep every promise you make and only make promises you can keep.

  -	przy wywołaniu funkcje zostaną dodane do call stack i usuwane z niego gdy zwraca wartość,
  -	web api pozwala na opóźnienie wykonania zadań bez blokowania wykonywania innych, tak jak np. setTimeout [warto dodać przykład z setTimeout na 0 i wyjaśnienie dlaczego nie wykona sie natychmiast]
  -	po zakończeniu (np timera w setTimeout) funkcja została dodana do queue, gdzie funkcje oczekuje na połączenie przez event loopa do call stacku
  -	jeżeli wszystkie funkcje w call stacku zostaną wywołane, funkcje z queue zostają przeniesione do call stack przez event loop

[Concurrency model and the event loop - JavaScript \| MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop)
[The JavaScript Event Loop](https://flaviocopes.com/javascript-event-loop/#:~:text=The%20call%20stack%20is%20a,executes%20each%20one%20in%20order.)
[YouTube - Jake Archibald: In The Loop - JSConf.Asia
](https://www.youtube.com/watch?v=cCOL7MC4Pl0)[YouTube - Czym do cholery jest pętla zdarzeń? | Philip Roberrs | JSConf EU
](https://www.youtube.com/watch?v=8aGhZQkoFbQ&feature=emb_title)
[Loup project for visualize call stack and callback queue](http://latentflip.com/loupe/?code=JC5vbignYnV0dG9uJywgJ2NsaWNrJywgZnVuY3Rpb24gb25DbGljaygpIHsKICAgIHNldFRpbWVvdXQoZnVuY3Rpb24gdGltZXIoKSB7CiAgICAgICAgY29uc29sZS5sb2coJ1lvdSBjbGlja2VkIHRoZSBidXR0b24hJyk7ICAgIAogICAgfSwgMjAwMCk7Cn0pOwoKY29uc29sZS5sb2coIkhpISIpOwoKc2V0VGltZW91dChmdW5jdGlvbiB0aW1lb3V0KCkgewogICAgY29uc29sZS5sb2coIkNsaWNrIHRoZSBidXR0b24hIik7Cn0sIDUwMDApOwoKY29uc29sZS5sb2coIldlbGNvbWUgdG8gbG91cGUuIik7!!!PGJ1dHRvbj5DbGljayBtZSE8L2J1dHRvbj4%3D)

---

### [!] What is event delegation?

It is a mechanism of responding to ui-events via a single common parent rather than each child, through the magic of event "bubbling" (aka event propagation). The benefits of this technique are:

- Memory footprint goes down because only one single handler is needed on the parent element, rather than having to attach event handlers on each descendant.
- There is no need to unbind the handler from elements that are removed and to bind the event for new elements.

```js
document.getElementById("parent-list").addEventListener("click", function(e) {
  if(e.target && e.target.nodeName == "LI") {
```

### [!] Event propagation, what is event bubbling and event capturing? Which phase happening first?

Dom events opisuje 3 fazy propagacji eventu:
  -	capturing (od góry drzewa do elementu na którym został wywołany),
  -	target phase (element na którym został wywołany)
  -	bubbling (od el. na którym został wywołany w górę drzewa)
  -	event podąża od elementu na którym został przechwycony w górę drzewa,
  -	np. focus nie bubbluje,
  -	stopPropagation() zatrzymuje bubbling

### [!] Difference between currentTarget and target. How to eliminate event bubbling?

When an event triggers on a DOM element, it will attempt to handle the event if there is a listener attached, then the event is bubbled up to its parent and the same thing happens. This bubbling occurs up the element's ancestors all the way to the document. Event bubbling is the mechanism behind event delegation.

---

**How can we remove something from array?**

pop - Removes from the End of an Array
shift - Removes from the beginning of an Array
splice - removes from a specific Array index
filter - allows you to programatically remove elements from an Array
reduce

- `splice` method is also insert on specific index if you add 0 as a second parameter

```js
arr.splice(index, 0, item);
```

---

**Interesting things about arrays:**

- `push` returns array length after added item
```js
arr.push(4);
```

- removing or adding item to first or last element
`unshift/push` - add an element to the beginning/end of an array
`shift/pop` - remove and return the first/last element of an array

-

---

**[!] Difference between setTimeout, setInterval. Why do we need clearInterval?**

setTimeout
does not guarantee time to execution, it's a minimum time to execution

---

**Difference between loops in JS (for...of|forEach|map|filter|reduce|find|every|some)**

> Generally, for > forEach > for..of > for..in in terms of performance. This relationship is uniform in almost all engines but may vary for different array lengths.

map, filter and reduce were introduced in ES5, so you can safely use them as implemented in every browser since years


`for...in`

> This loop always iterates over the index. While traversing through the array, the variable i will hold the value of the index of each element. This can be used when the index of the elements needed during iteration.
>
```js
var letters = ["a","b","c"];
for (var i in letters)
{
    console.log("Index : "+i, "Value : "+letters[i]);
}
```

`for...of`

- Can works on objects
- It works on any iterable
- It supports all kinds of control flow in the loop body, like continue, break, return, yield and await.

```js
var letters = ["a","b","c"];
for (var i of letters)
{
    console.log(i);
}
```

```js
for (const [key, value] of Object.entries(elements)) {
    if (value > 1) {
        returnArr.push(Number(key));
    }
}
```

The list is an extensive one such as:
- Array
- Map
- Set
- String
- TypedArray
- Other W3C classes

> Use always for...of instead of forEach. Also I personally find it more readable, but that comes down to preference. Some people think forEach is a more functional style, but that's wrong - it has no result value and is all about doing side effects, so an imperative-looking loop fits that purpose better.

[javascript - Should one use for-of or forEach when iterating through an array? - Stack Overflow](https://stackoverflow.com/a/50844413)

`forEach`

This loop performs a callback function on each element while traversing through the arr. The parameters to the callback are currentValue, index of the currentValue. Works only with those data structure which are Arrays. The method basically iterates over the elements of the array and executes a callback function.

But it isn't immutable by nature. New value isn't provided for you automatically (like with reduce or map).

Equivalent of:
```js
[1,2,3].forEach(async (value) => {
  await new Promise(resolve => console.log(value));
})
```
Can be:
```js
for (const value of [1,2,3]) {
  new Promise(resolve => console.log(value));
}
```

https://stackoverflow.com/questions/49420891/why-should-foreach-be-preferred-over-regular-iterators

`map`

Returns an array with the same length

`filter`

As the name implies, it returns an array with less items than the original array reduce returns a single value (or object)

`reduce`

> Dealing with pure functions that return values is easier to reason about than side effects.

Remember about always return value form reduce loop.

```js
// bad
return arr.reduce((acc, arrElem) => {
  if(arrElem === item) {
    return acc += 1;
  }
}, 0);

// good
return arr.reduce((acc, arrElem) => {
  if(arrElem === item) {
    return acc += 1;
  }
  return acc;
}, 0);

// or
return arr.reduce((acc, arrElem) => {
    return arrElem === item ? (acc += 1) : acc;
}, 0);
```

```js
// bad
let sum = 0;
for (let num of numbers) {
 sum += num;
}
sum === 15;

// bad
let sum = 0;
numbers.forEach((num) => {
 sum += num;
});

sum === 15;

// good
const sum = numbers.reduce((num, sum) => sum += num, 0);

sum === 15;
```

`find`

Returns the first items in an array that satisfies a condition. Was introduced in ES6/ES2015.

`every`

stops looping the first time the callback returns false or something falsey

`some`

stops looping the first time the callback returns true or something truthy

**Difference between shallow copy and deep copy of a object.**
[!] **How we can do a copy of an array? Few methods;**
[!] **Difference between deep and shallow copy?**

`Shallow copy` does not copy nested objects.

A `deep copy` copies all fields, and makes copies of dynamically allocated memory pointed to by the fields. A deep copy occurs when an object is copied along with the objects to which it refers.

1. Use `JSON.stringify` and `JSON.parse`
This approach only works well if your object only contains strings, numbers, booleans, objects, and arrays. For example, if your object has a property date that is a JavaScript date, the cloned object's date property will be a string. A round-trip through text is inefficient at best, and it won't handle Date, RegExp, undefined, etc.


2. Lodash `_.cloneDeep()`


3. Spread operator `[...arr]`
Spread syntax effectively goes one level deep while copying an array (it's the same with Object.assign()). This syntax is everything you need if your objects doesn't have objects as properties.


4. `Object.assign({}, obj)`
Lets you shallow clone an object. This will keep a reference to the original copy.

[jsPerf: JavaScript performance playground](https://jsperf.com/)

### What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?

Some examples of languages that compile to JavaScript include CoffeeScript, Elm, ClojureScript, PureScript, and TypeScript.

Advantages:

- Fixes some of the longstanding problems in JavaScript and discourages JavaScript anti-patterns.
- Enables you to write shorter code, by providing some syntactic sugar on top of JavaScript, which I think ES5 lacks, but ES2015 is awesome.
- Static types are awesome (in the case of TypeScript) for large projects that need to be maintained over time.

Disadvantages:

- Require a build/compile process as browsers only run JavaScript and your code will need to be compiled into JavaScript before being served to browsers.
- Debugging can be a pain if your source maps do not map nicely to your pre-compiled source.
- Most developers are not familiar with these languages and will need to learn it. There's a ramp up cost involved for your team if you use it for your projects.
– Smaller community (depends on the language), which means resources, tutorials, libraries, and tooling would be harder to find.
- IDE/editor support might be lacking.
- These languages will always be behind the latest JavaScript standard.
– Developers should be cognizant of what their code is being compiled to — because that is what would actually be running, and that is what matters in the end.

### High Order Function - HOF

A higher-order function is any function that takes one or more functions as arguments, which it uses to operate on some data, and/or returns a function as a result. Higher-order functions are meant to abstract some operation that is performed repeatedly. The classic example of this is map, which takes an array and a function as arguments. map then uses this function to transform each item in the array, returning a new array with the transformed data. Other popular examples in JavaScript are forEach, filter, and reduce. A higher-order function doesn't just need to be manipulating arrays as there are many use cases for returning a function from another function. Function.prototype.bind is one such example in JavaScript.
