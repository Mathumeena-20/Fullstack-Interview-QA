## 1. Can you explain how the Redux flow works in your project?

### 🔹 Explanation

Redux follows a **unidirectional data flow**:

1. **Action** → describes what happened (e.g., `FETCH_CONFIGS_SUCCESS`).
2. **Reducer** → takes the current state + action, and returns a new state.
3. **Store** → holds the global state tree.
4. **UI (React Components)** → subscribes to the store using `useSelector` and dispatches actions using `useDispatch`.

### 🔹 Example (from your Vehicle Configuration Project)

```javascript
// actions.js
export const fetchConfigs = () => async (dispatch) => {
  const res = await fetch("/api/configurations");
  const data = await res.json();
  dispatch({ type: "FETCH_CONFIGS_SUCCESS", payload: data });
};

// reducer.js
const initialState = { configs: [] };

export const configReducer = (state = initialState, action) => {
  switch (action.type) {
    case "FETCH_CONFIGS_SUCCESS":
      return { ...state, configs: action.payload };
    default:
      return state;
  }
};

// In React Component
import { useSelector, useDispatch } from "react-redux";
import { useEffect } from "react";
import { fetchConfigs } from "./actions";

function ConfigList() {
  const dispatch = useDispatch();
  const configs = useSelector((state) => state.configs);

  useEffect(() => {
    dispatch(fetchConfigs());
  }, [dispatch]);

  return (
    <ul>
      {configs.map((c) => (
        <li key={c.id}>{c.name}</li>
      ))}
    </ul>
  );
}
```

👉 This shows the **Redux flow**:
Component → `dispatch(action)` → Reducer updates → Store → Component re-renders.

---

## 2. How do you handle API calls in React (mention hooks like useEffect, useState)?

### 🔹 Explanation

* `useState` → manage state (loading, error, data).
* `useEffect` → perform side effects like API calls when the component mounts or dependencies change.

### 🔹 Example

```javascript
import React, { useState, useEffect } from "react";

function VehicleList() {
  const [vehicles, setVehicles] = useState([]);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetch("/api/vehicles")
      .then((res) => res.json())
      .then((data) => {
        setVehicles(data);
        setLoading(false);
      })
      .catch(() => setLoading(false));
  }, []); // runs once when component mounts

  if (loading) return <p>Loading...</p>;

  return (
    <ul>
      {vehicles.map((v) => (
        <li key={v.id}>{v.name}</li>
      ))}
    </ul>
  );
}
```

👉 In your project, you likely used `useEffect` for **fetching configs/simulations** and `useState` for storing results before dispatching to Redux.

---

## 3. What’s the difference between a controlled and uncontrolled component?

### 🔹 Controlled Component

* React manages the form input state.
* Value comes from `useState` (single source of truth).
* Easier to validate and manipulate input values.

```javascript
function ControlledInput() {
  const [value, setValue] = useState("");
  return (
    <input
      value={value}
      onChange={(e) => setValue(e.target.value)}
    />
  );
}
```

### 🔹 Uncontrolled Component

* The DOM manages the input state (via `ref`).
* Useful when you don’t need to track input on every keystroke.

```javascript
import { useRef } from "react";

function UncontrolledInput() {
  const inputRef = useRef();
  const handleSubmit = () => {
    alert(inputRef.current.value);
  };
  return (
    <>
      <input ref={inputRef} />
      <button onClick={handleSubmit}>Submit</button>
    </>
  );
}
```

👉 In interview: say *“I prefer controlled components for forms since I can validate and control user input easily, but I use uncontrolled when performance is critical or I just need the final value (like file uploads).”*

---

## 4. Can you explain React Router v5 vs v6 differences?

### 🔹 Key Differences

1. **Routes Syntax**

   * v5: `<Route component={Component} />`
   * v6: `<Route element={<Component />} />`

2. **Switch → Routes**

   * v5: `<Switch>` matches the first route.
   * v6: `<Routes>` replaces it.

3. **Nested Routes** → Simplified in v6 with relative paths.

4. **Redirect → Navigate**

   * v5: `<Redirect to="/home" />`
   * v6: `<Navigate to="/home" />`

### 🔹 Example

**React Router v5**

```jsx
<Switch>
  <Route path="/dashboard" component={Dashboard} />
  <Redirect from="/" to="/dashboard" />
</Switch>
```

**React Router v6**

```jsx
<Routes>
  <Route path="/dashboard" element={<Dashboard />} />
  <Route path="/" element={<Navigate to="/dashboard" />} />
</Routes>
```

👉 In interview: say *“I migrated my project from v5 to v6, and the biggest changes were switching from `Switch` to `Routes`, and using `element` instead of `component`. Also, nested routing became much cleaner.”*
