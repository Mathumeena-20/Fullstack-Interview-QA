## 1. **What is React Reconciliation?**

* **Reconciliation** is the process React uses to update the DOM **efficiently** when state/props change.
* React compares the **new Virtual DOM** with the previous one using the **diffing algorithm**.
* Only the changed nodes are updated in the **real DOM**.

🔹 Example:
If you update just one `<p>` in a large list, React will update **only that `<p>`**, not the entire list.

---

## 2. **What is React Fiber Architecture?**

* **Fiber** is the new reconciliation algorithm introduced in React 16.
* Enables React to **break rendering work into small units** and spread them over multiple frames.
* Improves **performance** and supports **features like Suspense, concurrent rendering, and error boundaries**.

Think of Fiber as React’s **new engine** for rendering and scheduling.

---

## 3. **Difference between `React.createElement` and JSX**

* **JSX** is a syntax sugar for `React.createElement`.
* JSX is easier to read/write, but at compile-time, it gets converted into `React.createElement`.

🔹 Example:

```jsx
// JSX
const element = <h1>Hello World</h1>;

// Compiled JS
const element2 = React.createElement("h1", null, "Hello World");
```

So JSX = developer-friendly, `React.createElement` = what React actually uses.

---

## 4. **How does React Diffing Algorithm work?**

* React assumes:

  1. **Different element types → replace whole node.**
  2. **Same type → compare props/children → update only changed parts.**
  3. Lists → use **keys** to track moved/updated items.

🔹 Example:

```jsx
<ul>
  <li key="1">Apple</li>
  <li key="2">Banana</li>
</ul>
```

If "Banana" changes to "Mango", React only updates that `<li>`, not the entire `<ul>`.

---

## 5. **What are Higher-Order Components (HOC)?**

* A **HOC** is a function that takes a component and returns a new component with additional props or logic.
* Used for **code reusability** (authentication, logging, permissions, etc.).

🔹 Example:

```jsx
function withLogger(WrappedComponent) {
  return function(props) {
    console.log("Props:", props);
    return <WrappedComponent {...props} />;
  };
}

function Hello({ name }) {
  return <h1>Hello {name}</h1>;
}

const HelloWithLogger = withLogger(Hello);

// Usage
<HelloWithLogger name="John" />;
```

---

## 6. **Difference between Context API and Redux**

| Feature        | Context API                | Redux                                 |
| -------------- | -------------------------- | ------------------------------------- |
| Purpose        | Avoids **prop drilling**   | Full **state management**             |
| Complexity     | Simple                     | More setup (store, actions, reducers) |
| Scalability    | Good for small/medium apps | Better for large apps                 |
| Async Handling | No built-in support        | Has middleware (Thunk, Saga)          |
| Boilerplate    | Minimal                    | More verbose                          |

🔹 Example: Use Context API for **theme toggling**, Redux for **large data-heavy apps**.

---

## 7. **What is Prop Drilling and How to Avoid it?**

* **Prop Drilling:** Passing props through multiple components just to reach a deeply nested child.

🔹 Example (prop drilling):

```jsx
function App() {
  return <Parent theme="dark" />;
}
function Parent(props) {
  return <Child theme={props.theme} />;
}
function Child(props) {
  return <button>{props.theme}</button>;
}
```

🔹 **Avoiding it:** Use **Context API** or **Redux**.

```jsx
const ThemeContext = React.createContext("light");

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Child />
    </ThemeContext.Provider>
  );
}

function Child() {
  const theme = React.useContext(ThemeContext);
  return <button>{theme}</button>;
}
```

---

## 8. **What is Lazy Loading in React? How do you implement it?**

* **Lazy Loading** = load components **only when needed**, reducing bundle size.
* Implemented using **`React.lazy` + `Suspense`**.

🔹 Example:

```jsx
const Profile = React.lazy(() => import("./Profile"));

function App() {
  return (
    <React.Suspense fallback={<h1>Loading...</h1>}>
      <Profile />
    </React.Suspense>
  );
}
```

---

## 9. **How does Error Boundary work in React?**

* **Error Boundaries** catch JavaScript errors in child components and display a fallback UI.
* Only available in **class components**.

🔹 Example:

```jsx
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }
  static getDerivedStateFromError() {
    return { hasError: true };
  }
  componentDidCatch(error, info) {
    console.error("Error caught:", error, info);
  }
  render() {
    if (this.state.hasError) {
      return <h1>Something went wrong!</h1>;
    }
    return this.props.children;
  }
}

// Usage
<ErrorBoundary>
  <BuggyComponent />
</ErrorBoundary>
```

---

## 10. **How does React handle Forms? (Controlled vs Uncontrolled)**

* **Controlled Form:** React state controls input value.
* **Uncontrolled Form:** DOM manages input via `ref`.

🔹 Example:

```jsx
// Controlled
function ControlledForm() {
  const [name, setName] = React.useState("");
  return (
    <form>
      <input value={name} onChange={e => setName(e.target.value)} />
      <p>{name}</p>
    </form>
  );
}

// Uncontrolled
function UncontrolledForm() {
  const inputRef = React.useRef();
  const handleSubmit = () => alert(inputRef.current.value);
  return (
    <form>
      <input ref={inputRef} />
      <button type="button" onClick={handleSubmit}>Submit</button>
    </form>
  );
}
```

---

✅ That’s all **10 Intermediate React concepts with explanations + examples**.

Would you like me to also make a **quick comparison table (Controlled vs Uncontrolled, Context API vs Redux, JSX vs createElement)** for **fast revision before interviews**?
