1. **What is React, and how does it work?**

   - React is a JavaScript library used for building user interfaces. It allows we to create reusable UI components and manage the state of wer application efficiently. React uses a virtual DOM to optimize updates and render changes to the actual DOM.React follows a uni-deirectional data flow where data is passed from the parent component to the child component with the help of props.

2. **Explain the concept of the Virtual DOM in React.**

   - The Virtual DOM is a lightweight in-memory representation of the actual DOM. React uses it to improve performance by minimizing direct manipulation of the DOM. When there are updates in the application, React creates a virtual representation of the updated UI, compares it to the previous one, and then selectively updates only the changed parts in the real DOM. This process is more efficient and faster than re-rendering the entire DOM.

3. **What are React components?**

   - React components are reusable building blocks for creating user interfaces. They can be either class-based components or functional components. Components encapsulate their own logic, state, and UI rendering, making it easier to manage complex UIs.

4. **What is the difference between class components and functional components in React?**

   - Class components are JavaScript classes that extend `React.Component`. They have access to lifecycle methods and state management. Functional components, on the other hand, are plain JavaScript functions that receive props and return JSX. With the introduction of React Hooks, functional components can also manage state and have lifecycle-like features.

5. **What do we mean by lifecycle methods?**

   - In React, lifecycle methods are methods that are automatically invoked at different stages of a component's life, from its creation to its removal from the DOM. These methods allow we to hook into the component's behavior and perform actions at specific points in its lifecycle.
     Certainly, here's a concise explanation of the main React class-based component lifecycle methods:

   1. `constructor(props)`: Initialize state and bind event handlers.

   2. `render()`: Render the component's UI.

   3. `componentDidMount()`: Perform initial setup, like making API requests or setting up event listeners, after the component is inserted into the DOM.

   4. `shouldComponentUpdate(nextProps, nextState)`: Control when the component should re-render for performance optimization.

   5. `componentDidUpdate(prevProps, prevState)`: Handle post-update tasks, like making additional API requests or interacting with the DOM.

   6. `componentWillUnmount()`: Clean up resources, like removing event listeners, before the component is removed from the DOM.

   These methods help manage the component's lifecycle and behavior. However, keep in mind that React has evolved, and functional components with React Hooks are now more commonly used for similar functionality and are considered a best practice.

6. **Why it is advised to use functional components over the class components?**

   - Using functional components with hooks is advised over class components because functional components are simpler, more readable, promote code reusability, and are better for performance. They also align with React's current best practices and the evolving ecosystem.

7. **What are props in React, and how do we pass data from a parent to a child component?**

   - Props (short for properties) are a way to pass data from a parent component to a child component in React. we can pass data as attributes to a child component when rendering it. Inside the child component, we can access these props as properties of the `props` object.

8. **How can we pass props from the child component to the parent component in React?**
   -We can achieve this by using the concept of higher order function , first we create a function in the parent component (this function will be receiving the data from the parent), after that we pass this function to the child as a prop , and when the child wants to pass the data we can simply use that function.

9. **What do you mean by higher order function?**

   - In javascript and many other languages functions are also treated as normal variables or values , thus enabaling us to store functions in a variable and passing and returing functions as variables to other functions , some common examples of this are the map,filter and reduce methods , we take a function as a parameter.

   In short , A higher-order function is a function that can accept other functions as arguments or return functions as results.

10. **Explain state in React.**

- State is a built-in feature in React that allows components to manage and store their own data. It represents mutable data that can be changed over time, triggering re-renders when it's updated. State should be used for data that is specific to a single component and needs to be reactive.

11. **Explain react hooks.**

    - Hooks are a feature introduced in React 16.8 that allow functional components to manage state and side effects without the need for class components. They provide a way to "hook into" React state and lifecycle features from functional components, making it easier to reuse stateful logic and side effects.

    Here are some key aspects of hooks in React:

    1. **State Management with `useState`:**

    - The `useState` hook allows functional components to manage local component state. It returns an array with two elements: the current state value and a function to update it.
    - Example:

      ```jsx
      import React, { useState } from "react";

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

    2. **Managing Side Effects with `useEffect`:**

    - The `useEffect` hook allows functional components to perform side effects, such as data fetching, DOM manipulation, or subscribing to events, in a way that's safe and easy to reason about.
    - Example:

      ```jsx
      import React, { useState, useEffect } from "react";

      function Timer() {
        const [seconds, setSeconds] = useState(0);
        useEffect(() => {
          const intervalId = setInterval(() => {
            setSeconds((prevSeconds) => prevSeconds + 1);
          }, 1000);

          return () => {
            clearInterval(intervalId);
          };
        }, []); // Empty dependency array means the effect runs once on mount

        return <div>Seconds: {seconds}</div>;
      }
      ```

    3. **Custom Hooks:**

    - You can create your own custom hooks to encapsulate and share stateful logic between components. Custom hooks follow a naming convention of starting with "use" to indicate that they are hooks.
    - Example:

      ```jsx
      import { useState } from "react";

      function useToggle(initialState) {
        const [state, setState] = useState(initialState);

        const toggle = () => {
          setState((prevState) => !prevState);
        };

        return [state, toggle];
      }
      ```

    4. **Rules of Hooks:**

    - Hooks have specific rules and must be called at the top level of your functional component or custom hook, not inside loops, conditions, or nested functions.
    - This ensures that React can track the order and dependencies of hooks correctly.

    Hooks have significantly simplified state management and side effect handling in React, making functional components more powerful and easier to maintain. They are now the recommended way to work with state and side effects in React applications, and many existing class components have been rewritten as functional components using hooks.

12. **Explain how react manages the rendering process.**

    - React manages component rendering by creating a virtual representation of the DOM (Virtual DOM), updating it when component state or props change, comparing it with the previous Virtual DOM, and efficiently applying the necessary changes to the actual DOM through a process called reconciliation. This minimizes direct DOM manipulation and optimizes performance. React also provides lifecycle methods for additional logic and updates components when data changes to keep the UI in sync.

13. **Explain the significance of keys in React lists.**

    - Keys are unique identifiers assigned to elements within a list in React. They help React identify which items have changed, been added, or been removed in a list. Keys are essential for optimizing list rendering and preventing unnecessary re-renders.

14. **What is Redux, and why is it used in React applications?**

- Redux is a state management library for JavaScript applications, commonly used with React. It helps manage and centralize application state, making it easier to maintain and share data between components. Redux provides a predictable and controlled way to handle state changes in complex applications.

15. **What are the core principles of Redux?**

- The core principles of Redux are:
  - Single Source of Truth: The entire application state is stored in a single JavaScript object, simplifying data access and management.
  - State is Read-Only: State cannot be directly modified. Instead, you dispatch actions to describe changes you want to make.
  - Changes are Made Through Pure Functions (Reducers): Reducers are pure functions that specify how the state should change in response to dispatched actions.

16. **What is the role of actions and reducers in Redux?**

- Actions are plain JavaScript objects that describe what happened in an application (e.g., user interactions). They include a `type` property and may also include data. Reducers specify how the state should change in response to actions. They are pure functions that take the current state and an action as arguments and return a new state.

17. **How do you connect a React component to the Redux store?**

- To connect a React component to the Redux store, you typically use the `connect` function from the `react-redux` library. You define a "container component" that wraps your "presentational component" and specifies which parts of the store's state and which actions should be available as props to the presentational component.

18. **What is the purpose of the Redux Thunk middleware?**

- Redux Thunk is a middleware that enables Redux to handle asynchronous actions. It allows you to dispatch functions (thunks) instead of plain objects as actions. Thunks can perform asynchronous operations, like API requests, before dispatching actual actions, making it essential for managing side effects in Redux.

19. **What are selectors in Redux, and why are they useful?**

- Selectors are functions that extract and compute data from the Redux store. They are useful for encapsulating the logic of accessing specific parts of the store and computing derived data. Selectors improve performance by memoizing the results and enhance maintainability by centralizing data access logic.

Some key- points to know before going to the interview:

- some common questions about react routing
- how the diffing algorithm work.
- some connon code examples ,like class component, functional component,
- different syntax used for exporting modules.
- what is the role and significance.
