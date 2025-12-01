Below are **clean, scalable, REAL production-level React solutions** for tasks 16–20.
These cover **Context API, global alerts, theming, Redux Toolkit carts, multi-step wizards, and syncing state to localStorage** — all common in **2+ years React interviews**.

---

# =====================================================

# ✅ **16. Global Alert System (Toast Notifications via Context)**

=====================================================

## ⭐ ToastContext (Global Scope)

```jsx
import { createContext, useContext, useState } from "react";

const ToastContext = createContext();

export function ToastProvider({ children }) {
  const [toasts, setToasts] = useState([]);

  const showToast = (msg, type = "info") => {
    const id = Date.now();
    setToasts(t => [...t, { id, msg, type }]);

    setTimeout(() => {
      setToasts(t => t.filter(toast => toast.id !== id));
    }, 3000);
  };

  return (
    <ToastContext.Provider value={{ showToast }}>
      {children}
      <div className="toast-container">
        {toasts.map(t => (
          <div key={t.id} className={`toast ${t.type}`}>
            {t.msg}
          </div>
        ))}
      </div>
    </ToastContext.Provider>
  );
}

export const useToast = () => useContext(ToastContext);
```

---

## ⭐ Any component can trigger a toast

```jsx
function SaveButton() {
  const { showToast } = useToast();
  return (
    <button onClick={() => showToast("Saved Successfully!", "success")}>
      Save
    </button>
  );
}
```

---

### ✔ Explanation

* Context stores global `showToast()` function.
* Any component calls `useToast()` → triggers toast.
* Toast disappears with `setTimeout`.
* Used heavily in SaaS dashboards (success/error notifications).

---

# =====================================================

# ✅ **17. Theme Settings Stored Globally (Context)**

### Supports:

* Theme (light/dark)
* Font size
* Color scheme
  =====================================================

---

## ⭐ ThemeContext

```jsx
const ThemeContext = createContext();

export function ThemeProvider({ children }) {
  const [settings, setSettings] = useState({
    theme: "light",
    fontSize: 16,
    color: "#0055ff"
  });

  const updateTheme = (key, value) =>
    setSettings(prev => ({ ...prev, [key]: value }));

  return (
    <ThemeContext.Provider value={{ settings, updateTheme }}>
      <div style={{ 
        background: settings.theme === "dark" ? "#222" : "#fff",
        color: settings.color,
        fontSize: settings.fontSize
      }}>
        {children}
      </div>
    </ThemeContext.Provider>
  );
}

export const useTheme = () => useContext(ThemeContext);
```

---

## ⭐ UI to change theme

```jsx
function ThemeSettings() {
  const { settings, updateTheme } = useTheme();

  return (
    <>
      <label>Theme: </label>
      <select
        value={settings.theme}
        onChange={(e) => updateTheme("theme", e.target.value)}
      >
        <option value="light">Light</option>
        <option value="dark">Dark</option>
      </select>

      <label>Font Size: </label>
      <input
        type="number"
        value={settings.fontSize}
        onChange={(e) => updateTheme("fontSize", Number(e.target.value))}
      />
    </>
  );
}
```

---

### ✔ Explanation

* Global theme stored in Context.
* Updates instantly across all components.
* Excellent for dashboards/settings pages.

---

# =====================================================

# ✅ **18. Shopping Cart with Redux Toolkit**

Slice must support:

* add item
* remove item
* change quantity
  =====================================================

---

## ⭐ cartSlice.js

```jsx
import { createSlice } from "@reduxjs/toolkit";

const cartSlice = createSlice({
  name: "cart",
  initialState: [],
  reducers: {
    addItem: (state, action) => {
      const existing = state.find(i => i.id === action.payload.id);
      if (existing) {
        existing.qty += 1;
      } else {
        state.push({ ...action.payload, qty: 1 });
      }
    },

    removeItem: (state, action) =>
      state.filter(i => i.id !== action.payload),

    changeQty: (state, action) => {
      const { id, qty } = action.payload;
      const item = state.find(i => i.id === id);
      if (item) item.qty = qty;
    }
  }
});

export const { addItem, removeItem, changeQty } = cartSlice.actions;
export default cartSlice.reducer;
```

---

## ⭐ Usage Example

```jsx
const dispatch = useDispatch();

<button onClick={() => dispatch(addItem({ id: 1, name: "Shoe" }))}>
  Add to Cart
</button>

<input
  type="number"
  value={item.qty}
  onChange={(e) =>
    dispatch(changeQty({ id: item.id, qty: Number(e.target.value) }))
  }
/>

<button onClick={() => dispatch(removeItem(item.id))}>Remove</button>
```

---

### ✔ Explanation

* RTK auto-handles immutability using Immer.
* Very compact compared to classic Redux.
* Perfect real-world cart structure.

---

# =====================================================

# ✅ **19. Employee Onboarding Wizard (Redux State)**

### Multi-step form → state persists across pages

=====================================================

---

## ⭐ onboardingSlice.js

```jsx
import { createSlice } from "@reduxjs/toolkit";

const onboardingSlice = createSlice({
  name: "onboarding",
  initialState: {
    personal: {},
    address: {},
    documents: {}
  },
  reducers: {
    savePersonal: (state, action) => { state.personal = action.payload },
    saveAddress: (state, action) => { state.address = action.payload },
    saveDocuments: (state, action) => { state.documents = action.payload }
  }
});

export const { savePersonal, saveAddress, saveDocuments } = onboardingSlice.actions;
export default onboardingSlice.reducer;
```

---

## ⭐ Step 1 Component

```jsx
function PersonalStep() {
  const dispatch = useDispatch();
  const [data, setData] = useState({ name: "", age: "" });

  return (
    <button onClick={() => dispatch(savePersonal(data))}>
      Save & Next
    </button>
  );
}
```

---

## ⭐ Step 2 Component

```jsx
function AddressStep() {
  const dispatch = useDispatch();
  const [data, setData] = useState({ city: "", pin: "" });

  return (
    <button onClick={() => dispatch(saveAddress(data))}>
      Save & Next
    </button>
  );
}
```

---

## ⭐ Review Step

```jsx
function ReviewPage() {
  const onboarding = useSelector(state => state.onboarding);

  return <pre>{JSON.stringify(onboarding, null, 2)}</pre>;
}
```

---

### ✔ Explanation

* Redux stores step data so navigating between pages does NOT lose state.
* Perfect for enterprise onboarding workflows (HR portals, internal systems).

---

# =====================================================

# ✅ **20. Save App Preferences to Local Storage**

### Sync state with localStorage via useEffect

=====================================================

---

## ⭐ Store preferences in React state

```jsx
function Preferences() {
  const [prefs, setPrefs] = useState(() => {
    return JSON.parse(localStorage.getItem("prefs")) || {
      language: "en",
      theme: "light"
    };
  });

  useEffect(() => {
    localStorage.setItem("prefs", JSON.stringify(prefs));
  }, [prefs]);

  return (
    <>
      <select
        value={prefs.language}
        onChange={(e) =>
          setPrefs({ ...prefs, language: e.target.value })
        }
      >
        <option value="en">English</option>
        <option value="hi">Hindi</option>
      </select>

      <select
        value={prefs.theme}
        onChange={(e) =>
          setPrefs({ ...prefs, theme: e.target.value })
        }
      >
        <option value="light">Light</option>
        <option value="dark">Dark</option>
      </select>
    </>
  );
}
```

---

### ✔ Explanation

* Loads localStorage on initial render
* Auto-saves updates using `useEffect`
* Persistent preferences across page refreshes
* Common in dashboards + mobile apps

---

# 🎯 FINAL INTERVIEW SUMMARY

| Feature            | Key Concept                                |
| ------------------ | ------------------------------------------ |
| Global alert       | Context API + portal-like container        |
| Global theme       | Context + CSS variables or inline styles   |
| Shopping cart      | Redux Toolkit slice with add/remove/update |
| Onboarding wizard  | Multi-page Redux state persistence         |
| Local storage sync | Lazy initializer + useEffect               |

These are **real production-level solutions** that demonstrate you understand **React + Redux architecture**.

---

