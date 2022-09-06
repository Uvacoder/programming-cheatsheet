# Interview - General (Algorithms, Clean Code, Principles)

???

- Interfaces
- Namespace
- TDD, DDD
- JSON
- AJAX
- Regular expression
- Serverless functions
- npm vs yarn - differences
- Serverless functions
- CSS Modules, CSS in JS, Styled Components
- Performance
- SPA architecture
- What is Continous: Integrarion, Delivery?
- Różnice pomiędzy private, public, protected
- How browsers are working?
- What is TCP/UDP?
- DNS how works?
- What is telnet?
- How does browser builds a page?
- What is the difference between XHR request and fetch?
- Merge and rebase - differences?
- Semantic Versioning
- Basic Terminal Usage
- Character Encodings
- Licences
- Version Control Systems
- Data structures
  - Złożoność obliczeniowa
- Różnica pomiędzy REST a GraphQL
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
- IETF
???

## Concepts

### **Imperative programming**

[Programming paradigms]

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

### **Declarative programming**

[Programming paradigms]

> (HTML, CSS, React, Prolog, Lisp) Specify what to do, not how to do it. When you say what you want. It does not force the traveler to memorize a long set of instructions. Declarative programming tells the machine what you would like to happen (and the computer figures out how to do it). Users concentrate on defining the input and output rather than the program steps required in a procedural programming language such as C++ or Java.

[8 steps to turn imperative JavaScript class to a functional declarative code \| by Martin Novák | Frontend Weekly | Medium](https://medium.com/front-end-weekly/8-steps-to-turn-imperative-javascript-class-to-a-functional-declarative-code-862964faf46c)

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

### What is an isomorphic application?

https://www.lullabot.com/articles/what-is-an-isomorphic-application

## Questions

### What is the diffrent between web developer and software engineer?

Both involve programming and craftsmanship, but software engineering adds to it knowledge of data structures and algorithms, compiled languages, memory considerations, and understanding the impact of coding and architecture decisions on the machines where they reside.

---

### Jak przeglądarka łączy się z hostem?

1. Wpisyjemy adres URL 
2. Ustalenie adresu IP strony
- Czy adres kiedyś był odwiedzany i znamy adres IP
- Czy w systemiem i pliku hosts istnieje taki adres
- Internet Service Provider DNS
- Global authority 
3. Połączenie z hostem z adresu IP przy pomocy HTTP i portu 80 lub 443
- wysłanie odpowiednich żądań zgodnych z protokołem komunikacji HTTP/1.1 lub HTTP/2

---

### Różnica pomiędzy URI, URL, URN
**What is the difference between URL and URI?**

`URL` (ang. Uniform Resource Locator)
`URI` (ang. Uniform Resource Indentifier)

URL-e są podzbiorem URI. Często używa się ich zamiennie, dokładne wyjaśnienie zawiera się w dokumencie: [RFC 3305 - Report from the Joint W3C/IETF URI Planning Interest](https://tools.ietf.org/html/rfc3305#section-2.3)

`URN` (ang. Uniform Resource Name)

An identifier might specify the location of a resource (a URL) or its name (a URN), independent of location.  Thus a URI was either a URL or a URN.

**Verdict:**
> URI space was thought to be partitioned into two classes: URL (as a ) and URN (as a ). Any new scheme would be cast into one of these two classes. Over time, the importance of this additional level of hierarchy seemed to lessen; the view became that an individual scheme did not need to be cast into one of a discrete set of URI types, such as "URL", "URN", "URC", etc.

---

### How ssh connection is working?

