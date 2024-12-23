# ReactJsInterviewQuestions
Here are detailed answers for the **React Basics** questions:

---

### **1. What is React, and why is it used?**
React is a **JavaScript library** developed by Facebook for building **user interfaces**, especially for single-page applications. It is used to:
- **Build dynamic web applications**: React updates and renders only the necessary parts of the UI, making it efficient for interactive interfaces.
- **Component-based architecture**: Code can be broken into reusable pieces, simplifying development and testing.
- **Declarative UI**: Developers define the UI, and React ensures it reflects the underlying application state.

---

### **2. What are the major features of React?**
Key features of React include:
1. **Declarative UI**: Describes what the UI should look like for a given state.
2. **Component-based architecture**: Encapsulates logic and UI into reusable building blocks.
3. **Virtual DOM**: Minimizes updates to the real DOM for better performance.
4. **Unidirectional data flow**: Ensures a predictable data structure with controlled state management.
5. **JSX syntax**: Allows writing HTML-like syntax directly in JavaScript.
6. **Rich ecosystem**: Includes hooks, libraries like React Router, and tools like Redux for state management.

---

### **3. What is JSX?**
JSX (JavaScript XML) is a **syntax extension for JavaScript** that looks like HTML. It allows developers to write UI components in a way that closely resembles HTML.

For example:
```jsx
const element = <h1>Hello, World!</h1>;
```
JSX is transformed into JavaScript by tools like Babel:
```javascript
const element = React.createElement('h1', null, 'Hello, World!');
```

---

### **4. Why can’t browsers read JSX directly?**
Browsers can’t read JSX because it is not valid JavaScript. JSX needs to be **transpiled** into JavaScript code using tools like **Babel** or **Webpack** before browsers can interpret it.

For instance:
```jsx
const element = <h1>Hello, World!</h1>;
```
is transpiled to:
```javascript
const element = React.createElement('h1', null, 'Hello, World!');
```

---

### **5. What is the Virtual DOM?**
The **Virtual DOM** is a lightweight representation of the real DOM. It is a **JavaScript object** that React uses to optimize updates to the real DOM.

**How it works**:
1. When the state of a component changes, React creates a new virtual DOM tree.
2. React compares the new tree with the previous one (a process called **reconciliation**).
3. React updates only the necessary elements in the real DOM.

This minimizes direct manipulation of the real DOM, improving performance.

---

### **6. Explain the difference between Real DOM and Virtual DOM.**

| **Feature**          | **Real DOM**                              | **Virtual DOM**                          |
|-----------------------|-------------------------------------------|------------------------------------------|
| **Update**            | Updates the entire tree                  | Updates only the changed elements        |
| **Performance**       | Slow due to direct manipulation          | Fast due to minimal DOM operations       |
| **Usage**             | Standard in web development              | Used internally by React for optimization|
| **Cost**              | More memory-intensive due to large trees | Lightweight JavaScript objects           |

---

### **7. What are React components?**
React components are **independent, reusable pieces of UI** that return JSX to render.

Example of a component:
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}!</h1>;
}
```
Types of components:
1. **Functional components**: Use functions to define UI.
2. **Class components**: Use ES6 classes to define UI.

---

### **8. What are the types of components in React?**
React components can be broadly classified into:

1. **Functional Components**:
   - Written as JavaScript functions.
   - Can use hooks for state and lifecycle management.
   - Example:
     ```jsx
     function Greeting(props) {
       return <h1>Hello, {props.name}!</h1>;
     }
     ```

2. **Class Components**:
   - Defined as ES6 classes.
   - Use lifecycle methods and `this.state` for state management.
   - Example:
     ```jsx
     class Greeting extends React.Component {
       render() {
         return <h1>Hello, {this.props.name}!</h1>;
       }
     }
     ```

---

### **9. What is the difference between a functional and a class component?**

| **Aspect**            | **Functional Component**                  | **Class Component**                      |
|-----------------------|-------------------------------------------|------------------------------------------|
| **Definition**         | JavaScript function                      | ES6 class                                |
| **State Management**   | Uses `useState` and other hooks          | Uses `this.state`                        |
| **Lifecycle Methods**  | Uses hooks like `useEffect`              | Uses methods like `componentDidMount`    |
| **Performance**        | Faster and simpler                       | Slightly slower due to `this` binding    |
| **Syntax**             | Concise and modern                       | Verbose                                  |

---

### **10. What is the significance of the `key` prop in React?**
The `key` prop is used by React to identify elements in a list. It helps React efficiently update and render components.

**Why it’s important**:
- Helps React track changes (additions, removals, or reorders) in a list.
- Improves performance during reconciliation.

Example:
```jsx
const items = ['Apple', 'Banana', 'Cherry'];
const list = items.map((item, index) => <li key={index}>{item}</li>);
```

**Best practices**:
- Use a unique and stable identifier (e.g., database IDs) as the `key`.
- Avoid using array indices as keys unless the list is static.

--- 


### **11. What is state in React?**
State is a built-in object in React used to store and manage data that changes over time in a component. It is:
- **Mutable**: Can be updated within the component.
- **Component-specific**: Each component has its own state.
- Used to trigger re-renders when updated.

Example:
```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

---

### **12. What are props in React?**
Props (short for properties) are used to pass data from one component to another, typically from a parent to a child. They are:
- **Immutable**: Cannot be modified by the receiving component.
- **Read-only**: Used to configure or display data within a child component.

Example:
```jsx
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

function App() {
  return <Greeting name="John" />;
}
```

---

### **13. What is the difference between state and props?**

| **Aspect**            | **State**                                 | **Props**                                 |
|-----------------------|-------------------------------------------|------------------------------------------|
| **Definition**         | Internal data managed by a component      | Data passed to a component from its parent |
| **Mutability**         | Mutable (can be updated)                 | Immutable (read-only)                    |
| **Scope**              | Local to the component                   | Can be accessed by child components      |
| **Usage**              | Used for dynamic data                    | Used to pass data between components     |

---

### **14. Can you modify props in React?**
No, props are **read-only** and cannot be modified by the receiving component. Attempting to modify props results in an error. Props ensure that components remain predictable and follow React’s unidirectional data flow.

For instance:
```jsx
function Child(props) {
  // This is not allowed:
  // props.name = 'New Name';
  
  return <h1>{props.name}</h1>;
}
```

If you need to modify the data, manage it in the parent component's state and pass it down as props.

---

### **15. How do you pass data from a parent to a child component?**
Data is passed from a parent to a child component using **props**. 

Example:
```jsx
function Child(props) {
  return <h1>Hello, {props.name}!</h1>;
}

function Parent() {
  return <Child name="Alice" />;
}
```
In this case, the `Parent` component passes the `name` prop to the `Child` component.

---

### **16. How do you manage state in a functional component?**
Functional components use the `useState` hook to manage state. The `useState` hook returns an array with two elements:
1. The current state.
2. A function to update the state.

Example:
```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

---

### **17. What is the use of `useState` in React?**
The `useState` hook is used in functional components to manage state. It allows you to:
- Declare state variables.
- Update the state.
- Trigger re-renders when state changes.

Example:
```jsx
const [state, setState] = useState(initialValue);
```
Where:
- `state` is the current state value.
- `setState` is a function used to update the state.

---

### **18. What is the difference between controlled and uncontrolled components?**

| **Aspect**            | **Controlled Component**                  | **Uncontrolled Component**               |
|-----------------------|-------------------------------------------|------------------------------------------|
| **Definition**         | Component controls the input's value     | DOM manages the input's value            |
| **Data Source**        | State in React                           | Reference to the DOM element             |
| **Example**            | `<input value={value} onChange={handler}/>` | `<input defaultValue="value" />`        |
| **Use Case**           | Preferred for form validation            | Used for simpler scenarios               |

Controlled Component Example:
```jsx
function ControlledInput() {
  const [value, setValue] = useState('');
  
  return <input value={value} onChange={(e) => setValue(e.target.value)} />;
}
```

Uncontrolled Component Example:
```jsx
function UncontrolledInput() {
  const inputRef = React.useRef();
  
  return <input defaultValue="Default" ref={inputRef} />;
}
```

---

### **19. How do you lift state up in React?**
Lifting state up means moving the shared state to the nearest common ancestor of components that need access to it. This approach ensures that components receive data via props.

Example:
```jsx
function Parent() {
  const [value, setValue] = useState('');
  
  return (
    <div>
      <ChildA value={value} setValue={setValue} />
      <ChildB value={value} />
    </div>
  );
}

function ChildA({ value, setValue }) {
  return <input value={value} onChange={(e) => setValue(e.target.value)} />;
}

function ChildB({ value }) {
  return <p>{value}</p>;
}
```

---

### **20. What is the purpose of default props in React?**
Default props are used to set default values for props when they are not explicitly provided. This ensures that the component has meaningful values even if the parent does not pass props.

Example:
```jsx
function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}

Greeting.defaultProps = {
  name: 'Guest',
};
```
Here, if `name` is not passed, it defaults to `'Guest'`.

---

### **3. Lifecycle Methods**


---

### **21. What are React lifecycle methods?**
React lifecycle methods are special methods that get called at different stages of a component’s life: from creation to update and finally to removal from the DOM. These methods allow you to run specific code at various points in the component’s lifecycle. In class components, lifecycle methods are integral to managing side effects, such as fetching data, updating the UI, and cleaning up resources.

### **22. List the phases of the React component lifecycle.**
React component lifecycle is divided into three main phases:
1. **Mounting**: The phase when the component is being created and inserted into the DOM. Lifecycle methods: `constructor`, `getDerivedStateFromProps`, `render`, `componentDidMount`.
2. **Updating**: The phase when a component’s state or props change, leading to a re-render. Lifecycle methods: `getDerivedStateFromProps`, `shouldComponentUpdate`, `render`, `getSnapshotBeforeUpdate`, `componentDidUpdate`.
3. **Unmounting**: The phase when the component is being removed from the DOM. Lifecycle method: `componentWillUnmount`.

---

### **23. What is the `componentDidMount` method used for?**
The `componentDidMount` method is called once, immediately after the component is mounted (added to the DOM). It is commonly used for:
- **Data fetching**: Making API calls.
- **Event listeners**: Adding event listeners or subscriptions.
- **Setting up external libraries**: For example, initializing third-party libraries.
  
Example:
```jsx
componentDidMount() {
  fetch('/api/data')
    .then((response) => response.json())
    .then((data) => this.setState({ data }));
}
```

---

### **24. What is the purpose of `shouldComponentUpdate`?**
The `shouldComponentUpdate` method allows you to prevent unnecessary re-renders by comparing the current and next props or state. It returns a boolean value (`true` to update, `false` to skip the update). It’s particularly useful for performance optimization.

Example:
```jsx
shouldComponentUpdate(nextProps, nextState) {
  if (this.state.count === nextState.count) {
    return false;  // Prevent re-render if the count hasn't changed
  }
  return true;
}
```

---

### **25. What happens in the `componentWillUnmount` method?**
The `componentWillUnmount` method is called just before a component is removed from the DOM. This is the ideal place to:
- **Clean up timers**: Clear intervals or timeouts.
- **Remove event listeners**: Unsubscribe from external libraries or remove event listeners.
- **Cancel network requests**: If necessary, abort or cancel API calls.

Example:
```jsx
componentWillUnmount() {
  clearInterval(this.timerID);  // Clear any ongoing timer
}
```

---

### **26. How is the `getDerivedStateFromProps` method used?**
The `getDerivedStateFromProps` method is a static method that gets called before every render, both when the component is receiving new props and when the state is updated. It allows you to update the state based on the incoming props. This is a replacement for the old `componentWillReceiveProps` method.

It has the following signature:
```jsx
static getDerivedStateFromProps(nextProps, nextState) {
  // Logic to update state based on props
  return { derivedState: nextProps.value };
}
```

---

### **27. What replaced `componentWillReceiveProps` in React 16.3?**
In React 16.3, `componentWillReceiveProps` was deprecated and replaced with the `getDerivedStateFromProps` method. While `componentWillReceiveProps` was invoked before each render when props changed, `getDerivedStateFromProps` is now the preferred way to manage state updates based on props changes in class components.

---

### **28. What is the difference between `componentDidUpdate` and `componentWillUpdate`?**

| **Aspect**              | **componentDidUpdate**                        | **componentWillUpdate**                     |
|-------------------------|-----------------------------------------------|--------------------------------------------|
| **When it's called**    | After the component has re-rendered (post-update) | Before the component re-renders (pre-update) |
| **Purpose**              | Used to perform side effects after updates (e.g., fetching new data, updating the DOM) | Deprecated in React 16.3; not used anymore |
| **Availability of props/state** | Both the current and previous props/state are available | Only the next props/state are available |

`componentWillUpdate` is deprecated because it can lead to potential issues with async rendering, so `componentDidUpdate` is preferred for performing tasks after updates.

---

### **29. Can you use lifecycle methods in functional components?**
No, lifecycle methods are specific to **class components**. However, in **functional components**, React introduced **hooks** that replicate lifecycle behaviors. The most commonly used hook for lifecycle-like behavior is `useEffect`.

For example:
- **componentDidMount** → `useEffect` with an empty dependency array (`[]`).
- **componentDidUpdate** → `useEffect` with dependencies.
- **componentWillUnmount** → Return a cleanup function inside `useEffect`.

Example of `useEffect`:
```jsx
useEffect(() => {
  // This runs once after the component mounts
  fetchData();
  return () => {
    // Cleanup code, runs when the component unmounts
    cancelFetchRequest();
  };
}, []);  // Empty array means it runs only once
```

---

### **30. How do React hooks replace lifecycle methods?**

React hooks were introduced to handle side effects and lifecycle-related logic in **functional components**. They offer a more concise and reusable way of managing lifecycle behaviors:

- **`useEffect`**: Replaces several lifecycle methods like `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`.
  - **`componentDidMount`**: Use `useEffect` with an empty dependency array (`[]`).
  - **`componentDidUpdate`**: Use `useEffect` with specific dependencies.
  - **`componentWillUnmount`**: Use the cleanup function returned by `useEffect`.
  
Example:
```jsx
import { useEffect } from 'react';

function Example() {
  useEffect(() => {
    // This acts like componentDidMount
    console.log('Component mounted');

    return () => {
      // This acts like componentWillUnmount
      console.log('Component unmounted');
    };
  }, []);  // Empty array means it runs once after the initial render

  return <div>Example Component</div>;
}
```
---
## **4. React Hooks**

---


### **31. What are React hooks?**
React hooks are functions that allow you to use state and other React features in **functional components**. Before hooks, state and lifecycle methods were only available in **class components**. Hooks allow you to manage state, side effects, context, and other behaviors without writing class-based components. React hooks were introduced in React 16.8.

Common hooks include:
- `useState`: Manages state in functional components.
- `useEffect`: Handles side effects like data fetching and subscriptions.
- `useContext`: Accesses the context API.
- `useRef`: Manages mutable references.
- `useReducer`: Manages more complex state logic.
- `useMemo` and `useCallback`: Optimizes performance by memoizing values and functions.

---

### **32. What are the rules of hooks?**
React hooks follow a set of rules to ensure they work correctly and predictably:
1. **Only call hooks at the top level**: Do not call hooks inside loops, conditions, or nested functions. Hooks should always be called at the top level of your component to ensure the same order every time the component renders.
2. **Only call hooks from React functions**: You can call hooks only from React function components or custom hooks. They cannot be called from regular JavaScript functions or class components.
3. **Use hooks in functional components or custom hooks**: Hooks should only be used inside functional components or other custom hooks, not in class components.

---

### **33. What is the purpose of the `useEffect` hook?**
The `useEffect` hook is used to handle side effects in functional components, such as:
- Fetching data from an API.
- Updating the DOM directly.
- Subscribing to events.
- Setting up timers or intervals.
- Cleaning up resources before the component unmounts.

`useEffect` is similar to lifecycle methods in class components, like `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`.

Example:
```jsx
useEffect(() => {
  fetchData();
  return () => {
    cleanUpData();
  };
}, [dependency]);  // Runs when 'dependency' changes
```

---

### **34. How does the `useContext` hook work?**
The `useContext` hook allows you to consume context values in a functional component. Context provides a way to pass data through the component tree without having to pass props manually at every level. 

To use `useContext`, you first create a context with `React.createContext`, then access the context in any functional component using `useContext`.

Example:
```jsx
const ThemeContext = React.createContext('light');

function ThemedComponent() {
  const theme = useContext(ThemeContext);  // Consume the context
  return <div className={theme}>Themed Component</div>;
}

// Parent component
function App() {
  return (
    <ThemeContext.Provider value="dark">
      <ThemedComponent />
    </ThemeContext.Provider>
  );
}
```

---

### **35. What is the difference between `useEffect` and `componentDidMount`?**
- **`componentDidMount`**: It is a lifecycle method in class components, which runs once after the component is mounted (rendered) for the first time. It is used to perform operations like data fetching or setting up subscriptions.
- **`useEffect`**: In functional components, `useEffect` can replicate `componentDidMount` behavior. It runs after the first render, and you can use an empty dependency array `[]` to ensure it runs only once (just like `componentDidMount`).

Example:
```jsx
useEffect(() => {
  // Runs once, similar to componentDidMount
  fetchData();
}, []);  // Empty array ensures it runs only once
```

---

### **36. How do you manage state with `useReducer`?**
The `useReducer` hook is an alternative to `useState` for managing more complex state logic, especially when the state depends on previous values or when you have multiple state variables that are updated in different ways. It works by dispatching actions to a reducer function, which returns the updated state.

Example:
```jsx
const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      return state;
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>Increment</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>Decrement</button>
    </div>
  );
}
```

---

### **37. What is the `useRef` hook used for?**
The `useRef` hook is used to persist values across renders and to access DOM elements directly. Unlike `useState`, `useRef` does not trigger a re-render when the value changes. It is useful for:
- Accessing DOM elements (e.g., input fields, buttons).
- Keeping a mutable reference to a value that does not require re-rendering.
- Storing values across renders without causing unnecessary re-renders.

Example:
```jsx
function Timer() {
  const timerId = useRef(null);

  useEffect(() => {
    timerId.current = setInterval(() => console.log('Tick'), 1000);
    return () => clearInterval(timerId.current);
  }, []);

  return <div>Timer is running</div>;
}
```

---

### **38. Explain the difference between `useState` and `useReducer`.**
- **`useState`**: Ideal for managing simple, local state in functional components. It is easier to use for small state logic that doesn't involve complex state transformations.
- **`useReducer`**: Used for managing more complex state logic where the next state depends on the previous state. It is often used in situations where multiple sub-values or state updates are involved or when actions are dispatched with different types.

Example:
- `useState`: Simple state updates, e.g., a counter.
- `useReducer`: More complex updates, e.g., managing form state with multiple fields or handling actions like `increment`, `decrement`, etc.

---

### **39. What is the `useMemo` hook, and why is it used?**
The `useMemo` hook is used to **memoize** expensive calculations, ensuring that they are only recalculated when their dependencies change. It helps improve performance by preventing unnecessary re-calculations on every render.

Example:
```jsx
const memoizedValue = useMemo(() => expensiveCalculation(a, b), [a, b]);
```
This ensures that `expensiveCalculation` is only re-run when `a` or `b` changes, improving performance.

---

### **40. What is the difference between `useCallback` and `useMemo`?**
- **`useMemo`**: Memoizes the **result** of a function, ensuring the result is recalculated only when specific dependencies change. It is useful for optimizing expensive calculations.
- **`useCallback`**: Memoizes the **function itself**, ensuring that the function reference does not change unless its dependencies change. It is useful when passing functions as props to child components to prevent unnecessary re-renders.

Example of `useCallback`:
```jsx
const memoizedCallback = useCallback(() => {
  doSomething();
}, [dependency]);
```

---

### **5. Event Handling**

---


### **41. How does event handling work in React?**
Event handling in React works similarly to DOM event handling in JavaScript, but with some differences:
1. React uses **synthetic events**, which are wrapped around the browser’s native events to ensure consistent behavior across different browsers.
2. In React, event handlers are passed as **camelCase** properties (e.g., `onClick`, `onChange`).
3. React automatically binds event handlers to the component instance in class components. In functional components, you can use arrow functions or bind the event handler to the component instance if necessary.

Example:
```jsx
function handleClick() {
  console.log('Button clicked');
}

<button onClick={handleClick}>Click Me</button>
```

---

### **42. What is the significance of synthetic events in React?**
Synthetic events are a cross-browser wrapper around the browser’s native events. React creates synthetic events to ensure that events are normalized and have consistent behavior, regardless of the browser. They are part of the React event system and are more efficient than native DOM events because React manages event delegation efficiently.

**Advantages**:
- Cross-browser compatibility.
- Improved performance with event delegation.
- Synthetic events follow the same API as native events, making it easy to work with.

---

### **43. How do you bind events in React?**
In React class components, you can bind event handlers to the component instance by either using the **constructor** or by using **public class fields** (arrow functions). In functional components, event handlers can be written as arrow functions or functions defined within the component.

**Example in class component**:
```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    console.log('Button clicked');
  }

  render() {
    return <button onClick={this.handleClick}>Click Me</button>;
  }
}
```

**Example in functional component**:
```jsx
function MyComponent() {
  const handleClick = () => {
    console.log('Button clicked');
  };

  return <button onClick={handleClick}>Click Me</button>;
}
```

---

### **44. What are event pooling and its implications in React?**
Event pooling is a technique used by React to improve performance by reusing event objects instead of creating new ones for every event. This is done by **pooling** events and resetting their properties after the event handler is invoked. 

The implication is that you cannot directly access the event properties asynchronously (e.g., inside `setTimeout`) unless you call `e.persist()` to prevent React from recycling the event.

Example:
```jsx
function handleClick(e) {
  setTimeout(() => {
    console.log(e.type);  // Error without e.persist()
  }, 1000);
}
```
In the example above, you would need to call `e.persist()` to prevent React from clearing the event.

---

### **45. How do you prevent the default behavior of an event in React?**
To prevent the default behavior of an event (like preventing form submission or link navigation), you can call `e.preventDefault()` within the event handler, similar to how it works in plain JavaScript.

Example:
```jsx
function handleSubmit(e) {
  e.preventDefault();  // Prevents form submission
  console.log('Form submitted');
}

<form onSubmit={handleSubmit}>
  <button type="submit">Submit</button>
</form>
```

---

### **46. What is the difference between `onClick` in React and JavaScript?**
- In **JavaScript**, you add event listeners directly to DOM elements, and event handlers are passed as functions.
- In **React**, the event handler is passed as a camelCase property (e.g., `onClick`), and React handles event delegation for you by attaching the event listener at the root level of the DOM.

In JavaScript, you would add an event listener like this:
```javascript
document.getElementById('myButton').addEventListener('click', function() {
  alert('Button clicked');
});
```

In React, you do it as follows:
```jsx
<button onClick={() => alert('Button clicked')}>Click Me</button>
```

---

### **47. Can you pass parameters to event handlers in React?**
Yes, you can pass parameters to event handlers in React. The most common way to do this is by using an **arrow function** inside the `onClick` or other event handler attributes.

Example:
```jsx
function handleClick(id) {
  console.log(`Button ${id} clicked`);
}

<button onClick={() => handleClick(1)}>Click Me</button>
```

Alternatively, you can pass the event itself as a parameter:
```jsx
<button onClick={(e) => handleClick(e, 1)}>Click Me</button>
```

---

### **48. What is the purpose of the `e.persist()` method?**
`e.persist()` is used to **prevent React from resetting the event** after the event handler has been executed. Since React pools events for performance reasons, event properties are cleared after the handler finishes. If you need to access the event properties asynchronously (e.g., after a `setTimeout`), you must call `e.persist()` to keep the event alive.

Example:
```jsx
function handleClick(e) {
  e.persist();  // Prevent event pooling

  setTimeout(() => {
    console.log(e.type);  // Now you can access the event
  }, 1000);
}
```

---

### **49. How do you handle form submissions in React?**
In React, form submissions are handled in a way similar to handling any other event, but you need to prevent the default form submission behavior and handle it with React’s state management.

Example:
```jsx
function handleSubmit(e) {
  e.preventDefault();
  console.log('Form submitted');
}

function MyForm() {
  return (
    <form onSubmit={handleSubmit}>
      <button type="submit">Submit</button>
    </form>
  );
}
```

You can also handle form data by using `useState` or `useReducer` to track input field values.

---

### **50. What is the best way to manage multiple input fields in a form?**
To manage multiple input fields in a form, the best practice is to use controlled components, where the form field values are stored in the component’s state. You can either use `useState` in functional components or `setState` in class components. For handling complex forms with many inputs, you may also use `useReducer`.

Example using `useState`:
```jsx
function MyForm() {
  const [formData, setFormData] = useState({
    name: '',
    email: ''
  });

  const handleChange = (e) => {
    const { name, value } = e.target;
    setFormData(prevData => ({
      ...prevData,
      [name]: value
    }));
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log(formData);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        name="name"
        value={formData.name}
        onChange={handleChange}
      />
      <input
        type="email"
        name="email"
        value={formData.email}
        onChange={handleChange}
      />
      <button type="submit">Submit</button>
    </form>
  );
}
```

This pattern allows you to manage multiple form fields in a single state object, making it easier to handle and update each field.

---
### **6. React Routing**
---


### **51. What is React Router?**
React Router is a standard library for routing in React applications. It enables navigation among different views or components based on the URL. React Router allows you to create single-page applications (SPAs) where the page content changes dynamically without a full page reload. It maps URLs to specific components and helps manage navigation, paths, and redirects.

---

### **52. What are the differences between `BrowserRouter` and `HashRouter`?**
- **`BrowserRouter`**: Uses the HTML5 history API to create a clean and SEO-friendly URL (e.g., `/home`), which enables you to create dynamic URLs without the `#` symbol.
  - **Pros**: Clean URLs.
  - **Cons**: Requires server-side configuration to handle routes properly.
  
- **`HashRouter`**: Uses a hash (`#`) symbol in the URL (e.g., `/#/home`) to simulate different views. The part after the `#` is not sent to the server, so it's entirely client-side.
  - **Pros**: Doesn’t require server-side configuration, suitable for static sites.
  - **Cons**: URLs contain the `#`, making them less SEO-friendly.

---

### **53. How do you implement nested routes in React Router?**
Nested routes are routes within other routes, allowing for nested UI rendering. You can define nested routes by using the `Route` component inside another `Route` component's `element` prop, which renders child routes inside the parent route.

Example:
```jsx
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';

function ParentComponent() {
  return (
    <div>
      <h1>Parent</h1>
      <Routes>
        <Route path="child" element={<ChildComponent />} />
      </Routes>
    </div>
  );
}

function ChildComponent() {
  return <h2>Child</h2>;
}

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<ParentComponent />} />
      </Routes>
    </Router>
  );
}
```

---

### **54. What is the purpose of the `Switch` component in React Router?**
The `Switch` component is used to **render the first route that matches the current location**. It ensures that only one route is rendered at a time. When you have multiple routes, `Switch` will only display the route whose path matches the current URL.

Note: `Switch` is used in React Router v5 and below. In v6, `Switch` has been replaced by `Routes`.

Example in v5:
```jsx
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';

function App() {
  return (
    <Router>
      <Switch>
        <Route path="/home" component={Home} />
        <Route path="/about" component={About} />
      </Switch>
    </Router>
  );
}
```

---

### **55. What is the `Link` component used for in React Router?**
The `Link` component is used to **navigate between different routes** in a React application without causing a page reload. It renders an anchor (`<a>`) element that allows you to change the URL and trigger a route change.

Example:
```jsx
import { Link } from 'react-router-dom';

function App() {
  return (
    <div>
      <Link to="/home">Go to Home</Link>
      <Link to="/about">Go to About</Link>
    </div>
  );
}
```

---

### **56. What is the difference between `Link` and `NavLink`?**
- **`Link`**: A basic navigation component that renders a clickable link (`<a>` tag) to navigate to different routes in the app.
  
- **`NavLink`**: A specialized version of `Link` that allows you to style the active link differently. It has an `activeClassName` (v5) or `className` function in v6 to apply styles when the route is active.

Example with `NavLink`:
```jsx
import { NavLink } from 'react-router-dom';

function App() {
  return (
    <NavLink to="/home" activeClassName="active-link">
      Home
    </NavLink>
  );
}
```

---

### **57. How do you pass parameters in React Router?**
Parameters can be passed through the URL path by using **route parameters**. You define parameters in the route path with a colon (`:`) before the parameter name. These parameters can then be accessed in the component via the `useParams` hook.

Example:
```jsx
import { BrowserRouter as Router, Route, Routes, useParams } from 'react-router-dom';

function UserProfile() {
  const { userId } = useParams();
  return <h1>Profile of User {userId}</h1>;
}

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/user/:userId" element={<UserProfile />} />
      </Routes>
    </Router>
  );
}
```

In this example, if the URL is `/user/123`, the `UserProfile` component will render the text "Profile of User 123."

---

### **58. What is dynamic routing in React?**
Dynamic routing refers to the ability to create routes in React that can be defined at runtime. Instead of defining static routes at the beginning, dynamic routing allows routes to be created based on data or conditions that are available only when the app is running, such as fetching route configurations from a server or based on user authentication.

Example:
```jsx
function App() {
  const routes = [
    { path: "/home", component: <Home /> },
    { path: "/about", component: <About /> },
  ];

  return (
    <Router>
      <Routes>
        {routes.map((route, index) => (
          <Route key={index} path={route.path} element={route.component} />
        ))}
      </Routes>
    </Router>
  );
}
```

---

### **59. How do you handle redirection in React Router?**
To handle redirection, you can use the `useNavigate` hook (in v6) or `Redirect` component (in v5) in React Router. In v6, `useNavigate` is the recommended approach for programmatic navigation.

**Example with `useNavigate` (v6)**:
```jsx
import { useNavigate } from 'react-router-dom';

function RedirectToHome() {
  const navigate = useNavigate();
  
  useEffect(() => {
    navigate('/home');
  }, [navigate]);

  return <div>Redirecting...</div>;
}
```

**Example with `Redirect` (v5)**:
```jsx
import { Redirect } from 'react-router-dom';

function App() {
  return <Redirect to="/home" />;
}
```

---

### **60. What are the differences between v5 and v6 of React Router?**
React Router v6 introduces several breaking changes and new features:
1. **`Switch` is replaced with `Routes`**: In v6, `Switch` is replaced with `Routes`, which works similarly but renders only the first matching route and supports nested routes more easily.
2. **`component` prop is replaced with `element`**: In v6, the `component` prop for `Route` is replaced by `element`, where you pass a React element directly.
3. **`Redirect` is replaced with `Navigate`**: The `Redirect` component is replaced by the `Navigate` component for programmatic redirection.
4. **Improved handling of nested routes**: v6 allows more intuitive nested routing through the `element` prop.
5. **No more `exact` prop**: In v6, all routes are **exact by default**, so you no longer need to specify `exact`.

Example in v6:
```jsx
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/home" element={<Home />} />
      </Routes>
    </Router>
  );
}
```

In v5:
```jsx
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';

function App() {
  return (
    <Router>
      <Switch>
        <Route exact path="/home" component={Home} />
      </Switch>
    </Router>
  );
}
```

---
### **7. State Management**
---


### **61. What is Redux, and why is it used in React?**
Redux is a state management library that helps manage the application state in a predictable way. It is often used in React applications to maintain the application’s global state, especially in large-scale applications where multiple components need access to shared state. Redux works by storing the entire state of an application in a single, immutable store, and making state changes through actions and reducers. It is useful for managing complex state logic, ensuring predictable state transitions, and making state easy to debug.

---

### **62. What are the core principles of Redux?**
The core principles of Redux are:
1. **Single source of truth**: The entire application state is stored in a single JavaScript object (store). This makes it easier to manage and debug.
2. **State is read-only**: The only way to change the state is by dispatching an action, which is an object that describes what happened.
3. **Changes are made with pure functions (reducers)**: To specify how the state changes in response to an action, pure functions called reducers are used. A reducer takes the current state and the action, and returns a new state.

---

### **63. What is the difference between `useReducer` and Redux?**
`useReducer` is a React hook that is used for managing local component state in a similar manner to Redux. Both Redux and `useReducer` work on the concept of actions and reducers, but there are key differences:
- **Scope**: `useReducer` is used to manage state within a single component, whereas Redux is used to manage global state across the entire application.
- **Complexity**: Redux is more feature-rich and has more tools for handling large-scale state management (such as middleware and dev tools), while `useReducer` is simpler and is used mainly in smaller or isolated scenarios.
- **Store**: Redux has a central store, while `useReducer` manages state within individual components.

---

### **64. What is the purpose of middleware in Redux?**
Middleware in Redux is a layer that sits between the dispatching of an action and the moment it reaches the reducer. It is used to:
- **Extend Redux**: Middleware allows you to extend the behavior of Redux, such as adding logging, handling asynchronous actions (e.g., with Redux Thunk or Redux Saga), or transforming actions.
- **Intercept actions**: Middleware can modify or stop actions before they are processed by reducers, giving you more control over the flow of your application.
- **Side effects**: Middleware can be used to handle side effects like API calls, timers, or other asynchronous operations.

---

### **65. How do you connect Redux with a React application?**
To connect Redux with a React application, follow these steps:
1. **Install Redux**: Install `redux` and `react-redux` via npm/yarn.
   ```bash
   npm install redux react-redux
   ```
2. **Create the Redux store**: Define your reducers and create a store using `createStore`.
3. **Wrap the root component with `Provider`**: Use the `Provider` component from `react-redux` to make the Redux store available to all React components.
4. **Connect components**: Use `connect()` or hooks like `useSelector` and `useDispatch` to access and modify state from Redux in your React components.

Example:
```jsx
import { createStore } from 'redux';
import { Provider, connect } from 'react-redux';

// Reducer
function rootReducer(state = { count: 0 }, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    default:
      return state;
  }
}

// Create Redux store
const store = createStore(rootReducer);

// Component
function Counter({ count, increment }) {
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
}

// Map state and dispatch to props
const mapStateToProps = (state) => ({
  count: state.count,
});
const mapDispatchToProps = (dispatch) => ({
  increment: () => dispatch({ type: 'INCREMENT' }),
});

// Connect component to Redux
const ConnectedCounter = connect(mapStateToProps, mapDispatchToProps)(Counter);

// App Component
function App() {
  return (
    <Provider store={store}>
      <ConnectedCounter />
    </Provider>
  );
}
```

---

### **66. What is the difference between Redux and Context API?**
- **Scope**: Redux is meant for global state management and is better suited for large-scale applications with complex state logic. The Context API, on the other hand, is primarily for simpler use cases and smaller applications.
- **Performance**: Redux is more optimized for performance when dealing with large state updates. The Context API can cause unnecessary re-renders in the component tree when the context value changes.
- **Middleware**: Redux supports middleware (e.g., Redux Thunk, Redux Saga) for handling side effects and asynchronous actions, whereas the Context API doesn't have built-in middleware support.
- **State Management**: Redux follows a strict pattern with actions and reducers, making it more predictable and scalable. Context API is simpler and doesn’t enforce such a pattern.

---

### **67. What is the `connect` function in Redux?**
The `connect` function is a higher-order component (HOC) from `react-redux` that allows you to connect a React component to the Redux store. It maps the Redux state to component props and dispatches actions to update the store. It can be used for both functional and class components.

Example:
```jsx
import { connect } from 'react-redux';

function Counter({ count, increment }) {
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
}

const mapStateToProps = (state) => ({
  count: state.count,
});

const mapDispatchToProps = (dispatch) => ({
  increment: () => dispatch({ type: 'INCREMENT' }),
});

export default connect(mapStateToProps, mapDispatchToProps)(Counter);
```

---

### **68. What is the purpose of the `Provider` component in Redux?**
The `Provider` component from `react-redux` is used to provide the Redux store to the entire React component tree. It must wrap your root component, allowing all child components to access the store via `connect()` or hooks (`useSelector`, `useDispatch`).

Example:
```jsx
import { Provider } from 'react-redux';
import store from './store';

function App() {
  return (
    <Provider store={store}>
      <MyComponent />
    </Provider>
  );
}
```

---

### **69. What is Redux Toolkit, and how does it simplify state management?**
Redux Toolkit (RTK) is a set of utilities provided by Redux to simplify the Redux setup process. It aims to reduce the boilerplate code that developers need to write, making Redux easier to use. Some key features of Redux Toolkit:
- **`configureStore`**: Simplifies store setup by providing sensible defaults.
- **`createSlice`**: Combines reducers and actions into one entity to reduce boilerplate.
- **`createAsyncThunk`**: Simplifies handling of asynchronous actions (e.g., fetching data).
- **Redux DevTools**: Integrated by default in the configuration.

Example with `createSlice`:
```jsx
import { createSlice, configureStore } from '@reduxjs/toolkit';

const counterSlice = createSlice({
  name: 'counter',
  initialState: { count: 0 },
  reducers: {
    increment(state) {
      state.count += 1;
    },
    decrement(state) {
      state.count -= 1;
    },
  },
});

const store = configureStore({
  reducer: {
    counter: counterSlice.reducer,
  },
});

export default store;
```

---

### **70. How do you manage asynchronous actions in Redux?**
In Redux, asynchronous actions are typically handled using middleware like **Redux Thunk** or **Redux Saga**. 
- **Redux Thunk** allows action creators to return functions (thunks) instead of plain action objects. These functions can dispatch actions asynchronously.
- **Redux Saga** is a middleware that uses generators to manage side effects, making it more powerful for complex asynchronous flows.

Example with **Redux Thunk**:
```jsx
import { createStore, applyMiddleware } from 'redux';
import thunk from 'redux-thunk';

const fetchData = () => async (dispatch) => {
  dispatch({ type: 'FETCH_START' });
  try {
    const response = await fetch('/api/data');
    const data = await response.json();
    dispatch({ type: 'FETCH_SUCCESS', payload: data });
  } catch (error) {
    dispatch({ type: 'FETCH_ERROR', error });
  }
};

const store = createStore(reducer, applyMiddleware(thunk));
```

---

### **8. Performance Optimization**

---

### **71. What is React's reconciliation process?**
React's reconciliation process is the algorithm React uses to update the UI efficiently when the state or props of components change. When a component’s state changes, React compares the new virtual DOM with the previous one (diffing), and determines the minimal number of changes (or patches) required to update the real DOM. This is done in the following steps:
1. **Diffing**: React compares the old and new virtual DOMs and finds differences.
2. **Patching**: After finding the differences, React only updates the parts of the real DOM that have changed, rather than re-rendering the entire DOM.
3. **Reconciliation** ensures that the UI stays in sync with the component state while optimizing performance.

---

### **72. What are pure components in React?**
Pure components in React are components that only re-render when their props or state change. They are a way to optimize performance by reducing unnecessary re-renders. React’s `PureComponent` class implements `shouldComponentUpdate` with a shallow comparison of props and state. If neither the props nor the state change, the component will not re-render.

Example:
```jsx
import React, { PureComponent } from 'react';

class MyComponent extends PureComponent {
  render() {
    return <div>{this.props.value}</div>;
  }
}
```
Pure components are useful for functional components as well, which can be optimized using `React.memo`.

---

### **73. How does `React.memo` improve performance?**
`React.memo` is a higher-order component that wraps a functional component and prevents it from re-rendering if its props haven't changed. It performs a shallow comparison of the previous and next props, and only re-renders the component if there is a change in props. This helps to optimize performance, particularly in functional components where re-renders can be expensive.

Example:
```jsx
const MyComponent = React.memo(function MyComponent({ value }) {
  return <div>{value}</div>;
});
```
`React.memo` is particularly useful for functional components that render the same output for the same input props.

---

### **74. What is the purpose of the `shouldComponentUpdate` method?**
The `shouldComponentUpdate` method is a lifecycle method in class components that helps optimize performance by preventing unnecessary re-renders. It is called before the render method is executed and can return `true` (to allow re-rendering) or `false` (to prevent re-rendering). This method compares current props and state with the next ones to determine whether the component needs to update.

Example:
```jsx
shouldComponentUpdate(nextProps, nextState) {
  if (this.props.value !== nextProps.value) {
    return true; // Re-render if props change
  }
  return false; // Prevent re-render if props don't change
}
```

---

### **75. How does `useMemo` optimize performance in React?**
The `useMemo` hook helps optimize performance by memoizing the result of a function so that it is recomputed only when the dependencies change. This can prevent unnecessary recalculations of expensive operations on every render. `useMemo` is particularly useful for optimizing performance in components that perform complex computations or render large lists.

Example:
```jsx
const computedValue = useMemo(() => expensiveComputation(a, b), [a, b]);
```
In this example, `expensiveComputation(a, b)` will only be recalculated if `a` or `b` changes.

---

### **76. What are React fragments, and why are they used?**
React fragments are a way to group multiple elements without adding extra nodes to the DOM. They allow you to return multiple elements from a component’s render method without wrapping them in a parent element, such as a `<div>`. This can help reduce the number of unnecessary DOM nodes and keep the structure clean.

Example:
```jsx
return (
  <>
    <h1>Title</h1>
    <p>Content</p>
  </>
);
```
The shorthand syntax `<>...</>` is equivalent to `<React.Fragment>...</React.Fragment>`, and it helps in returning multiple children from a component without adding extra nodes.

---

### **77. How do you optimize rendering in React?**
To optimize rendering in React:
1. **Use React.memo**: Memoize functional components to avoid unnecessary re-renders when props haven't changed.
2. **Use PureComponent**: Use class components that automatically prevent re-renders when props or state haven't changed.
3. **Optimize component structure**: Break down large components into smaller, more manageable ones to optimize rendering and reduce unnecessary complexity.
4. **Avoid Inline Functions in JSX**: Inline functions cause unnecessary re-renders, as they create new function instances on every render.
5. **Lazy Loading**: Dynamically load components when required to reduce the initial load time.
6. **Use `useMemo` and `useCallback`**: Memoize values and functions to avoid recalculations or recreations on every render.
7. **Batching updates**: Use `ReactDOM.unstable_batchedUpdates` to batch multiple state updates into a single render.

---

### **78. What is the difference between lazy loading and code splitting?**
- **Lazy Loading** refers to the technique where content is loaded only when it is needed (on-demand). This helps improve the initial load performance by deferring the loading of components or data until they are actually required.
- **Code Splitting** involves breaking up the codebase into smaller chunks, so that only the required code for a particular route or feature is loaded at a time. This reduces the initial load time by loading smaller portions of the code.

In practice, React supports both through `React.lazy` and `Suspense` for lazy loading components, while tools like Webpack can handle code splitting.

---

### **79. What is the `React.lazy` function used for?**
`React.lazy` is a function that enables dynamic import of components. It allows you to load components lazily, i.e., only when they are required. It is often used in conjunction with `Suspense` to provide a loading indicator while the component is being loaded.

Example:
```jsx
const MyComponent = React.lazy(() => import('./MyComponent'));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <MyComponent />
    </Suspense>
  );
}
```
This approach improves the initial load time by only loading the component when it’s needed.

---

### **80. How does React handle high-frequency state updates?**
React handles high-frequency state updates through **batching**. When multiple state updates are triggered, React groups them into a single re-render to improve performance. React batches state updates to minimize the number of renders, reducing unnecessary UI reflows.

However, in cases of high-frequency updates (like animations or frequent event handling), React provides options such as:
- **Using `useCallback` and `useMemo`** to prevent unnecessary recalculations.
- **Throttling or debouncing** state updates when necessary to reduce the frequency of updates.
- **Avoiding unnecessary state updates** that don’t impact the rendering, and using `useRef` for values that don’t trigger a re-render.

React’s reconciliation process also ensures that only necessary changes are reflected in the UI, improving the performance of high-frequency state updates.

---
### **9. Testing in React**


---

### **81. What are the types of testing used in React applications?**
In React applications, the following types of testing are commonly used:
1. **Unit Testing**: Testing individual components or functions in isolation to ensure they work as expected. It typically involves testing small units of code like functions or methods.
2. **Integration Testing**: Testing multiple components or functions together to ensure they work as expected when combined.
3. **End-to-End (E2E) Testing**: Testing the entire application to ensure that all parts of the system work together correctly. Tools like Cypress or Selenium are often used.
4. **Snapshot Testing**: Checking if a component renders consistently over time by taking a "snapshot" of its rendered output.
5. **Functional Testing**: Testing the behavior and interaction of components based on user input and expected output.
6. **UI/Visual Testing**: Ensuring the user interface appears as expected, which can be done with tools like Storybook or visual regression tools.

---

### **82. What is the purpose of Jest in React testing?**
Jest is a testing framework maintained by Facebook that is commonly used for testing React applications. Its main purposes are:
1. **Test Runner**: Jest automatically finds and runs tests, reporting their results in an easy-to-understand format.
2. **Assertions**: Jest provides built-in functions like `expect()` for making assertions, simplifying testing.
3. **Mocking**: Jest provides a mocking utility that allows you to mock functions and modules for unit testing without involving real implementations.
4. **Snapshots**: Jest supports snapshot testing, which ensures that the UI remains consistent over time by comparing the rendered output of components.

Jest is often used with React Testing Library to test React components.

---

### **83. What is React Testing Library, and how does it differ from Enzyme?**
React Testing Library (RTL) is a library that encourages testing React components in a way that focuses on the behavior of the components as users would interact with them. It encourages tests to interact with components through their UI rather than directly testing the internal implementation.

Key differences between **React Testing Library** and **Enzyme**:
- **Enzyme**: Primarily allows shallow rendering and testing components in isolation. It gives direct access to component instances and allows testing the internal state and methods.
- **React Testing Library**: Focuses on testing the component from the user's perspective, interacting with it through DOM elements (like buttons, inputs, etc.), and encourages tests that focus on what the component does rather than how it does it.

**React Testing Library** provides utilities like `render()`, `screen`, and `fireEvent` for testing DOM elements in a way that simulates user interaction.

---

### **84. How do you test functional components in React?**
To test functional components in React, you generally follow these steps:
1. **Render the component**: Use the `render` function from React Testing Library to render the component in a virtual DOM.
2. **Interact with the component**: Simulate user actions using functions like `fireEvent`.
3. **Check for expected output**: Use assertions to check if the component's rendered output matches the expected result.

Example:
```jsx
import { render, screen, fireEvent } from '@testing-library/react';
import MyComponent from './MyComponent';

test('it displays the correct text', () => {
  render(<MyComponent />);
  expect(screen.getByText(/Hello, World!/i)).toBeInTheDocument();
});

test('it handles click events', () => {
  render(<MyComponent />);
  fireEvent.click(screen.getByText(/Click Me/i));
  expect(screen.getByText(/Clicked!/i)).toBeInTheDocument();
});
```

---

### **85. What is the `act` method in React Testing Library?**
The `act` method is used to ensure that all updates to the component’s state and effects are processed before making assertions. It is especially useful for handling asynchronous operations like state updates or effects that occur after rendering. 

`act` ensures that the test waits for React to finish all state updates, component re-renders, and side effects before performing any assertions.

Example:
```jsx
import { render, screen, act } from '@testing-library/react';

test('it updates the state after click', async () => {
  render(<MyComponent />);
  
  await act(async () => {
    fireEvent.click(screen.getByText('Click Me'));
  });

  expect(screen.getByText('Clicked!')).toBeInTheDocument();
});
```

---

### **86. How do you test state changes in React?**
To test state changes in React, you:
1. **Render the component**.
2. **Trigger the action** that causes the state change (e.g., a button click).
3. **Make assertions** to check the updated state’s effect on the rendered output.

Example:
```jsx
import { render, screen, fireEvent } from '@testing-library/react';
import MyComponent from './MyComponent';

test('it updates the state correctly', () => {
  render(<MyComponent />);
  fireEvent.click(screen.getByText('Increment'));
  expect(screen.getByText('Count: 1')).toBeInTheDocument();
});
```

---

### **87. What is snapshot testing, and how is it done in React?**
Snapshot testing in React involves taking a "snapshot" of the rendered output of a component and comparing it with a saved snapshot to ensure that the component's output doesn't change unexpectedly.

To perform snapshot testing with Jest:
1. **Render the component** using `render` from React Testing Library.
2. **Generate the snapshot** by calling `expect(tree).toMatchSnapshot()`.
3. **Jest will automatically compare the generated snapshot** with a previously stored snapshot and alert you if there are any differences.

Example:
```jsx
import { render } from '@testing-library/react';
import MyComponent from './MyComponent';

test('it matches the snapshot', () => {
  const { asFragment } = render(<MyComponent />);
  expect(asFragment()).toMatchSnapshot();
});
```

---

### **88. How do you mock API calls in React tests?**
You can mock API calls in React tests using Jest’s mocking functions, like `jest.fn()` or `jest.mock()`. The key is to replace the actual API call with a mock function that simulates the API response.

Example:
```jsx
import { render, screen, waitFor } from '@testing-library/react';
import MyComponent from './MyComponent';

jest.mock('./api', () => ({
  fetchData: jest.fn().mockResolvedValue({ data: 'Hello World' })
}));

test('it displays data from API', async () => {
  render(<MyComponent />);
  await waitFor(() => expect(screen.getByText('Hello World')).toBeInTheDocument());
});
```

---

### **89. What are the best practices for writing unit tests in React?**
Best practices for writing unit tests in React include:
1. **Test behavior, not implementation**: Write tests that check how components behave (i.e., what they render and how they respond to user input), not how they’re implemented.
2. **Keep tests isolated**: Avoid dependencies on external services or complex setups that can make tests brittle. Use mocks or stubs.
3. **Write meaningful assertions**: Ensure that your tests validate the expected output and behavior of components.
4. **Avoid testing implementation details**: Tests should not depend on internal details (like state or private methods).
5. **Use descriptive test names**: Name tests clearly to describe their purpose and what they are testing.
6. **Test edge cases**: Include tests that cover boundary conditions and unusual user interactions.

---

### **90. What is the purpose of `fireEvent` in React Testing Library?**
`fireEvent` is used to simulate user interactions in tests. It allows you to trigger events like clicks, changes, inputs, and more, on DOM elements rendered by React Testing Library.

Example:
```jsx
import { render, screen, fireEvent } from '@testing-library/react';

test('fires a click event', () => {
  render(<button onClick={() => console.log('clicked')}>Click Me</button>);
  fireEvent.click(screen.getByText('Click Me'));
  // Assertions can be added to verify expected outcomes
});
```

`fireEvent` is essential for testing how components respond to user interactions and simulate real-world usage.

---

### **10. Advanced React Concepts**

---

### **91. What is server-side rendering (SSR) in React?**
Server-Side Rendering (SSR) in React refers to the process where the React components are rendered on the server, and the resulting HTML is sent to the client. The main advantage of SSR is that it provides faster initial page load times, as the browser receives fully rendered HTML instead of waiting for JavaScript to download and render the page. SSR is commonly used in SEO-sensitive applications because search engines can crawl the pre-rendered HTML.

Tools like Next.js are popular for implementing SSR in React applications.

---

### **92. What is the difference between SSR and client-side rendering (CSR)?**
- **Server-Side Rendering (SSR)**: The initial rendering of the application is done on the server, and the HTML is sent to the browser. Afterward, React takes over on the client-side for subsequent interactions. SSR is faster for the first load and better for SEO because search engines can easily index server-rendered content.
- **Client-Side Rendering (CSR)**: In CSR, the initial HTML is minimal, and JavaScript is responsible for rendering the entire page on the client-side. This can result in slower initial load times since the browser must download and execute the JavaScript before rendering the page. However, CSR can offer smoother interactions after the initial load.

---

### **93. What is static site generation (SSG)?**
Static Site Generation (SSG) is a technique where HTML pages are generated at build time rather than on each request. The application is built into static files (HTML, CSS, JavaScript) that are ready to be served by a CDN. SSG is useful for content that doesn’t change frequently, providing fast load times and improved SEO.

Next.js supports SSG via `getStaticProps` for static data fetching during build time.

---

### **94. What is the purpose of Context API in React?**
The Context API in React provides a way to share data across components without having to explicitly pass props through every level of the component tree. It is particularly useful for global states like themes, authentication, and language preferences, which need to be accessible throughout the app.

React's Context API consists of:
1. **`React.createContext()`**: Creates a context object.
2. **Provider**: The component that supplies the context to its child components.
3. **Consumer**: The component that subscribes to the context and consumes the provided value.

---

### **95. What is React Concurrent Mode?**
React Concurrent Mode is an experimental feature that enables React to work on multiple tasks simultaneously by allowing it to split rendering work into chunks and prioritize the most important updates. This results in smoother user interactions, especially for complex applications. Concurrent Mode ensures that UI updates are responsive and don't block the main thread.

It is still an experimental feature and is available in newer versions of React under special flags.

---

### **96. What are portals in React, and how are they used?**
Portals in React provide a way to render children into a DOM node that exists outside the DOM hierarchy of the parent component. This is useful for rendering modals, tooltips, and dropdowns that should not be confined to their parent’s layout but still be part of the React component tree.

Example of using a portal:
```jsx
import ReactDOM from 'react-dom';

function Modal({ isOpen, children }) {
  if (!isOpen) return null;
  return ReactDOM.createPortal(
    children,
    document.getElementById('modal-root')
  );
}
```

---

### **97. What is React Fiber?**
React Fiber is the new reconciliation algorithm introduced in React 16 that improves the rendering performance and ensures that updates are processed efficiently. It allows React to split rendering work into chunks and prioritize updates, which leads to smoother animations and faster page loads. Fiber enables features like Suspense and Concurrent Mode.

Fiber provides fine-grained control over when and how the rendering process happens, allowing for better handling of complex user interactions and asynchronous rendering.

---

### **98. What are higher-order components (HOCs) in React?**
A Higher-Order Component (HOC) is a pattern in React where a function takes a component and returns a new component with additional props or functionality. HOCs are used for code reuse, logic encapsulation, and abstraction. They don’t modify the original component but rather enhance it with additional behavior.

Example of an HOC:
```jsx
function withLoading(Component) {
  return function WithLoading({ isLoading, ...props }) {
    if (isLoading) {
      return <div>Loading...</div>;
    }
    return <Component {...props} />;
  };
}
```

---

### **99. What are render props in React?**
Render props is a pattern in React where a component accepts a function as a prop, and that function returns a React element. This allows for greater flexibility by providing a way to pass down dynamic content or behavior to child components.

Example of a render prop:
```jsx
class MouseTracker extends React.Component {
  state = { x: 0, y: 0 };

  handleMouseMove = (event) => {
    this.setState({ x: event.clientX, y: event.clientY });
  };

  render() {
    return (
      <div onMouseMove={this.handleMouseMove}>
        {this.props.render(this.state)}
      </div>
    );
  }
}

<MouseTracker render={({ x, y }) => (
  <h1>The mouse position is ({x}, {y})</h1>
)} />
```

---

### **100. What is the purpose of error boundaries in React?**
Error boundaries are React components that catch JavaScript errors anywhere in their child component tree, log those errors, and display a fallback UI instead of crashing the entire app. This helps improve the stability and user experience of React applications by gracefully handling runtime errors.

Example:
```jsx
class ErrorBoundary extends React.Component {
  state = { hasError: false };

  static getDerivedStateFromError(error) {
    return { hasError: true };
  }

  componentDidCatch(error, info) {
    logErrorToMyService(error, info);
  }

  render() {
    if (this.state.hasError) {
      return <h1>Something went wrong.</h1>;
    }
    return this.props.children;
  }
}
```


Here are detailed answers to the 5 React interview questions focused on security:

---

### 1. **What are some common security vulnerabilities in React applications, and how would you mitigate them?**

**Common vulnerabilities in React applications:**
- **Cross-Site Scripting (XSS):** Malicious scripts injected into the application could steal cookies, session data, or perform unauthorized actions.
  - **Mitigation:** React automatically escapes data rendered via JSX, which helps protect against XSS attacks. Developers should avoid using `dangerouslySetInnerHTML`, as it can allow raw HTML to be injected. Any dynamic data should be sanitized and validated before being inserted into the DOM.
  
- **Cross-Site Request Forgery (CSRF):** Attackers can trick the user’s browser into making a request to a site where the user is authenticated, potentially leading to data manipulation or unauthorized actions.
  - **Mitigation:** Using anti-CSRF tokens in requests, ensuring sensitive endpoints require proper authentication, and relying on secure methods like HTTP-only cookies can help mitigate CSRF attacks. Many React applications use stateful authentication (e.g., JWT), which doesn't suffer from CSRF in the same way.

- **Insecure Deserialization:** Attackers may inject malicious payloads that are deserialized, potentially leading to arbitrary code execution.
  - **Mitigation:** Always validate and sanitize data before processing. Avoid accepting serialized objects directly from users unless necessary, and use libraries that provide safe parsing mechanisms.

- **Sensitive Data Exposure:** Storing sensitive data in unsafe places (e.g., localStorage or in URL parameters) can lead to data exposure.
  - **Mitigation:** Securely store sensitive information like tokens in HTTPOnly cookies (which can’t be accessed by JavaScript) instead of localStorage or sessionStorage.

---

### 2. **How do you handle sensitive data (e.g., authentication tokens) in a React application?**

**Handling sensitive data securely:**
- **JWT Tokens:** JSON Web Tokens (JWT) are commonly used for client-server authentication. When storing JWT tokens on the client side, it's important to use **HTTPOnly cookies** for secure storage, which prevents JavaScript access to the token, thus reducing the risk of XSS attacks.
  
- **Avoiding localStorage/sessionStorage:** Storing tokens in localStorage or sessionStorage exposes them to JavaScript, making them vulnerable to XSS attacks. HTTPOnly cookies provide a safer alternative, as they are automatically sent with requests and not directly accessible via JavaScript.

- **Token Expiration & Refresh:** Implement token expiration mechanisms to limit the lifespan of tokens. Use refresh tokens for long-lived sessions, where the client sends the refresh token to a secure endpoint to obtain a new access token without needing the user to log in again.

- **Secure Communication:** Always use **HTTPS** to transmit sensitive data, ensuring that tokens and other confidential information are encrypted during transmission.

---

### 3. **Explain how to protect against Cross-Site Scripting (XSS) attacks in a React application.**

**Protecting against XSS:**
- **React's built-in escaping:** React automatically escapes dynamic content inserted into JSX, preventing attackers from injecting scripts. For example:
  ```jsx
  <div>{userInput}</div>
  ```
  In this case, React automatically escapes any special characters in `userInput`, preventing malicious script execution.

- **Avoid `dangerouslySetInnerHTML`:** This method should only be used when absolutely necessary, as it can expose your application to XSS attacks. If you need to insert raw HTML, make sure it's sanitized and validated first.

- **Sanitize Input:** Use libraries like `DOMPurify` to sanitize input before inserting it into the DOM. This ensures that any potentially malicious content is cleaned before rendering.

- **Content Security Policy (CSP):** Implement a strict CSP to only allow scripts from trusted sources. This prevents unauthorized scripts from running, even if an attacker manages to inject them.

---

### 4. **What is Content Security Policy (CSP), and how can you implement it in a React app to enhance security?**

**Content Security Policy (CSP):**
- **What is it?** CSP is a browser security feature that helps prevent a wide range of attacks, such as XSS and data injection attacks, by specifying which sources the browser should allow for content (e.g., scripts, styles, images, etc.). It reduces the chances of unauthorized content being loaded or executed on a website.

- **How to implement it:**
  1. **Set the CSP Header:** In your server configuration, set the `Content-Security-Policy` header to define allowed sources.
     ```http
     Content-Security-Policy: default-src 'self'; script-src 'self' https://trusted-cdn.com; style-src 'self' https://trusted-cdn.com;
     ```
     This example allows only scripts and styles from the same origin and `https://trusted-cdn.com`.

  2. **Nonce-based CSP:** Use a nonce (number used once) for inline scripts to allow only scripts with a specific nonce to execute.
     ```html
     <script nonce="random-value">...</script>
     ```
     In the CSP header, you specify that only scripts with the given nonce are allowed to run.

  3. **Reporting:** Set up a reporting mechanism to monitor violations of the CSP policy.
     ```http
     Content-Security-Policy: default-src 'self'; report-uri /csp-violation-report-endpoint;
     ```

  CSP helps prevent malicious scripts from executing by blocking scripts that are not from trusted sources.

---
