# Interview Questions - Theoretical

## General Questions:

### Concepts

#### **Imperative programming** - Programming paradigms
> Specify both what and how. When you say how to get what you want. Requires developers to define step by step how code should be executed. Imperative programming tells the machine how to do something (resulting in what you want to happen)

- Procedural programming (COBOL, FORTRAN, BASIC, C)
- Object-oriented programming (C++, C#, Java, PHP)

```js
var numbers = [1,2,3,4,5]
var doubled = []

for(var i = 0; i < numbers.length; i++) {
  var newNumber = numbers[i] * 2
  doubled.push(newNumber)
}
console.log(doubled) //=> [2,4,6,8,10]
```
#### **Declarative programming** - Programming paradigms

> (HTML, CSS, React, Prolog, Lisp) Specify what to do, not how to do it. When you say what you want. It does not force the traveler to memorize a long set of instructions. Declarative programming tells the machine what you would like to happen (and the computer figures out how to do it). Users concentrate on defining the input and output rather than the program steps required in a procedural programming language such as C++ or Java.

- [Functional programming](#functional-programming) - based on lambda calculus is Turing complete, avoids states, side effects and mutation of data.
- Logic
- Mathematical

```js
var numbers = [1,2,3,4,5]

var doubled = numbers.map(function(n) {
  return n * 2
})
console.log(doubled) //=> [2,4,6,8,10]
```

#### What is an isomorphic application?
https://www.lullabot.com/articles/what-is-an-isomorphic-application

### Questions

- **What is the diffrent between web developer and software engineer?**
 Both involve programming and craftsmanship, but software engineering adds to it knowledge of data structures and algorithms, compiled languages, memory considerations, and understanding the impact of coding and architecture decisions on the machines where they reside.


- Interfaces
- Namespace
- TDD, DDD
- JSON
- AJAX
- Regular expression
- Serverless functions
- Web App Security
    - XSS cross-site scripting
- npm vs yarn - differences
- Serverless functions
- Hoisting
- Bezpieczeństwo aplikacji www
- CSS Modules, CSS in JS, Styled Components
- performance
- SPA architecture
- What is Continous: Integrarion, Delivery?
- Give some examples of tree shaking algorithms and how they work?
- Różnice pomiędzy private, public, protected
- How browsers are working?
- [!] How is caching implemented in browsers?
- What is TCP/UDP?
- DNS how works?
- What is telnet?
- How does browser builds a page?
- What is the difference between XHR request and fetch?
- Merge and rebase - differences?
- Jak parsowany jest html przez przeglądarkę?
- Semantic Versioning
- Basic Terminal Usage
- HTTP/HTTPS
  - Difference between http and https?
  - Error codes
- Character Encodings
- Licences
- Version Control Systems
- Data structures
  - Złożoność obliczeniowa
- REST API
- Algorithms
- PUB - klucze prywatne publiczne
- SSL
- What is CORS and how works?
- SSH
- What is JWT?


- **Public and private keys**
https://www.digitalocean.com/docs/droplets/how-to/add-ssh-keys/to-existing-droplet/
https://askubuntu.com/questions/218344/why-am-i-getting-a-port-22-connection-refused-error

## WEB

### Questions

- What are service workers and what are the advantages?
- Can you access hard drive from browser?
- Various methods to do API calls.
- What is a PWA?
- webservices
- websockets
- webworkers


- **What are various types of storages? What is the difference and possible use cases for: localStorage, sessionstorage, cookie, indexdb?**

  -	**localStorage** - dane znajdujące się w tym obiekcie dostępne są pomiędzy sesjami przeglądarki, tzn. mamy do nich dostęp nawet kiedy użytkownik, zamknie a następnie otworzy przeglądarkę/zakładkę
  -	**sessionStorage** - w tym przypadku dane przechowywane są tylko w ramach jednej sesji przeglądarki, kiedy zamkniemy ją, dane zostaną utracone
  -	**cookies** - to niewielkie informacje tekstowe, wysyłane przez serwer WWW i zapisywane po stronie użytkownika (zazwyczaj na twardym dysku). Domyślne parametry ciasteczek pozwalają na odczytanie informacji w nich zawartych jedynie serwerowi, który je utworzył.


## HTML

### Concepts

- SEO
- Semantic [What Is Semantic HTML and Why You Should Use It](https://www.lifewire.com/why-use-semantic-html-3468271)
- Accessibility [Learn JavaScript Accessibility Features for Making Your JavaScript Web Applications More Accessible with Marcy Sutton.](https://frontendmasters.com/courses/javascript-accessibility/)

- Design patterns
  - Singleton
  - Facade (pol. fasada)
  - Composite (pol. kompozyt)
  - Decorator (pol. dekorator)
  - Observer (pol. obserwator)
  - MVC
  - KISS (Keep It Simple, Stupid)
  - [!] SOLID
  - DRY
  - Factory (pol. fabryka)

### Questions

##### Sources

[What Is Semantic HTML and Why You Should Use It](https://www.lifewire.com/why-use-semantic-html-3468271)

## CSS

### Concepts

### Questions

- Ważność styli CSS

## JS

### Concepts

#### Functional Programming

[6 fundamental terms in functional JavaScript - Frontend Weekly - Medium](https://medium.com/front-end-weekly/6-fundamental-terms-in-functional-javascript-e25d50d40b2c)
In javascript there are 6 fundamental terms:
  - Arrow Functions
  - First-class function
  - Hight-order function
  - Unary function
  - Currying
  - Pure Functions

#### Immutability - Side Effects - Immutable objects
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

#### Execution Context

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

#### Hoisting (var, let, const)

>Hoisting is the concept where Javascript moves all declarations to the top of the current scope. As such, a variable can be used before it has been declared. There are two types of hoisting:
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

#### Scope

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

## Questions

- **What is a Function?**
Is a process which takes some input, called arguments, and produces some output called a return value.
    - Mapping: Produce some output based on given inputs. A function maps input values to output values.
    - Procedures: A function may be called to perform a sequence of steps. The sequence is known as a procedure, and programming in this style is known as procedural programming.
    - I/O: Some functions exist to communicate with other parts of the system, such as the screen, storage, system logs, or network.


- **What is Pure Function?**
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


- [!] Explain the usage of bind, call, apply.

  -	call wywołuje funkcję i wskazuje this którego ma użyć, wywołanie funkcji następuje w chwili wywołania call lub apply,
  -	bind zwraca przekazaną funkcję jako nową ze wskazaniem na this w argumencie,


- [!] Event Loop

  -	przy wywołaniu funkcje zostaną dodane do call stack i usuwane z niego gdy zwraca wartość,
  -	web api pozwala na opóźnienie wykonania zadań bez blokowania wykonywania innych, tak jak np. setTimeout [warto dodać przykład z setTimeout na 0 i wyjaśnienie dlaczego nie wykona sie natychmiast]
  -	po zakończeniu (np timera w setTimeout) funkcja została dodana do queue, gdzie funkcje oczekuje na połączenie przez event loopa do call stacku
  -	jeżeli wszystkie funkcje w call stacku zostaną wywołane, funkcje z queue zostają przeniesione do call stack przez event loop

[YouTube - Jake Archibald: In The Loop - JSConf.Asia
](https://www.youtube.com/watch?v=cCOL7MC4Pl0)[YouTube - Czym do cholery jest pętla zdarzeń? | Philip Roberrs | JSConf EU
](https://www.youtube.com/watch?v=8aGhZQkoFbQ&feature=emb_title)

- **How is the value of `this` decided?**

  -	jeżeli wywołano funkcję ze słowem new this odnosi się do nowo utworzonego obiektu,
  -	jeżeli zostało użyte jedno z apply, call lub bind zostało użyte do wywołania funkcji, this odnosi się do funkcji przekazanej jako argument,
  -	jeżeli funkcja została zdefiniowana w obiekcie i użyta poprzez zapis obiekt.funkcja() this odnosi się do obiektu który zdefiniował funkcję,


- **HOC High Order Functions**
  -	funkcja która przyjmuje inna funkcje jako parametr lub zwraca inna funkcje,
  -	przykłady z js. np. map, reduce, filter, forEach,
  -	łatwiejsze do testowania


- **Progressive enhancement**
  -	poświęcenie wykorzystania nowych technologii na rzecz działania na starszych urządzeniach, następnie dodanie opcjonalnych rozszerzeń na węższe grono urządzeń/przeglądarek


- **Graceful degradation**
  -	wykorzystanie nowych technologii podczas tworzenia aplikacji,
  -	następnym etapem jest dostosowanie do starszych przeglądarek/urządzeń,
  -	przykład: youtube i filmy wyświetlane w html5 w nowych przeglądarkach oraz flash w starszych


- **Redux selectors**
  -	selektory to funkcje które zwracają tylko interesująca część danych
  -	reselect cachuje dane dzięki czemu zwiększają optymalizacje aplikacji
  -	używamy reselect jeżeli do otrzymania danych potrzebujemy wykonać funkcje

- **Dziedziczenie (Prototype a proto)**

  - Prototype a proto (Właściwość prototype obiektu function wskazuje inny obiekt. Ma ona znaczenie tylko, jeśli funkcja jest wywoływana jako konstruktor. Wszystkie obiekty utworzone za pomocą funkcji przechowują referencję do właściwości prototype i mogą korzystać z jej właściwości jak z własnych. JavaScript jest prototypowym językiem obiektowym. Funkcje w języku JavaScript są obiektami  osiadającymi właściwości i metody. Niektóre z nich już znasz, na przykład metody apply() i call() oraz właściwości length i constructor. prototype jest kolejną właściwością obiektu Function. W JavaScripcie obiekty są przekazywane przez referencję, więc prototype nie jest kopiowany z każdą nową instancją obiektu. Co to oznacza w praktyce? Oznacza to, że można modyfikować prototype w dowolnym momencie, a wszystkie obiekty, nawet te utworzone wcześniej, dostrzegą te zmiany. )

- Programowanie funkcyjne a programowanie obiektowe
ES6 Features
    - [!] Strict Mode
- How cookie is working and what cookie secure is?
- Notacja (w programowaniu) - jest umownym sposobem zapisu nazw: stałych, zmiennych, metod, klas itp. Notacja ta ma na celu stosowanie się do określonych uniwersalnych zasad, aby kod programu, był uniwersalnie dla każdego przejrzysty i zrozumiały. W naszej grupie, przyjęliśmy mieszaninę dwóch notacji. CamelCase oraz notację węgierską.
https://github.com/gelldur/Kino-Time-Tracker/wiki/Notacje-(w-programowaniu)
- What is the Difference Between Class and Prototypal Inheritance?

- **What is Function Composition?**
  -	sposób pisania kodu - pisanie funkcji która posiada one job only
  -	następnie tworzenie bardziej skomplikowanych funkcji na podstawie wcześniej zdefiniowanych podstawowych funkcji
  -	kod latwo testowalny

-	glownie chodzi o rozdzielenie funkcji synchronicznych od asynchronicznych
- Asynchronous: Promises, async/await
- Prototypes
- Prototype and Prototype Chain
- What is Server Side Rendering? Why do we need it?
- Why Google crawlers are unable to crawl Client Side Rendered applications?
- What is ES6 and give some new features?
- How does browser renders HTML on screen?
- What are side effects?
- Is javascript compiled or interpreted?
- Difference between shallow copy and deep copy of a object.
- Rodzaje komponentów
- revealing module pattern
- jak można zmienić kontekst wywołania funkcji?
- [!] What is the difference between =, ==, === ?
- [!] What is closure? Examples. When we define variable in internal function, is it visible in the scope above?
  -	są to funkcję które mają dostęp do zmiennych na zewnątrz,
  -	funkcja wewnętrzna ma dostęp do swoich zmiennych oraz w blokach nadrzędnych,
  -	parent funkcji nie ma dostępu do zmiennych funkcji wewnątrz jego bloku,
  -	użyteczne aby uzyskac cos na ksztalt zmiennych prywatnych, co zabezpiecza dane
- Closure

- [!] What is hoisting in JS? Key word this;
  -	jeżeli wywołano funkcję ze słowem new this odnosi się do nowo utworzonego obiektu,
  -	jeżeli zostało użyte jedno z apply, call lub bind zostało użyte do wywołania funkcji, this odnosi się do funkcji przekazanej jako argument,
  -	jeżeli funkcja została zdefiniowana w obiekcie i użyta poprzez zapis obiekt.funkcja() this odnosi się do obiektu który zdefiniował funkcję,

- [!] Difference between currentTarget and target. How to eliminate event bubbling?
- [!] **Event propagation, what is event bubbling and event capturing? Which phase happening first?**
Dom events opisuje 3 fazy propagacji eventu:
  -	capturing (od góry drzewa do elementu na którym został wywołany),
  -	target phase (element na którym został wywołany)
  -	bubbling (od el. na którym został wywołany w górę drzewa)
  -	event podąża od elementu na którym został przechwycony w górę drzewa,
  -	np. focus nie bubbluje,
  -	stopPropagation() zatrzymuje bubbling

- [!] **What is event delegation?**

  -	pozwala na obsłużenie jednym handlerem wiele zdarzeń, [dziwnie to brzmi i w sumie nie wiem o co chodzi] - wyjaśnione poniżej z eventem na parnecie
  -	event zostanie dodany do parenta, ktory np. za pomoca event.target sprawdza element ktory go wywołał i odpowiednio obsługuje

- [!] Favourite es6 features
- [!] Difference between setTimeout, setInterval. Why do we need clearInterval?
- [!] Difference between deep and shallow copy?
- [!] How we can do a copy of an array? Few methods;
- [!] Object.freeze vs const - difference
- What is a Promise?
- What is npm?
- How javascript is working? (long description) engine V8 (google made), nodejs builded on it?
- What is Vanilla JS?
- Service Worker API
- template literals
- convert nodeList to Array
- spread operator
- map foreach
- FOUC
- BABEL jak działa
- Garbage collector in javascript
- js throttle
- ecmascript modules imports/exports
- Typy danych (primitive types)
- Typescrtipt
- anonymous functions

## React

### Questions

- [!] Difference between props and state?

- [!] **Stateless, class, stateful and pure components**

  - stateless - do renderowania prostych elementów ui, brak stanu, update jak zwykły komponent
  -	pure - do renderowania komponentów których rerender jest potrzeby rzadziej niż np. jego rodzica, zapobiega niepotrzebnym rerenderom
  -	komponent posiadający stan i propsy

- [!] React metod lifecycle (constructor, shouldComponentUpdate, render)
- [!] Where we can put fetching of data and why?
- [!] defaultProps
- [!] React Hooks : useState, useEffect
- [!] react memo and lazy - for which purpose and do we need them;
- [!] props drilling ("threading") issue; createContext, Provider

- **Wpółdzielenie kodu**
  - komponenty wyższego rzędu (ang. higher-order components)
  - właściwości renderujące (ang. render props).
  - hooks

- context api
- react refs
- virtual DOM
- react reconcilation
- react hooks

## Redux

### Questions

- [!] Redux Flow (Flux Pattern)
- [!] What is action Creator - what they return?
- [!] mapStateToProps, mapDispatchToProps
- [!] combineReducers
- [!] What is middleware in Redux, why it is needed / redux-thunk example

## Node

### Questions

- [!] How many threads we have in NodeJS;
- [!] 4 types of stream  in Node (writable, readable, duplex, transform); Pipe() and pipeline() methods, difference?
- [!] Promise - what is that?
- [!] async await - how it works;
- [!] callback hell, how to avoid it?
- [!] what is CORS issue - how to resolve it?
- [!] helmet in node - what is does?

## Tests

### Types of tests

- Unit tests (pol. jednostkowe)
  - **Chai** (expectation/assertion library, expect/should/assert)
  - **Jest** (developed by Facebook, Use Jest to capture snapshots of React components for certain time with props and states changes. Can be used together with Enzyme. Can mock clickable events to capture state changes in a snapshot)
  - **Jasmine** (test runner, run tests and log results)
  - **Mocha** (test runner, run tests and log results)

- Integration tests (pol. integracyjne)
  - **Enzyme** (developed by Airbnb. Testing utility for React that makes it easier to assert, manipulate, and traverse your React Components’ output. It simulates ReactDOM, and React Components like JQuery finding DOM. Can be used to shallow render React components.)
  - **Karma** is a testing environment. Karma works by running your unit tests inside of browsers (defaulting to PhantomJS, a headless WebKit browser), to allow you to test browser-based JavaScript code.
  - **react-testing-library**

- E2E tests (pol. systemowe)
  - **cypress**
  - **selenium**

- Regression tests (pol. regresyjne)

- Acceptance tests (pol. akceptacyjne)

### Questions

- What is Unit Testing?

### Terms
- Black-box testing
>wykorzystywane pojęcie w testach e2e, spojrzenie na system z zewnętrznego punktu widzenia; system jako „czarna skrzynka”, która ma realizować określone zadania i tylko pod tym kątem jest testowana – np. testy odbioru

- White-box testing
> testowanie obejmujące wgląd we wnętrze programu: testujący przeprowadza test jednocześnie badając kod programu. Wymagane umiejętności programistyczne – np. testy jednostkowe

## Links and sources


[YouTube - JSConf - Functional Programming](https://www.youtube.com/watch?v=e-5obm1G_FY)

[Inheritance and the prototype chain - JavaScript \| MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)

[Dziedziczenie i łańcuch prototypów - JavaScript \| MDN](https://developer.mozilla.org/pl/docs/Web/JavaScript/dziedziczenie_lancuch_prototypow)

[The Different Testing Tools (chai, mocha, enzyme, jest)](https://medium.com/@leannezhang/clarifying-different-testing-tools-chai-mocha-enzyme-jest-d7a561f01857)

[Poziomy testów - Czyli kilka słów o 4 poziomach testów i ich celu - DevEnv](https://devenv.pl/poziomy-testow/)

[fedev.tech](https://fedev.tech/topic/)

[FullStack.Café](https://www.fullstack.cafe/)

[fedev.tech - javascript](https://fedev.tech/topic/javascript/)

[JS: interview Questions -3](http://thatjsdude.com/interview/dom.html#windwoVsDocument)

[123-Essential-JavaScript-Interview-Questions: JavaScript interview Questions](https://github.com/ganqqwerty/123-Essential-JavaScript-Interview-Questions)

[JavaScript Array Functions CheatSheet - DEV](https://dev.to/vincenius/javascript-array-functions-cheatsheet-1c15)

[8 Ultimate Full Stack Interview Questions and Answers - DEV](https://dev.to/fullstackcafe/8-ultimate-full-stack-interview-questions-dj5)

[GitHub - sindresorhus/awesome: 😎 Awesome lists about all kinds of interesting topics](https://github.com/sindresorhus/awesome#media)

[GitHub - MaximAbramchuck/awesome-interview-questions: A curated awesome list of lists of interview questions. Feel free to contribute!](https://github.com/MaximAbramchuck/awesome-interview-questions?fbclid=IwAR3ovv1e77vVkL4jVpMMJxDqH9-A0uLYN8anzfIpVaycrN_dvHBuIsT4yxI#javascript)

[GitHub - denysdovhan/wtfjs: A list of funny and tricky JavaScript examples](https://github.com/denysdovhan/wtfjs#-is-equal-)

[30secondsofcode](https://www.30secondsofcode.org/react/p/1)

[Interview Questions For Full-Stack, Web Developers ☕ FullStack.Café](https://www.fullstack.cafe/javascript)

[API-Security-Checklist/README-pl.md at master · shieldfy/API-Security-Checklist · GitHub](https://github.com/shieldfy/API-Security-Checklist/blob/master/README-pl.md)

[fedev.tech](https://fedev.tech/topic/)

[FullStack.Café](https://www.fullstack.cafe/)

[javascript-interview-questions: List of 1000 JavaScript Interview Questions](https://github.com/sudheerj/javascript-interview-questions#what-are-the-differences-between-javascript-and-typescript)

[123-Essential-JavaScript-Interview-Questions: JavaScript interview Questions](https://github.com/ganqqwerty/123-Essential-JavaScript-Interview-Questions)

[JavaScript Array Functions CheatSheet - DEV](https://dev.to/vincenius/javascript-array-functions-cheatsheet-1c15)

[8 Ultimate Full Stack Interview Questions and Answers - DEV](https://dev.to/fullstackcafe/8-ultimate-full-stack-interview-questions-dj5)

[GitHub - sindresorhus/awesome: 😎 Awesome lists about all kinds of interesting topics](https://github.com/sindresorhus/awesome#media)

[GitHub - MaximAbramchuck/awesome-interview-questions: A curated awesome list of lists of interview questions. Feel free to contribute!](https://github.com/MaximAbramchuck/awesome-interview-questions?fbclid=IwAR3ovv1e77vVkL4jVpMMJxDqH9-A0uLYN8anzfIpVaycrN_dvHBuIsT4yxI#javascript)

[GitHub - denysdovhan/wtfjs: A list of funny and tricky JavaScript examples](https://github.com/denysdovhan/wtfjs#-is-equal-)

[30secondsofcode](https://www.30secondsofcode.org/react/p/1)

[Interview Questions For Full-Stack, Web Developers ☕ FullStack.Café](https://www.fullstack.cafe/javascript)

