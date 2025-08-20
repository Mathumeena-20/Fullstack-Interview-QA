## 1. **Explain Code Splitting in React**

* **Code Splitting** = Breaking app bundle into smaller chunks so only required code is loaded.
* Improves performance and reduces **initial load time**.
* Achieved using **`React.lazy` + `Suspense`** or bundlers like Webpack.

🔹 Example:

```jsx
// Lazy load component
const Dashboard = React.lazy(() => import("./Dashboard"));

function App() {
  return (
    <React.Suspense fallback={<p>Loading...</p>}>
      <Dashboard />
    </React.Suspense>
  );
}
```

---

## 2. **What is React Fiber Scheduling?**

* Fiber = React’s new reconciliation engine (React 16+).
* It **splits rendering work into small units (fibers)** so React can pause, resume, and prioritize tasks.
* Enables **Concurrent Mode** (smooth UI, avoids blocking the main thread).

Think of Fiber as a **task scheduler** that decides **which component updates first**.

---

## 3. **What is Server-Side Rendering (SSR) in React?**

* SSR = Rendering React components to HTML **on the server** before sending to browser.
* Improves SEO & first-load performance.
* Used in frameworks like **Next.js**.

🔹 Example (Next.js):

```jsx
export async function getServerSideProps() {
  const res = await fetch("https://jsonplaceholder.typicode.com/users");
  const data = await res.json();
  return { props: { users: data } };
}

function Users({ users }) {
  return <ul>{users.map(u => <li key={u.id}>{u.name}</li>)}</ul>;
}
```

---

## 4. **Difference between CSR and SSR**

| Feature    | CSR (Client-Side Rendering)       | SSR (Server-Side Rendering)        |
| ---------- | --------------------------------- | ---------------------------------- |
| Rendering  | Done in **browser (JS)**          | Done on **server**                 |
| First Load | Slower (JS bundle loads first)    | Faster (HTML delivered first)      |
| SEO        | Poor (empty HTML initially)       | Good (HTML available for crawlers) |
| Use Case   | SPAs (Dashboards, internal tools) | Public apps, blogs, e-commerce     |

---

## 5. **How does Hydration work in React?**

* Hydration = React takes server-rendered HTML and **attaches event listeners** to make it interactive.
* Used in SSR/Static apps (Next.js).

🔹 Example:

```jsx
// Server sends HTML: <button>Click</button>
// React hydrates it and attaches onClick
ReactDOM.hydrate(<App />, document.getElementById("root"));
```

---

## 6. **Difference between React.memo and useMemo**

* `React.memo` → Wraps a **component** to memoize its rendering.
* `useMemo` → Memoizes a **computed value** inside a component.

🔹 Example:

```jsx
const Child = React.memo(({ value }) => {
  console.log("Rendered");
  return <p>{value}</p>;
});

function Parent({ num }) {
  const squared = React.useMemo(() => num * num, [num]);
  return <Child value={squared} />;
}
```

---

## 7. **Difference between PureComponent and React.memo**

* `PureComponent` → Class components. Prevents re-render if props/state didn’t change (shallow comparison).
* `React.memo` → Functional component equivalent of `PureComponent`.

🔹 Example:

```jsx
class MyComponent extends React.PureComponent {
  render() {
    return <h1>{this.props.name}</h1>;
  }
}

const MyFunctional = React.memo(function({ name }) {
  return <h1>{name}</h1>;
});
```

---

## 8. **How do you Optimize Performance in React Apps?**

* Use **React.memo** / **PureComponent** to avoid re-renders.
* Use **useMemo** and **useCallback** for expensive calculations/functions.
* Implement **Code Splitting** (`React.lazy`).
* Use **React Profiler** to find bottlenecks.
* Use **windowing/virtualization** (react-window, react-virtualized) for large lists.
* Avoid **anonymous functions** in render.
* Use **throttling/debouncing** for event-heavy updates.

---

## 9. **Difference between Redux, MobX, Zustand, Recoil**

| Library     | Type                        | Pros                                         | Cons                          |
| ----------- | --------------------------- | -------------------------------------------- | ----------------------------- |
| **Redux**   | Predictable state container | Centralized store, great tooling             | Verbose, boilerplate          |
| **MobX**    | Reactive state management   | Simple, less boilerplate                     | Less strict, debugging harder |
| **Zustand** | Lightweight global state    | Minimal API, easy to use                     | Less ecosystem support        |
| **Recoil**  | Experimental FB library     | Works seamlessly with React, async selectors | Still evolving                |

Use Redux for **large apps**, Zustand for **small/medium apps**, MobX if you prefer **observable pattern**, Recoil for **React-first state management**.

---

## 10. **Explain Concurrent Mode in React 18**

* Concurrent Mode (React 18 → "Concurrent Rendering") allows React to **prepare multiple UI updates simultaneously**.
* It doesn’t block rendering → smoother UX.
* Features:

  * **Automatic Batching**: multiple state updates combined.
  * **Transitions**: differentiate urgent vs non-urgent updates.
  * **Suspense Improvements**: async loading states.

🔹 Example (Transition):

```jsx
function Search() {
  const [query, setQuery] = React.useState("");
  const [results, setResults] = React.useState([]);
  const [isPending, startTransition] = React.useTransition();

  const handleChange = (e) => {
    setQuery(e.target.value);
    startTransition(() => {
      // simulate expensive operation
      setResults(Array(2000).fill(e.target.value));
    });
  };

  return (
    <>
      <input value={query} onChange={handleChange} />
      {isPending ? <p>Loading...</p> : results.map((r, i) => <div key={i}>{r}</div>)}
    </>
  );
}
```

Here, typing (urgent) is smooth, while list rendering (non-urgent) happens in the background.

---

✅ That covers **all 10 Advanced React topics with clear explanations and examples**.

Would you like me to now create a **mindmap-style summary (Core → Hooks → Intermediate → Advanced)** so you can revise everything in one glance before interviews?
