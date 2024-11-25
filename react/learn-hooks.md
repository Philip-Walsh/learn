# React Hooks: A Beginner's Guide

In this article, we'll explore **React Hooks**—`useState`, `useEffect`, `useMemo`, and `useRef`. These hooks allow you to manage state, handle side effects, optimize performance, and interact with the DOM in functional components. Let's dive in and understand how to use them effectively in your React projects.

## Table of Contents

1. [useState - Managing Component State](#usestate)
2. [useEffect - Handling Side Effects](#useeffect)
3. [useMemo - Optimizing Performance](#usememo)
4. [useRef - Accessing DOM Elements](#useref)
5. [Conclusion](#conclusion)

---

### 1. **useState - Managing Component State** 

`useState` lets you add state to functional components. It's perfect for storing and updating data that changes during the component's lifecycle, like form inputs, counters, or toggles.

#### Syntax:
```javascript
const [state, setState] = useState(initialValue);
```
- `state`: Current value of the state.
- `setState`: Function to update the state.
- `initialValue`: Initial value for the state.

#### Example:

```jsx
import React, { useState } from 'react';

const Counter = () => {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <button onClick={() => setCount(count - 1)}>Decrement</button>
    </div>
  );
};
```
#### [Live Demo on CodePen](https://codepen.io/Philip-Walsh/pen/YPKKrJP)

---

### 2. **useEffect - Handling Side Effects** 

`useEffect` is used for side effects such as fetching data, subscribing to services, or setting up event listeners. By default, it runs after every render, but you can control when it runs with dependency arrays.

#### Syntax:
```javascript
useEffect(() => {
  // Side effect logic
  return () => {
    // Cleanup logic
  };
}, [dependencies]);
```
- **cleanup function**: Runs when the component unmounts or before the effect re-runs.
- **dependencies array**: Tells React when to re-run the effect.

#### Example:

```jsx
import React, { useState, useEffect } from 'react';

const Timer = () => {
  const [seconds, setSeconds] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => setSeconds(prev => prev + 1), 1000);
    return () => clearInterval(interval);
  }, []);

  return <h1>{seconds} seconds</h1>;
};
```
#### [Live Demo on CodePen](https://codepen.io/Philip-Walsh/pen/bNbbomW)

---

### 3. **useMemo - Optimizing Performance**

`useMemo` memoizes expensive calculations, preventing unnecessary recalculations on every render. It's ideal for performance optimization when dealing with heavy computations.

#### Syntax:
```javascript
const memoizedValue = useMemo(() => expensiveCalculation(), [dependencies]);
```
- **memoizedValue**: The result of the memoized computation.
- **dependencies**: Values that trigger recalculation.

#### Example:

```jsx
import React, { useState, useMemo } from 'react';

const Fibonacci = ({ n }) => {
  const calculateFibonacci = (n) => {
    if (n <= 1) return n;
    return calculateFibonacci(n - 1) + calculateFibonacci(n - 2);
  };

  const fibonacci = useMemo(() => calculateFibonacci(n), [n]);

  return <h1>Fibonacci of {n} is {fibonacci}</h1>;
};
```
#### [Live Demo on CodePen](https://codepen.io/Philip-Walsh/pen/bNbboQW)

---

### 4. **useRef - Accessing DOM Elements**

`useRef` is used to reference DOM elements or store mutable values that don’t trigger re-renders. It’s commonly used for focusing inputs or measuring element dimensions.

#### Syntax:
```javascript
const ref = useRef(initialValue);
```
- **ref**: A mutable object storing the current reference.

#### Example:

```jsx
import React, { useRef } from 'react';

const FocusInput = () => {
  const inputRef = useRef(null);

  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={() => inputRef.current.focus()}>Focus Input</button>
    </div>
  );
};
```
#### [Live Demo on CodePen](https://codepen.io/Philip-Walsh/pen/zxOOEmM)

---

### Conclusion

React hooks like `useState`, `useEffect`, `useMemo`, and `useRef` empower you to manage component state, handle side effects, optimize performance, and interact with the DOM in a more intuitive way. Mastering these hooks will help you write cleaner, more efficient React code.

By incorporating these hooks into your workflow, you'll be able to build more powerful and maintainable React applications. Happy coding!

- [useState Demo](https://codepen.io/Philip-Walsh/pen/YPKKrJP)
- [useEffect Demo](https://codepen.io/Philip-Walsh/pen/bNbbomW)
- [useMemo Demo](https://codepen.io/Philip-Walsh/pen/bNbboQW)
- [useRef Demo](https://codepen.io/Philip-Walsh/pen/zxOOEmM)