# React Crash Course and Interview Questions

## React

This cheat sheet is a crash course for React beginners and helps review the basic syntax and concepts of React.

### Getting Started

1.  **Setting Up a React Project:**

    ```bash
    npx create-react-app my-app
    cd my-app
    npm start
    ```

        create-react-app sets up a new React project with a lot of the initial configuration done for you, so you can start coding right away without worrying about build tools and other setup details.

2.  **Basic Component:**

    ```javascript
    import React from "react";

    function Welcome(props) {
      return <h1>Hello, {props.name}</h1>;
    }

    export default Welcome;
    ```

        Components are the building blocks of a React application. This shows how to create a simple functional component that receives props (data passed to the component).

3.  **Rendering a Component:**

    ```javascript
    import React from "react";
    import ReactDOM from "react-dom";
    import Welcome from "./Welcome";

    ReactDOM.render(<Welcome name="Sara" />, document.getElementById("root"));
    ```

        Rendering a component involves placing it into the DOM. This example shows how to use ReactDOM.render to display the Welcome component on the page.

## JSX

1.  **Embedding Expressions in JSX:**

    ```javascript
    const name = "Josh Perez";
    const element = <h1>Hello, {name}</h1>;
    ```

        JSX allows you to write HTML elements directly in JavaScript. Embedding expressions helps make your components dynamic and interactive.

2.  **JSX Attributes:**

    ```javascript
    const element = <a href="https://www.reactjs.org">link</a>;
    ```

        Just like HTML, JSX allows you to set attributes on elements. This is essential for making elements functional, like setting href for links.

3.  **JSX Child Elements:**

    ```javascript
    const element = (
      <div>
        <h1>Hello!</h1>
        <h2>Good to see you here.</h2>
      </div>
    );
    ```

        JSX can contain multiple child elements, which helps in creating complex UI structures.

## Components

1.  **Function Components:**

    ```javascript
    function Welcome(props) {
      return <h1>Hello, {props.name}</h1>;
    }
    ```

        Function components are simple and useful for presenting data passed via props.

2.  **Class Components:**

    ```jsx
    class Welcome extends React.Component {
      render() {
        return <h1>Hello, {this.props.name}</h1>;
      }
    }
    ```

        Class components provide more features, such as local state and lifecycle methods, which can be necessary for more complex components.

3.  **Rendering Components:**

    ```jsx
    const element = <Welcome name="Sara" />;
    ReactDOM.render(element, document.getElementById("root"));
    ```

        To actually see your component in the browser, you need to render it into the DOM.

## Props

1.  **Passing Props:**

    ```jsx
    function Welcome(props) {
      return <h1>Hello, {props.name}</h1>;
    }

    const element = <Welcome name="Sara" />;
    ```

        Props are a way to pass data from parent components to child components, making components reusable and dynamic.

2.  **Props in Class Components:**

    ```jsx
    class Welcome extends React.Component {
      render() {
        return <h1>Hello, {this.props.name}</h1>;
      }
    }
    ```

        Class components also use props to receive data, similar to function components, maintaining consistency across different types of components.

## State and Hooks

1.  **Using useState Hook:**

    ```jsx
    import React, { useState } from "react";

    function Counter() {
      const [count, setCount] = useState(0);

      return (
        <div>
          <p>You clicked {count} times</p>
          <button onClick={() => setCount(count + 1)}>Click me</button>
        </div>
      );
    }
    ```

        The useState hook allows functional components to have their own state. This example shows a simple counter that updates its state when the button is clicked.

2.  **Using useEffect Hook:**

    ```jsx
    import React, { useState, useEffect } from "react";

    function Clock() {
      const [date, setDate] = useState(new Date());

      useEffect(() => {
        const timerID = setInterval(() => setDate(new Date()), 1000);

        return () => clearInterval(timerID);
      }, []);

      return (
        <div>
          <h1>Current Time:</h1>
          <h2>{date.toLocaleTimeString()}</h2>
        </div>
      );
    }
    ```

        The useEffect hook allows you to perform side effects in function components, such as setting up a timer. This hook is a replacement for lifecycle methods in class components.

## Lifecycle Methods (Class Components)

1.  **componentDidMount:**

    ```jsx
    componentDidMount() {
    // Runs after the component output has been rendered to the DOM
    }
    ```

        This lifecycle method is used to perform side effects like data fetching, subscriptions, or setting up timers after the component has been added to the DOM.

2.  **componentWillUnmount:**

    ```jsx
    componentWillUnmount() {
    // Runs before the component is removed from the DOM
    }
    ```

        This method is used to clean up subscriptions, timers, or other side effects to prevent memory leaks.

## Event Handling

1.  **Handling Events:**

    ```jsx
    function Toggle() {
      const [isOn, setIsOn] = useState(true);

      function handleClick() {
        setIsOn(!isOn);
      }

      return <button onClick={handleClick}>{isOn ? "ON" : "OFF"}</button>;
    }
    ```

        Handling events in React is similar to handling events on DOM elements. This example shows how to handle a button click event to toggle its state.

## Conditional Rendering

1.  **Conditional Rendering with If:**

    ```jsx
    function Greeting(props) {
      const isLoggedIn = props.isLoggedIn;
      if (isLoggedIn) {
        return <h1>Welcome back!</h1>;
      }
      return <h1>Please sign up.</h1>;
    }
    ```

        Conditional rendering allows you to render different UI elements based on the component's state or props, making the UI dynamic and responsive to user actions.

2.  **Conditional Rendering with Ternary Operator:**

    ```jsx
    function Greeting(props) {
      return props.isLoggedIn ? (
        <h1>Welcome back!</h1>
      ) : (
        <h1>Please sign up.</h1>
      );
    }
    ```

        The ternary operator provides a concise way to implement conditional rendering.

## Lists and Keys

1.  **Rendering Lists:**

    ```jsx
    function NumberList(props) {
      const numbers = props.numbers;
      const listItems = numbers.map((number) => (
        <li key={number.toString()}>{number}</li>
      ));
      return <ul>{listItems}</ul>;
    }
    ```

        Rendering lists dynamically based on an array of data allows you to create flexible and reusable components.

2.  **Keys:**

    ```jsx
    const listItems = numbers.map((number) => (
      <li key={number.toString()}>{number}</li>
    ));
    ```

        Keys help React identify which items have changed, are added, or are removed. They are essential for ensuring efficient updates and re-renders.

## Forms

1.  **Controlled Components:**

    ```jsx
    import React, { useState } from "react";

    function NameForm() {
      const [value, setValue] = useState("");

      function handleChange(event) {
        setValue(event.target.value);
      }

      function handleSubmit(event) {
        alert("A name was submitted: " + value);
        event.preventDefault();
      }

      return (
        <form onSubmit={handleSubmit}>
          <label>
            Name:
            <input type="text" value={value} onChange={handleChange} />
          </label>
          <button type="submit">Submit</button>
        </form>
      );
    }
    ```

        Controlled components keep the form data in the React state, making it easier to handle user input and validate data before submission.

## Context

1.  **Using Context:**

    ```jsx
    const MyContext = React.createContext();

    function MyProvider(props) {
      const [value, setValue] = useState("Hello, World!");
      return (
        <MyContext.Provider value={value}>{props.children}</MyContext.Provider>
      );
    }

    function MyComponent() {
      const value = React.useContext(MyContext);
      return <div>{value}</div>;
    }
    ```

        Context provides a way to pass data through the component tree without having to pass props down manually at every level. This is useful for global data like user authentication, themes, or language settings.

# Advance Section:

## Advance Hooks

1.  **useReducer Hook:**

    ```jsx
    import React, { useReducer } from "react";

    const initialState = { count: 0 };

    function reducer(state, action) {
      switch (action.type) {
        case "increment":
          return { count: state.count + 1 };
        case "decrement":
          return { count: state.count - 1 };
        default:
          throw new Error();
      }
    }

    function Counter() {
      const [state, dispatch] = useReducer(reducer, initialState);

      return (
        <div>
          <p>Count: {state.count}</p>
          <button onClick={() => dispatch({ type: "increment" })}>+</button>
          <button onClick={() => dispatch({ type: "decrement" })}>-</button>
        </div>
      );
    }
    ```

         The useReducer hook is an alternative to useState for managing more complex state logic. It is particularly useful when the next state depends on the previous one.

2.  **useContext Hook:**

```jsx
import React, { useContext } from "react";

const MyContext = React.createContext();

function MyComponent() {
  const value = useContext(MyContext);
  return <div>{value}</div>;
}

function App() {
  return (
    <MyContext.Provider value="Hello, World!">
      <MyComponent />
    </MyContext.Provider>
  );
}
```

    The useContext hook allows you to access the context value directly in a functional component. It avoids the need to use a context consumer component.

## Higher-Order Components (HOC)

1. **Creating a Higher-Order Component:**

```jsx
import React from "react";

function withLoading(Component) {
  return function WithLoadingComponent({ isLoading, ...props }) {
    if (!isLoading) return <Component {...props} />;
    return <p>Loading...</p>;
  };
}

function MyComponent(props) {
  return <div>{props.data}</div>;
}

const MyComponentWithLoading = withLoading(MyComponent);

function App() {
  return <MyComponentWithLoading isLoading={true} data="Hello, World!" />;
}
```

    Higher-order components are a pattern in React for reusing component logic. They allow you to add additional behavior to existing components in a composable way.

## Context API

1. **Using Context for State Management:**

```jsx
import React, { createContext, useState } from "react";

const ThemeContext = createContext();

function ThemeProvider({ children }) {
  const [theme, setTheme] = useState("light");

  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      {children}
    </ThemeContext.Provider>
  );
}

function ThemedComponent() {
  const { theme, setTheme } = React.useContext(ThemeContext);

  return (
    <div>
      <p>The current theme is {theme}</p>
      <button onClick={() => setTheme(theme === "light" ? "dark" : "light")}>
        Toggle Theme
      </button>
    </div>
  );
}

function App() {
  return (
    <ThemeProvider>
      <ThemedComponent />
    </ThemeProvider>
  );
}
```

    The Context API is useful for sharing state across many components without passing props down manually at every level.

## React Router

1. **Basic Coding:**

```jsx
import React from "react";
import { BrowserRouter as Router, Route, Switch, Link } from "react-router-dom";

function Home() {
  return <h2>Home</h2>;
}

function About() {
  return <h2>About</h2>;
}

function App() {
  return (
    <Router>
      <div>
        <nav>
          <ul>
            <li>
              <Link to="/">Home</Link>
            </li>
            <li>
              <Link to="/about">About</Link>
            </li>
          </ul>
        </nav>

        <Switch>
          <Route path="/about">
            <About />
          </Route>
          <Route path="/">
            <Home />
          </Route>
        </Switch>
      </div>
    </Router>
  );
}
```

    React Router allows you to handle routing in a single-page application, enabling navigation between different components without a page refresh.

## Performance Optimization

1. **React.memo**

```jsx
import React from "react";

const MyComponent = React.memo(function MyComponent(props) {
  return <div>{props.data}</div>;
});
```

    React.memo is a higher-order component that prevents a component from re-rendering if its props haven't changed. This can improve performance for functional components.

2. **useCallback Hook:**

```jsx
import React, { useState, useCallback } from "react";

function Parent() {
  const [count, setCount] = useState(0);
  const handleClick = useCallback(() => {
    setCount(count + 1);
  }, [count]);

  return <Child onClick={handleClick} />;
}

function Child({ onClick }) {
  return <button onClick={onClick}>Click me</button>;
}
```

    The useCallback hook returns a memoized version of the callback function that only changes if one of the dependencies has changed. This can help prevent unnecessary re-renders of child components.

3. **useMemo Hook:**

```jsx
import React, { useState, useMemo } from "react";

function ExpensiveComponent({ data }) {
  const processedData = useMemo(() => {
    // Expensive processing
    return data.map((item) => item * 2);
  }, [data]);

  return <div>{processedData.join(", ")}</div>;
}
```

    The useMemo hook is used to memoize expensive calculations, improving performance by recalculating only when the dependencies change.

## Custom Hooks

1. **Creating a Custom Hook:**

```jsx
import { useState, useEffect } from "react";

function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetch(url)
      .then((response) => response.json())
      .then((data) => {
        setData(data);
        setLoading(false);
      });
  }, [url]);

  return { data, loading };
}

function App() {
  const { data, loading } = useFetch("https://api.example.com/data");

  if (loading) return <p>Loading...</p>;
  return <div>{JSON.stringify(data)}</div>;
}
```

Custom hooks allow you to encapsulate reusable logic in a function, making your components cleaner and more modular.

## Fragments

1. **Using Fragments:**

```jsx
import React from "react";

function App() {
  return (
    <>
      <h1>First element</h1>
      <h2>Second element</h2>
    </>
  );
}
```

    Fragments let you group a list of children without adding extra nodes to the DOM. This is useful for returning multiple elements from a component's render method without wrapping them in an additional HTML element like a div.
