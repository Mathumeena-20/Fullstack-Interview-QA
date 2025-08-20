## 1. **What are React Hooks? Why were they introduced?**

* **Hooks** are special functions introduced in React 16.8 that let you use **state, lifecycle, and other React features in functional components**.
* Before hooks, **class components** were needed for state & lifecycle.
* Hooks made React **simpler, more reusable, and easier to test**.

🔹 **Example:**

```jsx
// Functional Component with Hook
function Counter() {
  const [count, setCount] = React.useState(0); // useState hook
  return <button onClick={() => setCount(count + 1)}>Count: {count}</button>;
}
```

---

## 2. **Difference between `useState` and `useReducer`**

* `useState` → Best for **simple state management**.
* `useReducer` → Best for **complex state logic** (multiple transitions).

🔹 **Example:**

```jsx
// useState
function Counter() {
  const [count, setCount] = React.useState(0);
  return <button onClick={() => setCount(count + 1)}>Count: {count}</button>;
}

// useReducer
function CounterReducer() {
  function reducer(state, action) {
    switch (action.type) {
      case "increment": return { count: state.count + 1 };
      case "decrement": return { count: state.count - 1 };
      default: return state;
    }
  }
  const [state, dispatch] = React.useReducer(reducer, { count: 0 });

  return (
    <>
      <p>{state.count}</p>
      <button onClick={() => dispatch({ type: "increment" })}>+</button>
      <button onClick={() => dispatch({ type: "decrement" })}>-</button>
    </>
  );
}
```

---

## 3. **Explain `useEffect` hook with examples**

* `useEffect` lets you perform **side effects** (API calls, subscriptions, DOM updates).
* Works like **componentDidMount, componentDidUpdate, and componentWillUnmount** combined.

🔹 **Example:**

```jsx
function Timer() {
  const [count, setCount] = React.useState(0);

  // Runs only once (on mount)
  React.useEffect(() => {
    console.log("Component Mounted");
  }, []);

  // Runs on count change
  React.useEffect(() => {
    console.log("Count updated:", count);
  }, [count]);

  // Cleanup (like componentWillUnmount)
  React.useEffect(() => {
    const interval = setInterval(() => setCount(c => c + 1), 1000);
    return () => clearInterval(interval); 
  }, []);

  return <h1>{count}</h1>;
}
```

---

## 4. **Difference between `useMemo` and `useCallback`**

* `useMemo(fn, deps)` → Memoizes **computed values**.
* `useCallback(fn, deps)` → Memoizes **functions**.

🔹 **Example:**

```jsx
function Example({ items }) {
  const [query, setQuery] = React.useState("");

  // useMemo - caching computed value
  const filteredItems = React.useMemo(() => {
    return items.filter(item => item.includes(query));
  }, [query, items]);

  // useCallback - caching function
  const handleChange = React.useCallback((e) => {
    setQuery(e.target.value);
  }, []);

  return (
    <>
      <input value={query} onChange={handleChange} />
      <ul>{filteredItems.map(i => <li key={i}>{i}</li>)}</ul>
    </>
  );
}
```

---

## 5. **When should you use `useRef`?**

* To **store mutable values** that don’t trigger re-renders.
* To directly **access/manipulate DOM elements**.

🔹 **Example:**

```jsx
function FocusInput() {
  const inputRef = React.useRef();

  const focusInput = () => {
    inputRef.current.focus(); // direct DOM access
  };

  return (
    <>
      <input ref={inputRef} />
      <button onClick={focusInput}>Focus Input</button>
    </>
  );
}
```

---

## 6. **Can we use hooks inside loops or conditions? Why not?**

* ❌ No. Hooks must always be called **at the top level** of a component.
* React uses **order of hook calls** to track state.
* If placed inside conditions/loops, order breaks → errors.

✅ Solution → Always call hooks at top, and handle conditions inside the hook logic.

---

## 7. **How do Custom Hooks work? Give an example**

* A **custom hook** is a function starting with `use` that reuses hook logic.

🔹 **Example:**

```jsx
// Custom Hook
function useFetch(url) {
  const [data, setData] = React.useState(null);

  React.useEffect(() => {
    fetch(url).then(res => res.json()).then(setData);
  }, [url]);

  return data;
}

// Usage
function UserList() {
  const users = useFetch("https://jsonplaceholder.typicode.com/users");
  return <ul>{users?.map(u => <li key={u.id}>{u.name}</li>)}</ul>;
}
```

---

## 8. **What problem does `useContext` solve?**

* Avoids **prop drilling** (passing props through multiple levels).
* Provides **global state access**.

🔹 **Example:**

```jsx
const ThemeContext = React.createContext("light");

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Toolbar />
    </ThemeContext.Provider>
  );
}

function Toolbar() {
  return <ThemedButton />;
}

function ThemedButton() {
  const theme = React.useContext(ThemeContext);
  return <button>{theme} mode</button>;
}
```

---

## 9. **Difference between `useLayoutEffect` and `useEffect`**

* `useEffect` → Runs **after painting** (async, non-blocking).
* `useLayoutEffect` → Runs **synchronously before paint** (blocking).

🔹 **Example:** (Fixing layout flicker)

```jsx
function Box() {
  const ref = React.useRef();

  React.useLayoutEffect(() => {
    ref.current.style.color = "red"; // runs before paint
  }, []);

  return <div ref={ref}>Hello</div>;
}
```

---

## 10. **What happens if you update state inside `useEffect` without dependencies?**

* If no dependencies `[]` → runs only once.
* If dependencies missing → runs **on every render** → state update triggers re-render → infinite loop ⚠️.

🔹 **Bad Example (Infinite loop):**

```jsx
useEffect(() => {
  setCount(count + 1); // keeps updating → infinite loop
});
```

✅ **Solution → Add dependencies:**

```jsx
useEffect(() => {
  setCount(c => c + 1); 
}, []); // runs only once
```

---

✅ That covers **all 10 React Hooks concepts with explanations + code examples**.

Would you like me to create a **comparison table (Hooks vs Class Lifecycle methods)** so you can quickly answer interviewers when they ask “How do hooks replace lifecycle methods?”?
