## 🔹 1. Difference between React Router v5 and v6

**Explanation:**

* React Router v6 introduced major changes for simplicity and better performance.

| Feature          | v5                                | v6                             |
| ---------------- | --------------------------------- | ------------------------------ |
| Route matching   | Uses `Switch`                     | Uses `Routes` (more efficient) |
| Route props      | `component`, `render`, `children` | `element={<Component />}`      |
| Nested routes    | More boilerplate                  | Easier with `<Routes>` nesting |
| Redirect         | `<Redirect />`                    | `<Navigate to="/path" />`      |
| Default route    | `path="/" exact`                  | Exact matching by default      |
| Protected routes | Implemented manually              | Easier with nested routes      |

**Example (v5):**

```jsx
<Switch>
  <Route path="/home" component={Home} />
  <Redirect to="/home" />
</Switch>
```

**Example (v6):**

```jsx
<Routes>
  <Route path="/home" element={<Home />} />
  <Route path="*" element={<Navigate to="/home" />} />
</Routes>
```

---

## 🔹 2. How do you handle protected routes in React Router?

**Explanation:** Protected routes ensure only authenticated users can access certain pages.

**Example:**

```jsx
const ProtectedRoute = ({ children }) => {
  const isAuth = localStorage.getItem("token");
  return isAuth ? children : <Navigate to="/login" />;
};

// Usage
<Routes>
  <Route path="/dashboard" element={<ProtectedRoute><Dashboard /></ProtectedRoute>} />
</Routes>
```

---

## 🔹 3. How does Redux flow work?

**Explanation:** Redux follows a **unidirectional data flow**:

1. **Action** → describes what happened
2. **Reducer** → receives action & updates state
3. **Store** → holds global state
4. **Component** → subscribes to store updates

**Example:**

```js
// action
const increment = () => ({ type: "INCREMENT" });

// reducer
const counterReducer = (state = 0, action) => {
  switch (action.type) {
    case "INCREMENT": return state + 1;
    default: return state;
  }
};

// store
const store = createStore(counterReducer);
store.dispatch(increment());
```

---

## 🔹 4. What are middlewares in Redux (like thunk, saga)?

**Explanation:** Middleware allows side effects (async logic, logging, etc.) in Redux.

* **Redux Thunk** → async functions in actions.
* **Redux Saga** → generator functions for async flows.

**Thunk Example:**

```js
const fetchUsers = () => async (dispatch) => {
  const res = await fetch("/api/users");
  const data = await res.json();
  dispatch({ type: "SET_USERS", payload: data });
};
```

---

## 🔹 5. Role of Immer.js in Redux Toolkit

**Explanation:** Immer lets you write **mutable code** that produces **immutable updates**.

**Example:**

```js
import { createSlice } from "@reduxjs/toolkit";

const counterSlice = createSlice({
  name: "counter",
  initialState: { value: 0 },
  reducers: {
    increment: (state) => { state.value += 1 }, // looks mutable but is safe
  }
});
```

---

## 🔹 6. How do you debug React apps?

**Methods:**

* **React DevTools** → inspect components, props, state.
* **Console logs** → for tracing values.
* **Profiler** → find performance bottlenecks.
* **Redux DevTools** → debug Redux actions/state.

**Example (Profiler):**

```jsx
import { Profiler } from "react";

<Profiler id="App" onRender={(id, phase, actualDuration) => {
  console.log(id, phase, actualDuration);
}}>
  <App />
</Profiler>
```

---

## 🔹 7. Context API vs Redux

| Feature        | Context API          | Redux                             |
| -------------- | -------------------- | --------------------------------- |
| Usage          | Simple state sharing | Complex state management          |
| Async handling | Not built-in         | Supports middlewares (thunk/saga) |
| DevTools       | No                   | Yes                               |
| Boilerplate    | Less                 | More                              |
| Best for       | Small-medium apps    | Large apps with complex logic     |

**Example (Context API):**

```jsx
const ThemeContext = createContext("light");
const App = () => (
  <ThemeContext.Provider value="dark">
    <Toolbar />
  </ThemeContext.Provider>
);
```

---

## 🔹 8. What is Tree Shaking and how does React support it?

**Explanation:**

* **Tree Shaking** removes unused code during bundling (via Webpack, Rollup).
* React supports ES modules → allows bundlers to eliminate unused imports.

**Example:**

```js
// If you only use add()
import { add } from "./math";
// subtract() won’t be bundled
```

---

## 🔹 9. Controlled performance optimizations using React Profiler

**Explanation:** Profiler helps measure **which components re-render** and how long they take.

**Steps:**

1. Wrap component with `<Profiler>`.
2. Track re-renders.
3. Apply **React.memo, useMemo, useCallback**.

**Example:**

```jsx
<Profiler id="Counter" onRender={(id, phase, time) => {
  console.log(id, phase, time);
}}>
  <Counter />
</Profiler>
```

---

## 🔹 10. Best practices for structuring React projects

✅ Follow **feature-based folder structure**:

```
src/
  components/
    Button/
      Button.jsx
      Button.css
  pages/
    Home/
      Home.jsx
      Home.css
  hooks/
  context/
  store/
  utils/
  App.jsx
```

✅ Other practices:

* Use **functional components + hooks**.
* Use **Context/Redux** for global state.
* Use **lazy loading + code splitting**.
* Keep **reusable UI in components/**.
* Keep **API calls in services/**.

---

⚡Would you like me to make a **condensed PDF-style cheat sheet** of all these React Q\&A (Core → Hooks → Intermediate → Advanced → Ecosystem), so you can revise everything quickly before interviews?
