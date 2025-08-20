Awesome 🚀 These **React + JavaScript coding questions** are exactly what interviewers love asking for **2+ years experience** because they test both **React concepts** and **coding ability**. I’ll go through each problem step by step with **solution + explanation + code example**.

---

# ✅ React + JavaScript Coding Questions

---

## 1. **Build a To-Do List App with Add/Delete Functionality**

🔹 **Explanation**

* Use `useState` to store tasks.
* Add new tasks via input.
* Delete tasks using filter.

```jsx
function TodoApp() {
  const [tasks, setTasks] = React.useState([]);
  const [text, setText] = React.useState("");

  const addTask = () => {
    if (text.trim()) {
      setTasks([...tasks, { id: Date.now(), text }]);
      setText("");
    }
  };

  const deleteTask = (id) => {
    setTasks(tasks.filter(task => task.id !== id));
  };

  return (
    <div>
      <input value={text} onChange={e => setText(e.target.value)} />
      <button onClick={addTask}>Add</button>
      <ul>
        {tasks.map(task => (
          <li key={task.id}>
            {task.text} <button onClick={() => deleteTask(task.id)}>❌</button>
          </li>
        ))}
      </ul>
    </div>
  );
}
```

---

## 2. **Implement a Search Filter in React using Hooks**

🔹 **Explanation**

* Store items in state.
* Use `filter()` on input change.

```jsx
function SearchFilter() {
  const [query, setQuery] = React.useState("");
  const items = ["Apple", "Banana", "Mango", "Orange"];

  const filtered = items.filter(item =>
    item.toLowerCase().includes(query.toLowerCase())
  );

  return (
    <>
      <input value={query} onChange={e => setQuery(e.target.value)} />
      <ul>{filtered.map((item, i) => <li key={i}>{item}</li>)}</ul>
    </>
  );
}
```

---

## 3. **Create a Counter App with useReducer**

```jsx
function CounterReducer() {
  function reducer(state, action) {
    switch (action.type) {
      case "increment": return { count: state.count + 1 };
      case "decrement": return { count: state.count - 1 };
      case "reset": return { count: 0 };
      default: return state;
    }
  }

  const [state, dispatch] = React.useReducer(reducer, { count: 0 });

  return (
    <div>
      <h1>{state.count}</h1>
      <button onClick={() => dispatch({ type: "increment" })}>+</button>
      <button onClick={() => dispatch({ type: "decrement" })}>-</button>
      <button onClick={() => dispatch({ type: "reset" })}>Reset</button>
    </div>
  );
}
```

---

## 4. **Implement a Custom Hook for Fetching Data**

```jsx
function useFetch(url) {
  const [data, setData] = React.useState(null);

  React.useEffect(() => {
    fetch(url).then(res => res.json()).then(setData);
  }, [url]);

  return data;
}

function Users() {
  const users = useFetch("https://jsonplaceholder.typicode.com/users");
  return <ul>{users?.map(u => <li key={u.id}>{u.name}</li>)}</ul>;
}
```

---

## 5. **Write a Debounce Hook in React**

🔹 **Explanation**
Debouncing avoids calling a function too often (e.g., API calls).

```jsx
function useDebounce(value, delay) {
  const [debounced, setDebounced] = React.useState(value);

  React.useEffect(() => {
    const handler = setTimeout(() => setDebounced(value), delay);
    return () => clearTimeout(handler);
  }, [value, delay]);

  return debounced;
}

function Search() {
  const [query, setQuery] = React.useState("");
  const debouncedQuery = useDebounce(query, 500);

  React.useEffect(() => {
    if (debouncedQuery) console.log("Search API call:", debouncedQuery);
  }, [debouncedQuery]);

  return <input value={query} onChange={e => setQuery(e.target.value)} />;
}
```

---

## 6. **Implement Infinite Scroll in React**

🔹 **Explanation**

* Detect scroll to bottom.
* Load more items dynamically.

```jsx
function InfiniteScroll() {
  const [items, setItems] = React.useState(Array.from({ length: 20 }, (_, i) => i + 1));

  const loadMore = () => {
    setItems(prev => [...prev, ...Array.from({ length: 20 }, (_, i) => prev.length + i + 1)]);
  };

  React.useEffect(() => {
    const handleScroll = () => {
      if (window.innerHeight + window.scrollY >= document.body.offsetHeight - 10) {
        loadMore();
      }
    };
    window.addEventListener("scroll", handleScroll);
    return () => window.removeEventListener("scroll", handleScroll);
  }, []);

  return <ul>{items.map(i => <li key={i}>{i}</li>)}</ul>;
}
```

---

## 7. **Create a Form Validation with Controlled Components**

```jsx
function FormValidation() {
  const [email, setEmail] = React.useState("");
  const [error, setError] = React.useState("");

  const validate = () => {
    if (!/\S+@\S+\.\S+/.test(email)) {
      setError("Invalid Email");
    } else {
      setError("");
      alert("Form submitted");
    }
  };

  return (
    <div>
      <input value={email} onChange={e => setEmail(e.target.value)} />
      <button onClick={validate}>Submit</button>
      {error && <p style={{ color: "red" }}>{error}</p>}
    </div>
  );
}
```

---

## 8. **Implement Dark Mode Toggle using Context API**

```jsx
const ThemeContext = React.createContext();

function App() {
  const [theme, setTheme] = React.useState("light");

  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      <Toolbar />
    </ThemeContext.Provider>
  );
}

function Toolbar() {
  const { theme, setTheme } = React.useContext(ThemeContext);
  return (
    <div style={{ background: theme === "light" ? "#fff" : "#333", color: theme === "light" ? "#000" : "#fff" }}>
      <p>Current theme: {theme}</p>
      <button onClick={() => setTheme(theme === "light" ? "dark" : "light")}>Toggle</button>
    </div>
  );
}
```

---

## 9. **Build a Modal Popup using Portals**

```jsx
import ReactDOM from "react-dom";

function Modal({ children, onClose }) {
  return ReactDOM.createPortal(
    <div style={{ position: "fixed", top: 0, left: 0, right: 0, bottom: 0, background: "rgba(0,0,0,0.5)" }}>
      <div style={{ background: "white", padding: 20, margin: "100px auto", width: 300 }}>
        {children}
        <button onClick={onClose}>Close</button>
      </div>
    </div>,
    document.body
  );
}

function App() {
  const [show, setShow] = React.useState(false);
  return (
    <>
      <button onClick={() => setShow(true)}>Open Modal</button>
      {show && <Modal onClose={() => setShow(false)}>Hello Modal!</Modal>}
    </>
  );
}
```

---

## 10. **Optimize a List of 10,000 Items (Virtualization)**

🔹 **Explanation**
Rendering 10,000 items kills performance → use virtualization (`react-window` or memoization).

```jsx
import { FixedSizeList as List } from "react-window";

function BigList() {
  const items = Array.from({ length: 10000 }, (_, i) => `Item ${i}`);
  return (
    <List height={400} itemCount={items.length} itemSize={35} width={300}>
      {({ index, style }) => <div style={style}>{items[index]}</div>}
    </List>
  );
}
```

---

✅ That covers **10 practical coding questions** with **solutions + explanations + code examples**.

👉 Do you want me to also prepare a **GitHub-ready React mini project** (combining to-do, search, modal, dark mode, etc.) so you can showcase it in interviews?
