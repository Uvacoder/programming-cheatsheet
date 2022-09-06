---
sidebar_position: 1
---

# General

## React Context

<https://kentcdodds.com/blog/how-to-use-react-context-effectively>
<https://www.freecodecamp.org/news/react-context-for-beginners>
<https://blog.logrocket.com/react-context-api-deep-dive-examples/>

## Topics

ReactJS Reconciliation
react context
arrow functions in render are not fine only if component is memoized
rebase vs merge
<https://refactoring.guru/pl/design-patterns/decorator/typescript/example>

## Momoization

// <https://www.youtube.com/watch?v=DEPwA3mv_R8>
// useMemo is working with object and arrays
// useCallback is working with functions

```js
import React from "react";
import "./styles.css";

const Title = ({ title, color }) => {
  console.log("render title");
  return (
    <div style={{ color: color }}>
      <h1>{title}</h1>
    </div>
  );
};

const Color = React.memo(({ params }) => {
  console.log("render color");
  return (
    <div
      style={{
        width: "50px",
        height: "50px",
        backgroundColor: params.colorPrimary.colorSecondary.color
      }}
    />
  );
});

export default function App() {
  const [title, setTitle] = React.useState(0);
  const [color, setColor] = React.useState("red");

  const changeTitle = () => {
    setTitle(title + 1);
  };

  const changeColor = () => {
    setColor(color === "red" ? "blue" : "red");
  };

  const onColorClick = React.useCallback(() => {}, []);
  const colorParams = React.useMemo(
    () => ({
      colorPrimary: {
        colorSecondary: {
          color
        }
      }
    }),
    [color]
  );

  return (
    <div className="App">
      <div style={{ display: "flex", justifyContent: "center" }}>
        <Title color={color} title={title} />
      </div>
      <div style={{ display: "flex", justifyContent: "center" }}>
        <Color params={colorParams} onClick={onColorClick} />
      </div>
      <button onClick={changeTitle}>+</button>
      <button onClick={changeColor}>color</button>
    </div>
  );
}
```
