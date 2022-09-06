# Interviewing for Front-End Engineers

frontendmasters - Jem Young

[Learn to pass front-end engineering interviews, and give better interviews as a technical manager.](https://frontendmasters.com/courses/interviewing-frontend/)

<https://github.com/young/frontend-interviewing>

## Recruiter questions

1. How many steps are int the interview process?
2. How long does it generally take?
3. How big is you engineering team?
4. Which team would I be interviewing for?
5. What is the culture like?

- work hard, play hard
- very relax and easy going
- we celebrate wins together as a team
- we go out for a dinner every day

6. Who are you competitors?
7. What sort of projects would I work on?

## First call questions about JS

1. Difference between const, let, var?

Most difference is in hoisting between of them.

const - pointer to value, which cannot be changed, but we can modify values, in objects and arrays. We cannot change also primitive values because we get an error: "Uncaught TypeError: Assignment to constant variable."

var - is hosited to the top.

const and let - if you try to access them before declaration you get a reference error and var just throw undefined.

3. Explain prototypical inheritance

Everything inherits from an object and have a prototype. And if you create an object from another object you are inherit all those properties but you can overwrite them with your own.

5. What is 'this' mean in JS?

It's the current scope you're in which can change and if there is no scope there is a global window.

He:
Global context of everything that is available to access, all objects, function available the are not locally defined.

7. What is the data structure of the DOM?

Tree.

9. What is a Stack and a Queue? How would you create those data structures in JavaScript?

This is a stack. LIFO FIFO
Stack is LIFO, queue is FIFO.

You can create that using an array and pop and push methods.

11. How can you tell if an image element is loaded on a page?

There is an onload element, you can run a call back.

13. What is call() and apply()?

Using to change the scope for the calling function.

call() - is a series of arguments and applies an array of arguments.

apply() - is an array.

15. What is event delegation and what are the performance tradeoffs?

You can apply an event handler to every single element you wanna have. You can say I wanna have one event listener and if you can on that it just bubbles up to the parent that handles the event.

Bubbling as a more info about that.

Better have one eventdelegation than 60.

17. What is a Worker? When would you use one?

Using for not blocking the UI and do not stop the stack. If you have to do something expensive worker will help you.

## Project questions

- make a code readable
- comment your code to explain logic and chooses
- don't complicate the architecture
- don't import too many libraries
- add some unit tests
- ask questions

## Big O

Notation which tells us how log takes the worst case scenario of solution|function.

Big Omega - best case - Omega(1)
Bit Theta - Average case - Theta(n)
Big O - Worst case - O(n)

## Practise question

Knowladge about pure language than about freamworks. You should know how to add elements to DOM, using createDocumentFragment, appendChild, createElement, innerText, classList, be able to create own class with functions and properties.

Add eventLister on the root element and then catch event from clicked element and use it in your code.

```js

const listOfElements = ['A', 'B', 'C', 'D', 'E'];

class RemovingItems {
  constructor(listOfElements, rootElement) {
    this._listOfElements = listOfElements;
    this._rootElement = rootElement;
  }

  // Implementation can be easier
  // removeElementFromPage() {
  //   this._rootElement.addEventListener("click", function(event){
  //     const clieckedElementValue = event.target.textContent;
  //     const items = document.querySelectorAll('.element');
  //     for (const item of items) {
  //       if (clieckedElementValue === item.textContent) {
  //         item.remove();
  //       }
  //     }
  //   });
  // }

  removeElementFromPage() {
    this._rootElement.addEventListener("click", function(event){
      event.target.remove();
    });
  }

  renderAllElements() {
    const fragment = document.createDocumentFragment();

    this._listOfElements.forEach(function(element) {
        let div = document.createElement('div');
        div.textContent = element;
        div.className = 'element';
        // div.classList.add()
        fragment.appendChild(div);
    });

    return fragment;
  }

    renderElementOnDocument() {
      const elementsObject = this.renderAllElements();
      this.removeElementFromPage();
      this._rootElement.appendChild(elementsObject);
      document.body.appendChild(this._rootElement);
    }
}

const rootElement = document.createElement('div');
const removingList1 = new RemovingItems(listOfElements, rootElement)
removingList1.renderElementOnDocument();
```

<https://developer.mozilla.org/en-US/docs/Web/API/ChildNode/remove>

[Event Object](https://www.w3schools.com/JSREF/obj_event.asp)

[JavaScript Event Delegation, and event.target vs. event.currentTarget \| by Florence Liang | Medium](https://medium.com/@florenceliang/javascript-event-delegation-and-event-target-vs-event-currenttarget-c9680c3a46d1)

[Node.appendChild() - Web APIs \| MDN](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild)

[Document.createDocumentFragment() - Web APIs \| MDN](https://developer.mozilla.org/en-US/docs/Web/API/Document/createDocumentFragment)

[Classes - JavaScript \| MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)

## On-site review

- Practice writing code without a computer
- Study general sample problems
- Ask friends to test you

Algorithm questions, HTML, general JS problems

## Usefull methodes

String

- split()
- toLowerCase()
- substring()
- startsWith()

Array

- Array.from()
- [...item]
- .isArray()
- .filter()
- .concat()
- .join()
- .pop()
- .push()
- .map()

Object

- Object.entries()

Time

- setInterval()
- setTimeout()

## Tree search

## requestAnimationFrame()

```js
function moveElement(duration, distance, element) {
  const start = performance.now();
  element.style.transform = 'translateX(10px);'
  requestAnimationFrame();
}
```
