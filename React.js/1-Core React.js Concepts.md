## 1. Difference between **Functional Components** and **Class Components**

**Functional Components**

* Simple JavaScript functions.
* Use **hooks** (`useState`, `useEffect`, etc.) for state and lifecycle.
* Easier to test and maintain.

**Class Components**

* ES6 classes that extend `React.Component`.
* Use **this.state** and lifecycle methods (`componentDidMount`, `componentDidUpdate`, etc.).
* More verbose, mostly replaced by functional components.

🔹 **Example:**

```jsx
// Functional Component
function Greeting({ name }) {
  return <h1>Hello, {name}</h1>;
}

// Class Component
class GreetingClass extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

---

## 2. **Props vs State**

* **Props (Properties):**

  * Passed **from parent to child**.
  * **Read-only** (immutable).

* **State:**

  * Managed **inside the component**.
  * Can be **updated with setState / useState**.

🔹 **Example:**

```jsx
function Counter({ initial }) { // props
  const [count, setCount] = React.useState(initial); // state

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

// Usage
<Counter initial={5} />
```

---

## 3. **How Virtual DOM Works**

DOM- Document Object Model is a tree Sructure representing your HTML element in the browser

* React maintains a **virtual representation of the DOM** in memory.
* On state/prop change, React:

  1. Creates a new virtual DOM.
  2. **Diffs** it with the old one.
  3. Updates only the changed parts in the **real DOM** (efficient).

🔹 Example:

If only a `<p>` text changes, React won’t re-render the whole `<div>`, only updates that text node.

---

## 4. **Controlled vs Uncontrolled Components**

* **Controlled Component:** React **controls** the form input via state.
* **Uncontrolled Component:** Value is handled by the **DOM itself** (using `ref`).

🔹 **Example:**

```jsx
// Controlled
function ControlledInput() {
  const [value, setValue] = React.useState("");
  return (
    <input value={value} onChange={e => setValue(e.target.value)} />
  );
}

// Uncontrolled
function UncontrolledInput() {
  const inputRef = React.useRef();
  const handleSubmit = () => alert(inputRef.current.value);

  return (
    <>
      <input ref={inputRef} />
      <button onClick={handleSubmit}>Submit</button>
    </>
  );
}
```

---

## 5. **Why is the Key Prop Important in Lists?**

* Helps React identify **which items changed, added, or removed**.
* Improves performance in **list rendering**.
* Keys should be **unique and stable** (avoid `index` if possible).

🔹 Example:

```jsx
{items.map(item => (
  <li key={item.id}>{item.name}</li>
))}
```

Without keys, React re-renders entire list unnecessarily.

---

## 6. **React Fragments**

* Allow grouping multiple children **without adding extra DOM nodes** (`<div>`).
* Improves performance and clean HTML.

🔹 Example:

```jsx
function User() {
  return (
    <>
      <h1>John</h1>
      <p>Developer</p>
    </>
  );
}
```

Instead of wrapping with `<div>`.

---

## 7. **Difference between JSX and JavaScript**

* **JavaScript (JS):** Standard language.
* **JSX:** A **syntax extension** that lets you write HTML inside JS.
* JSX gets **compiled to `React.createElement()`** calls.

🔹 Example:

```jsx
// JSX
const element = <h1>Hello World</h1>;

// Compiles to JS
const elementJS = React.createElement("h1", null, "Hello World");
```

---

## 8. **Conditional Rendering in React**

Use JavaScript operators (`if`, ternary, `&&`) inside JSX.

🔹 Example:

```jsx
function Greeting({ isLoggedIn }) {
  return (
    <div>
      {isLoggedIn ? <h1>Welcome back!</h1> : <h1>Please log in.</h1>}
    </div>
  );
}
```

---

## 9. **React Elements vs React Components**

* **Element:** Smallest building block (e.g., `<h1>Hello</h1>`).
* **Component:** A function/class that returns elements.

🔹 Example:

```jsx
// React Element
const element = <h1>Hello</h1>;

// React Component
function Hello() {
  return <h1>Hello</h1>;
}
```

---

## 10. **Lifecycle Methods vs Hooks**

**Class Components Lifecycle:**

* `componentDidMount` → After render.
* `componentDidUpdate` → After state/props change.
* `componentWillUnmount` → Before removal.

**Functional Components with Hooks:**

* `useEffect` replaces all lifecycle methods.

🔹 Example:

```jsx
// Class Component
class Timer extends React.Component {
  componentDidMount() {
    console.log("Mounted");
  }
  componentDidUpdate() {
    console.log("Updated");
  }
  componentWillUnmount() {
    console.log("Unmounted");
  }
  render() {
    return <h1>Timer</h1>;
  }
}

// Functional with Hooks
function Timer() {
  React.useEffect(() => {
    console.log("Mounted/Updated");
    return () => console.log("Unmounted"); // cleanup
  });
  return <h1>Timer</h1>;
}
