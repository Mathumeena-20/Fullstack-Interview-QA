# ✅ **React.js Interview Questions & Answers (50 Q&A)**

---

## **📌 1. What is React?**

React is a **JavaScript library** for building user interfaces using **components**, **virtual DOM**, and **unidirectional data flow**.

---

## **📌 2. What is JSX?**

JSX is a syntax extension that lets you write **HTML-like code inside JavaScript**.
It compiles to `React.createElement()`.

---

## **📌 3. Why does React use Virtual DOM?**

To improve performance by:

* Comparing previous & current virtual DOM (diffing)
* Updating **only the changed nodes** in the real DOM

---

## **📌 4. What are components in React?**

Reusable building blocks.
Two types:

* Functional Components (modern, use hooks)
* Class Components (legacy)

---

## **📌 5. What is the difference between props and state?**

| Props                   | State              |
| ----------------------- | ------------------ |
| Read-only               | Mutable            |
| Passed from parent      | Local to component |
| No re-render by default | Triggers re-render |

---

## **📌 6. What is prop drilling?**

When props are passed through multiple components unnecessarily.
Solution → Context API, Redux, Zustand.

---

## **📌 7. What is the Context API?**

A way to share global state without prop drilling.
Used via `createContext()` + `useContext()`.

---

## **📌 8. What is the useState hook?**

Manages local component state.

```js
const [count, setCount] = useState(0);
```

---

## **📌 9. What is useEffect?**

Handles **side effects** like API calls, event listeners, timers.

---

## **📌 10. How does useEffect dependency array work?**

* `[]` → run once
* `[dep]` → run when dep changes
* no array → runs after every render

---

## **📌 11. What is the cleanup function in useEffect?**

Used to remove listeners, cancel timers, etc.

```js
useEffect(() => {
  return () => console.log("cleanup");
}, []);
```

---

## **📌 12. What is useRef?**

Stores values across renders without causing re-render.
Also used for DOM access.

---

## **📌 13. Difference between useMemo and useCallback?**

| useMemo                      | useCallback                                   |
| ---------------------------- | --------------------------------------------- |
| Memoizes **values**          | Memoizes **functions**                        |
| Avoid expensive calculations | Avoid re-render due to new function reference |

---

## **📌 14. What is React.memo?**

Higher-order component to prevent unnecessary re-renders of child components.

---

## **📌 15. What is reconciliation?**

React’s process of diffing the virtual DOM & updating only changed nodes.

---

## **📌 16. Why are keys needed in lists?**

To identify items uniquely and improve reconciliation.

---

## **📌 17. Why should we avoid using array index as key?**

Because:

* Items may reorder
* Causes incorrect re-renders

Better: unique IDs.

---

## **📌 18. Explain controlled components.**

Form inputs whose value is controlled by React state.

---

## **📌 19. Explain uncontrolled components.**

Inputs managed by the DOM using `ref`.

---

## **📌 20. What is React Router?**

A routing library to handle:

* Navigation
* URL matching
* Dynamic routes

---

## **📌 21. Difference between BrowserRouter and HashRouter?**

* **BrowserRouter** → Uses real URLs
* **HashRouter** → Uses `#` (older browsers, GitHub pages)

---

## **📌 22. What is Redux?**

A predictable state container.
Principles:

* Single source of truth
* State is read-only
* Pure reducers

---

## **📌 23. What is Redux Thunk?**

Middleware to handle async actions in Redux.

---

## **📌 24. Difference between Redux and Context API?**

Context is simple and good for small state.
Redux is more structured for large apps.

---

## **📌 25. What is useReducer?**

An alternative to useState for complex logic.

---

## **📌 26. What is lifting state up?**

Moving state to a common ancestor to share across children.

---

## **📌 27. What is React Fiber?**

React’s rendering engine optimized for:

* Scheduling
* Interruptible rendering
* Concurrent mode

---

## **📌 28. What is Concurrent Rendering?**

Allows React to pause, resume, or cancel renders → improves UI responsiveness.

---

## **📌 29. What is Suspense?**

A component for handling lazy loading or waiting states.

---

## **📌 30. What is lazy loading in React?**

Dynamic importing components.

```js
const About = React.lazy(() => import('./About'));
```

---

## **📌 31. What is Error Boundary?**

Catches runtime errors in child components (class-based).

---

## **📌 32. Why doesn’t useEffect run synchronously?**

Because React updates DOM first and then runs side effects.

---

## **📌 33. How to optimize React performance?**

* React.memo
* useCallback & useMemo
* Code splitting
* Windowing (React Window)
* Avoid inline functions
* Keys in lists

---

## **📌 34. What is SSR (Server-Side Rendering)?**

Rendering React components on server → sends HTML to client.
Used in Next.js.

---

## **📌 35. What is Hydration?**

Client-side React taking over server-rendered HTML.

---

## **📌 36. What is CSR vs SSR vs SSG?**

* CSR → Client renders (React default)
* SSR → Server renders on request (Next.js)
* SSG → Static site generation at build time

---

## **📌 37. What is a Pure Component?**

A component that only re-renders when props change (shallow comparison).

---

## **📌 38. What is the useImperativeHandle hook?**

Customizes the ref exposed to parents.

---

## **📌 39. What is portal in React?**

Render elements outside the parent DOM hierarchy.

---

## **📌 40. What is fragment `<></>`?**

Wraps elements without creating extra DOM nodes.

---

## **📌 41. Explain batching in React.**

React groups multiple state updates into one re-render.

---

## **📌 42. What is strict mode?**

Tool for:

* Detecting unsafe lifecycle methods
* Highlighting side-effects
* Double-rendering components in dev mode only

---

## **📌 43. Why shouldn’t we mutate state directly?**

Because React may not re-render.
Always use setter functions.

---

## **📌 44. What is hydration mismatch in Next.js?**

Mismatch between server-rendered HTML and client-side render.

---

## **📌 45. What is a Higher-Order Component (HOC)?**

A function that takes a component & returns a new enhanced component.

---

## **📌 46. What are render props?**

A function passed as a prop to decide what to render.

---

## **📌 47. Explain Tree Shaking.**

Removing unused code during bundling.

---

## **📌 48. What is code splitting?**

Splitting code into smaller bundles loaded on demand.

---

## **📌 49. How does React handle events?**

Uses synthetic events — a wrapper around browser events for cross-browser consistency.

---

## **📌 50. React interview scenario question:**

**You notice your entire component tree re-renders after clicking a button. Why?**
Possible reasons:

* Parent state changes → children re-render
* Functions re-created on every render → useCallback missing
* Props are non-primitive
* No memoization

---

Sure! Here are **top React coding interview questions with solutions**, covering **beginner → advanced**, including **hooks, state, performance optimization, API integration, context, custom hooks, and React patterns**.

---

# ✅ **React Coding Interview Questions (With Answers)**

Each question includes **problem → expected output → solution code → explanation**.

---

# **📌 1. Create a Counter Component (useState)**

### **❓ Question**

Build a counter with **increment, decrement, reset** buttons.

### ✅ **Answer**

```jsx
import { useState } from "react";

export default function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h2>{count}</h2>

      <button onClick={() => setCount(count + 1)}>+</button>
      <button onClick={() => setCount(count - 1)}>-</button>
      <button onClick={() => setCount(0)}>Reset</button>
    </div>
  );
}
```

### ✔ Explanation

* Simple usage of `useState`
* Re-renders on state change

---

# **📌 2. Build a Todo App (Add + Delete items)**

### **❓ Question**

Create a Todo list with **input + add button + delete button**.

### ✅ **Answer**

```jsx
import { useState } from "react";

export default function TodoApp() {
  const [text, setText] = useState("");
  const [todos, setTodos] = useState([]);

  const addTodo = () => {
    if (text.trim() === "") return;
    setTodos([...todos, text]);
    setText("");
  };

  const deleteTodo = (index) => {
    setTodos(todos.filter((_, i) => i !== index));
  };

  return (
    <div>
      <input value={text} onChange={(e) => setText(e.target.value)} />
      <button onClick={addTodo}>Add</button>

      {todos.map((t, i) => (
        <div key={i}>
          {t} <button onClick={() => deleteTodo(i)}>X</button>
        </div>
      ))}
    </div>
  );
}
```

---

# **📌 3. Fetch API Data (useEffect + Loading + Error)**

### **❓ Question**

Fetch data from:
`https://jsonplaceholder.typicode.com/posts`

### ✅ **Answer**

```jsx
import { useEffect, useState } from "react";

export default function Posts() {
  const [data, setData] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/posts")
      .then((res) => res.json())
      .then((res) => {
        setData(res);
        setLoading(false);
      })
      .catch(() => {
        setError("Failed to fetch");
        setLoading(false);
      });
  }, []);

  if (loading) return <h3>Loading...</h3>;
  if (error) return <h3>{error}</h3>;

  return (
    <ul>
      {data.map((p) => (
        <li key={p.id}>{p.title}</li>
      ))}
    </ul>
  );
}
```

---

# **📌 4. Debounce Search Input (Google Search Style)**

### ❓ **Question**

Trigger API only after user stops typing for **500ms**.

### ✅ **Answer**

```jsx
import { useEffect, useState } from "react";

export default function Search() {
  const [text, setText] = useState("");
  const [debounced, setDebounced] = useState("");

  useEffect(() => {
    const timer = setTimeout(() => setDebounced(text), 500);
    return () => clearTimeout(timer);
  }, [text]);

  useEffect(() => {
    if (debounced) {
      console.log("Calling API for:", debounced);
    }
  }, [debounced]);

  return <input value={text} onChange={(e) => setText(e.target.value)} />;
}
```

---

# **📌 5. Create Custom Hook: useFetch()**

### ❓ **Question**

Build a reusable hook for fetching APIs.

### ✅ **Answer**

```jsx
import { useEffect, useState } from "react";

export function useFetch(url) {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch(url)
      .then((res) => res.json())
      .then(setData);
  }, [url]);

  return data;
}
```

### Usage:

```jsx
export default function Users() {
  const users = useFetch("https://jsonplaceholder.typicode.com/users");
  return <pre>{JSON.stringify(users, null, 2)}</pre>;
}
```

---

# **📌 6. Stop Unnecessary Re-Renders (useMemo + useCallback)**

### ❓ Question

Optimize heavy calculation + child component re-renders.

### ✅ **Answer**

```jsx
import { useMemo, useCallback, useState } from "react";

function Child({ onClick }) {
  console.log("Child rendered");
  return <button onClick={onClick}>Click</button>;
}

const MemoChild = React.memo(Child);

export default function App() {
  const [count, setCount] = useState(0);

  const heavy = useMemo(() => {
    console.log("Heavy calc...");
    return count * 1000;
  }, [count]);

  const handleClick = useCallback(() => {
    console.log("Clicked");
  }, []);

  return (
    <>
      <h2>{heavy}</h2>
      <MemoChild onClick={handleClick} />
      <button onClick={() => setCount(count + 1)}>+</button>
    </>
  );
}
```

---

# **📌 7. Build Theme Toggler Using Context API**

### ❓ **Question**

Toggle dark/light mode using React Context.

### ✅ **Answer**

### `ThemeContext.js`

```jsx
import { createContext } from "react";
export const ThemeContext = createContext();
```

### `App.js`

```jsx
import { useState } from "react";
import { ThemeContext } from "./ThemeContext";
import Home from "./Home";

export default function App() {
  const [theme, setTheme] = useState("light");

  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      <Home />
    </ThemeContext.Provider>
  );
}
```

### `Home.js`

```jsx
import { useContext } from "react";
import { ThemeContext } from "./ThemeContext";

export default function Home() {
  const { theme, setTheme } = useContext(ThemeContext);

  return (
    <div className={theme}>
      <h1>{theme} mode</h1>
      <button onClick={() => setTheme(theme === "light" ? "dark" : "light")}>
        Toggle
      </button>
    </div>
  );
}
```

---

# **📌 8. Accordion Component (Open/Close toggle)**

### ❓ Question

Only one item should open at a time.

### ✅ **Answer**

```jsx
import { useState } from "react";

const data = [
  { title: "Section 1", content: "Content 1" },
  { title: "Section 2", content: "Content 2" },
];

export default function Accordion() {
  const [open, setOpen] = useState(null);

  return (
    <div>
      {data.map((item, index) => (
        <div key={index}>
          <h3 onClick={() => setOpen(open === index ? null : index)}>
            {item.title}
          </h3>
          {open === index && <p>{item.content}</p>}
        </div>
      ))}
    </div>
  );
}
```

---

# **📌 9. Stopwatch Component**

### ❓ Question

Create a timer with **start + stop + reset**.

### ✅ **Answer**

```jsx
import { useState, useEffect, useRef } from "react";

export default function Stopwatch() {
  const [time, setTime] = useState(0);
  const ref = useRef(null);

  const start = () => {
    if (!ref.current) {
      ref.current = setInterval(() => setTime(t => t + 1), 1000);
    }
  };

  const stop = () => {
    clearInterval(ref.current);
    ref.current = null;
  };

  const reset = () => {
    stop();
    setTime(0);
  };

  useEffect(() => stop, []);

  return (
    <>
      <h1>{time}</h1>
      <button onClick={start}>Start</button>
      <button onClick={stop}>Stop</button>
      <button onClick={reset}>Reset</button>
    </>
  );
}
```

---

# **📌 10. Pagination Component**

### ❓ Question

Show 10 items per page.

### ✅ **Answer**

```jsx
import { useState } from "react";

export default function Pagination({ items }) {
  const [page, setPage] = useState(1);
  const perPage = 10;
  const start = (page - 1) * perPage;
  const final = start + perPage;

  const paginated = items.slice(start, final);

  return (
    <div>
      {paginated.map((item) => (
        <p key={item}>{item}</p>
      ))}

      <button disabled={page === 1} onClick={() => setPage(page - 1)}>
        Prev
      </button>

      <button
        disabled={final >= items.length}
        onClick={() => setPage(page + 1)}
      >
        Next
      </button>
    </div>
  );
}
```



