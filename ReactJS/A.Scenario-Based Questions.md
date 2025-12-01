Below are **clear, interview-ready, real-world React answers** for performance, debugging, folder structure, JWT security, pagination, and state update issues.
These questions commonly appear in **2+ years experience** frontend interviews.

---

# =========================================

# ✅ **1. How will you avoid re-rendering of child components unnecessarily?**

# =========================================

Unnecessary re-renders slow down the UI. Solutions:

---

## ⭐ 1. **Use `React.memo` for child components**

```jsx
const Child = React.memo(function Child({ value }) {
  console.log("Child rendered");
  return <div>{value}</div>;
});
```

Only re-renders when `value` changes.

---

## ⭐ 2. **Use `useCallback` when passing functions**

```jsx
const handleClick = useCallback(() => {
  console.log("clicked");
}, []);
```

Helps React.memo because reference stays the same.

---

## ⭐ 3. **Use `useMemo` for expensive calculations**

```jsx
const result = useMemo(() => calculate(data), [data]);
```

---

## ⭐ 4. **Avoid inline objects/arrays**

❌ Causes new reference every render:

```jsx
<Child config={{ dark: true }} />
```

✔ Correct:

```jsx
const config = useMemo(() => ({ dark: true }), []);
```

---

## ⭐ 5. **Split components using dynamic import**

```jsx
const Chart = React.lazy(() => import("./Chart"));
```

---

### 🎯 Interview summary:

> Use React.memo + useCallback + useMemo + stable references to avoid unnecessary re-renders.

---

# =========================================

# ✅ **2. You have a slow page — how will you debug and optimize it?**

# =========================================

### ⭐ Step-by-step debugging approach:

---

## ✔ 1. **Use React Profiler**

Checks:

* Which components re-render?
* How long each render took?
* Why did it re-render?

---

## ✔ 2. **Check for unnecessary re-renders**

Use:

* React.memo
* useCallback
* useMemo

---

## ✔ 3. **Optimize expensive operations**

Examples:

* Heavy loops
* Large array filtering
* Formatting inside render

Move heavy logic to:

```jsx
useMemo(() => heavyWork(), [deps]);
```

---

## ✔ 4. **Avoid API calls inside render or missing dependency arrays**

Common mistake:

```jsx
useEffect(() => {
  fetchData();
});
```

→ Causes infinite API calls → slow page

---

## ✔ 5. **Use windowing for large lists**

`react-window`
`react-virtualized`

---

## ✔ 6. **Enable code splitting**

Lazy load heavy pages.

---

## ✔ 7. **Reduce bundle size**

* Remove unused packages
* Use tree shaking
* Compress images

---

### 🎯 Interview summary:

> First profile the app, then fix unnecessary re-renders, memoize heavy work, use windowing for large lists, and optimize bundle size.

---

# =========================================

# ✅ **3. API call is getting fired multiple times — what could be the reason?**

# =========================================

### ⭐ Root causes:

---

## ✔ 1. Missing dependency array in `useEffect`

```jsx
useEffect(() => {
  fetchData();
}); // ❌ Runs on every render
```

✔ Fix:

```jsx
useEffect(() => {
  fetchData();
}, []);
```

---

## ✔ 2. Function/prop reference is unstable

If `fetchData` is defined inside component:

```jsx
useEffect(() => {
  fetchData();
}, [fetchData]); // fetchData changes every render → infinite calls
```

✔ Fix:

```jsx
const fetchData = useCallback(() => { ... }, []);
```

---

## ✔ 3. React Strict Mode (Development)

In React 18, React **double-invokes effects in development**.

Fix: This ONLY happens in dev, not production.

---

## ✔ 4. Component unmount/remount loop

Conditional rendering mistake:

```jsx
{isVisible && <Component />}
```

---

## ✔ 5. Using fetch inside render

❌ Never call fetch inside render:

```jsx
const data = fetch(url); // wrong
```

---

### 🎯 Interview summary:

> The most common cause is missing or incorrect dependency arrays, or unstable function references.

---

# =========================================

# ✅ **4. How to design a scalable folder structure for a large React project?**

# =========================================

A good scalable structure:

```
src/
 ├── components/
 │    ├── Button/
 │    │    ├── Button.jsx
 │    │    ├── Button.test.js
 │    │    ├── Button.css
 │    │    └── index.js
 │    └── Card/
 │
 ├── pages/
 │    ├── Home/
 │    ├── Dashboard/
 │
 ├── hooks/
 │    ├── useAuth.js
 │    └── useFetch.js
 │
 ├── context/
 │    ├── AuthContext.js
 │
 ├── services/
 │    ├── api.js (axios configuration)
 │
 ├── store/
 │    ├── slices/
 │    └── index.js
 │
 ├── utils/
 │    ├── formatDate.js
 │
 ├── assets/
 │    ├── images/
 │    └── icons/
 │
 └── App.js
```

---

### Rules for scalability:

✔ Component-based structure
✔ Each feature/page in its own folder
✔ Keep hooks reusable
✔ Store global state in `store/`
✔ Keep API logic separate in `services/`
✔ Use barrel files (`index.js`)

---

### 🎯 Interview summary:

> Organize code by feature, not by file type. Keep components, hooks, services, and state modular.

---

# =========================================

# ✅ **5. How will you store JWT tokens securely?**

# =========================================

### ❌ WRONG (never do this)

* localStorage → vulnerable to XSS
* sessionStorage → also vulnerable

---

### ⭐ BEST PRACTICE (Secure)

✔ **Store JWT in HttpOnly Cookies**

Benefits:

* Cannot be accessed by JS (prevents XSS)
* Automatically sent with each request

---

## ❗ Refresh token strategy:

* Access token → short-lived (5–15 minutes)
* Refresh token → HttpOnly cookie

---

### 🎯 Interview summary:

> JWT should be stored in HttpOnly secure cookies to prevent XSS. Access tokens should be short-lived.

---

# =========================================

# ✅ **6. How to implement pagination efficiently?**

# =========================================

### ⭐ Backend pagination example:

```js
GET /users?page=1&limit=20
```

---

### ⭐ React approach:

1. Call API with page & limit
2. Show loading state
3. Cache results (optional)
4. Update only visible part of UI

Example:

```jsx
function Users() {
  const [page, setPage] = useState(1);

  useEffect(() => {
    fetch(`/api/users?page=${page}`)
      .then(res => res.json())
      .then(data => setUsers(data));
  }, [page]);

  return (
    <>
      <UserList users={users} />
      <button onClick={() => setPage(page + 1)}>Next</button>
    </>
  );
}
```

---

## ⭐ Best optimization techniques:

✔ Only load required data
✔ Prefetch next page
✔ Use react-query for caching
✔ Use windowing if list is large

---

### 🎯 Interview summary:

> Efficient pagination loads only needed data, avoids full list rendering, and can use windowing and caching for performance.

---

# =========================================

# ✅ **7. Component is not updating even after state change — why?**

# =========================================

### Common reasons:

---

## ❌ 1. State mutated directly (React doesn’t detect mutation)

```jsx
state.count = 5; // wrong
```

✔ Fix:

```jsx
setState(prev => ({ count: prev.count + 1 }));
```

---

## ❌ 2. Using same object reference

```jsx
setUser(user); // same object reference → no re-render
```

✔ Fix:

```jsx
setUser({ ...user });
```

---

## ❌ 3. React.memo blocking re-renders

Child won't update if props appear unchanged.

---

## ❌ 4. State update inside closure uses stale value

```jsx
setCount(count + 1); // stale if used twice
```

✔ Fix:

```jsx
setCount(prev => prev + 1);
```

---

## ❌ 5. Incorrect dependency array in useEffect

```jsx
useEffect(() => {
  setValue(propValue);
}, []); // runs only once
```

---

## ❌ 6. Async state update not awaited (setState is async)

```jsx
console.log(count); // old value
```

---

### 🎯 Interview summary:

> If a component is not updating, most likely the state was mutated directly, the reference didn’t change, or memoization prevented re-render.

---

