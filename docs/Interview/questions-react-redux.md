# Interview - React | Redux

[Build your own React](https://pomb.us/build-your-own-react/)

## Questions

### What is Virtual DOM?

The virtual DOM (VDOM) is an in-memory representation of Real DOM. The representation of a UI is kept in memory and synced with the “real” DOM.

### What is reconciliation?

When a component’s props or state change, React decides whether an actual DOM update is necessary by comparing the newly returned element with the previously rendered one. When they are not equal, React will update the DOM. This process is called reconciliation.

### Why we are using React refs?

Refs provide a way to access DOM nodes or React elements created in the render method.

### What is Context API?

Context provides a way to pass data through the component tree without having to pass props down manually at every level. For example, authenticated user, locale preference, UI theme need to be accessed in the application by many components.

```js
const {Provider, Consumer} = React.createContext(defaultValue);
```
https://reactjs.org/docs/context.html

### [!] What is Flux?

While Flux is a general pattern for enforcing data flow through an application, there exist many implementations from which to choose from.  

Unidrectional application flow paradigm popular a few years back in React; mostly superceded by Redux these days. This pattern, according to Facebook, is divided in parts: dispatcher, stores, and the views.

[Flux, Redux and React Redux overview - DEV](https://dev.to/renatobentorocha/flux-redux-and-react-redux-overview-32h8)

### What is JSX?

JSX is a syntax notation for JavaScript XML(XML-like syntax extension to ECMAScript). It stands for JavaScript XML. It provides expressiveness of JavaScript along with HTML like template syntax. For example, the below text inside h1 tag return as javascript function to the render function,

### What are Higher-Order components?

A higher-order component is a function that takes a component and returns a new component. HOC's allow you to reuse code, logic and bootstrap abstraction. The most common is probably Redux’s connect function. Beyond simply sharing utility libraries and simple composition, HOCs are the best way to share behavior between React Components. If you find yourself writing a lot of code in different places that does the same thing, you may be able to refactor that code into a reusable HOC.

We call them as “pure’ components”  because they can accept any dynamically provided child component but they won’t modify or copy any behavior from their input components.

```js
const EnhancedComponent = higherOrderComponent(WrappedComponent);
```

### How to create props proxy for HOC component?

```js
 function HOC(WrappedComponent) {
  return class Test extends Component {
    render() {
      const newProps = {
        title: 'New Header',
        footer: false,
        showFeatureX: false,
        showFeatureY: true
      };

      return <WrappedComponent {...this.props} {...newProps} />
    }
  }
}
 ```

### What is the purpose of using super constructor with props argument?

A child class constructor cannot make use of this reference until super() method has been called. The same applies for ES6 sub-classes as well. The main reason of passing props parameter to super() call is to access this.props in your child constructors.

```js
class MyComponent extends React.Component {
    constructor(props) {
        super();
        console.log(this.props); // Prints undefined
        // But Props parameter is still available
        console.log(props); // Prints { name: 'sudheer',age: 30 }
    }

    render() {
        // No difference outside constructor
        console.log(this.props) // Prints { name: 'sudheer',age: 30 }
    }
}
```

### What are portals in ReactJS?

Portal is a recommended way to render children into a DOM node that exists outside the DOM hierarchy of the parent component. The first argument (child) is any renderable React child, such as an element, string, or fragment. The second argument (container) is a DOM element.

```js
ReactDOM.createPortal(child, container);
```

### [!] Name the different lifecycle methods.

- `componentWillMount`- this is most commonly used for App configuration in your root component. 
- `componentDidMount` - here you want to do all the setup you couldn’t do without a DOM, and start getting all the data you need. Also if you want to set up eventListeners etc. this lifecycle hook is a good place to do that.
- `componentWillReceiveProps` - this lifecyclye acts on particular prop changes to trigger state transitions.
– `shouldComponentUpdate` - if you’re worried about wasted renders shouldComponentUpdate is a great place to improve performance as it allows you to prevent a rerender if component receives new prop. shouldComponentUpdate should always return a boolean and based on what this is will determine if the component is rerendered or not.
- `componentWillUpdate` - rarely used. It can be used instead of componentWillReceiveProps on a component that also has shouldComponentUpdate (but no access to previous props).
- `componentDidUpdate` - also commonly used to update the DOM in response to prop or state changes.
- `componentWillUnmount` - here you can cancel any outgoing network requests, or remove all event listeners associated with the component.

### What is a store in redux?

The store is a JavaScript object that holds application state. Along with this it also has the following responsibilities:
- Allows access to state via getState();
- Allows state to be updated via dispatch(action);
- Registers listeners via subscribe(listener);
- Handles unregistering of listeners via the function returned by subscribe(listener).

### What is an action?

Actions are plain javascript objects. They must have a type indicating the type of action being performed. In essence, actions are payloads of information that send data from your application to your store. 

### [!] Types of components - Stateless, class, stateful and pure components
  
`React.Component` or `Stateful Component` or `Smart Component` or `Container Component`

It is the base class for React components when they are defined using ES6 classes.

`React.PureComponent`

Similar to React.Component. The difference between them is that React.Component doesn’t implement shouldComponentUpdate(), but React.PureComponent implements it with a shallow prop and state comparison.
  
`Function Component` or `Stateless Component` or `Dumb Component` or `Presentational Component`

Stateless Components is an old name. (a flavor of “reusable” components) are nothing more than pure functions that render DOM based solely on the properties provided to them.
  
`React.memo`

It is high order component similar to React.PureComponent but for fucntional components instead of classes.

If your function component renders the same result given the same props, you can wrap it in a call to React.memo for a performance boost in some cases by memoizing the result. This means that React will skip rendering the component, and reuse the last rendered result.

React.memo only checks for prop changes. If your function component wrapped in React.memo has a useState or useContext Hook in its implementation, it will still rerender when state or context change.

### Wha is React.lazy?

`React.lazy`

The React.lazy function lets you render a dynamic import as a regular component.

Before:

```js
import OtherComponent from './OtherComponent';
```

After:

```js
const OtherComponent = React.lazy(() => import('./OtherComponent'));
```

This will automatically load the bundle containing the OtherComponent when this component is first rendered.

### What's the difference between a "smart" component and a "dumb" component?

- Smart components - manage their state or in a Redux environment are connected to the Redux store. 

- Dumb components - are driven completely by their props passed in from their parent and maintain no state of their own.

### What is the difference between ShadowDOM and VirtualDOM?

The Shadow DOM is a browser technology designed primarily for scoping variables and CSS in web components. The virtual DOM is a concept implemented by libraries in JavaScript on top of browser APIs.

### What is the difference between a controlled component and an uncontrolled component?

A `controlled component` is a component where React is in control and is the single source of truth for the form data. 
An `uncontrolled component` is where your form data is handled by the DOM, instead of inside your React component. They are stores its own state internally, and you query the DOM using a ref to find its current value when you need it. This is a bit more like traditional HTML.

```js
class UserProfile extends React.Component {
  constructor(props) {
    super(props);
    this.handleSubmit = this.handleSubmit.bind(this);
    this.input = React.createRef();
  }

  handleSubmit(event) {
    alert('A name was submitted: ' + this.input.current.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Name:
          <input type="text" ref={this.input} />
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```
In most cases, it is recommend using controlled components to implement forms.

### What is React Fiber?

Fiber is the new reconciliation engine or reimplementation core algorithm in React 16. Its main goal is to enable incremental rendering of the virtual DOM.The goal of React Fiber is to increase its suitability for areas like animation, layout, gestures, ability to pause, abort, or reuse work and  assign priority to different types of updates; and new concurrency primitives.

The goal of React Fiber is to increase its suitability for areas like animation, layout, and gestures. Its headline feature is incremental rendering: the ability to split rendering work into chunks and spread it out over multiple frames.

### [!] How to connect redux to react?

mapStateToProps, mapDispatchToProps

### [!] What is Action Creator

It is another common convention that, instead of creating action objects inline in the places where you dispatch the actions, you would create functions generating them.

Instead of:
```js
dispatch({
  type: 'ADD_TODO',
  text: 'Use Redux'
})
```

We can create:

```js
export function addTodo(text) {
  return {
    type: 'ADD_TODO',
    text
  }
}

import { addTodo } from './actionCreators'
dispatch(addTodo('Use Redux'))
```
### [!] What is combineReducers?

Combine reducers takes a hash of reducers and returns a reducer. The resulting reducer represents an object of the same shape as the hash.

```js
combineReducers({ name: nameReducer, secondName: secondNameReducer })
```

### [!] What is Redux Thunk used for?

Redux thunk is middleware that allows you to write action creators that return a function instead of an action. The thunk can then be used to delay the dispatch of an action if a certain condition is met. This allows you to handle the asyncronous dispatching of actions. 

### What is reselect and how it works?

Reselect is a selector library (for Redux) which uses memoization concept. It was originally written to compute derived data from redux-like applications state, but it can't be tied to any architecture or library.

Reselect keeps a copy of the last inputs/outputs of the last call, and recomputes the result only if one of the inputs changes. If the the same inputs are provided twice in a row, Reselect return the cached saved output. It's memoization and cache are fully customizable.

### [!] What is useState and useEffect from React Hooks?

`useState` - returns a stateful value, and a function to update it.

```js
const [state, setState] = useState(initialState);
```

`useEffect` - will run after the render is committed to the screen. Think of effects as an escape hatch from React’s purely functional world into the imperative world. By default, effects run after every completed render, but you can choose to fire them only when certain values have changed.

```js
useEffect(didUpdate);
```

`useContext` - accepts a context object (the value returned from React.createContext) and returns the current context value for that context. 

```js
const value = useContext(MyContext);
```

### [!] How to solve the Props Drilling - threading issue

The problem occurs when we are trying to passing props throught more than 2 components. Possible fixes:

1. Use Context API
```js
export const TodoContext = createContext({});
<TodoContext.Provider (...)>
```
2. Render Props

The technique for sharing code between React components using a prop whose value is a function. A component with a render prop takes a function that returns a React element and calls it instead of implementing its own render logic.

```js
<DataProvider render={data => (
  <h1>Hello {data.target}</h1>
)}/>
```

### [!] What is redux selectors?

- Selectors can compute derived data, allowing Redux to store the minimal possible state.
- Selectors are efficient. A selector is not recomputed unless one of its arguments changes.
- Selectors are composable. They can be used as input to other selectors.

Implementation with `reselect` library.
