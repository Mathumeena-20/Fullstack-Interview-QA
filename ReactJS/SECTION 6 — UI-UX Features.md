Below are **clean, interview-ready React solutions** for items **26–30**, including Accordion, Sidebar animation, Confirmation modal, Full-screen loader, and Skeleton loading.
All examples are production-style and perfect for **2+ years experience**.

---

# =====================================================

# ✅ **26. Accordion FAQ Section (Only One Open at a Time)**

=====================================================

### ⭐ State for active accordion

```jsx
function FAQAccordion({ items }) {
  const [active, setActive] = useState(null);

  const toggle = (index) => {
    setActive(prev => (prev === index ? null : index));
  };

  return (
    <div>
      {items.map((item, i) => (
        <div key={i} style={{ marginBottom: 10 }}>
          <button onClick={() => toggle(i)}>
            {item.question}
          </button>

          {active === i && (
            <div style={{ padding: 10, border: "1px solid #ccc" }}>
              {item.answer}
            </div>
          )}
        </div>
      ))}
    </div>
  );
}
```

---

### ✔ Explanation

* `active` stores the currently opened accordion index
* Clicking same question closes it
* Clicking another replaces the open one
* Ensures **only one opens at a time**

---

# =====================================================

# ✅ **27. Toggleable Sidebar with Smooth Animation**

=====================================================

### ⭐ CSS Transition for Slide Animation

```css
.sidebar {
  width: 250px;
  transition: transform 0.3s ease;
  background: #333;
  color: white;
  padding: 20px;
  position: fixed;
  height: 100%;
}

.sidebar.closed {
  transform: translateX(-100%);
}
```

---

## ⭐ React Component

```jsx
function Sidebar() {
  const [open, setOpen] = useState(false);

  return (
    <>
      <button onClick={() => setOpen(o => !o)}>
        Toggle Sidebar
      </button>

      <div className={`sidebar ${open ? "" : "closed"}`}>
        <h2>Menu</h2>
        <p>Dashboard</p>
        <p>Settings</p>
      </div>
    </>
  );
}
```

---

### ✔ Explanation

* Uses CSS transform for GPU-accelerated animation
* Sidebar shifts in/out smoothly
* Button toggles open/closed state

---

# =====================================================

# ✅ **28. Modal Confirmation Dialog (Delete Confirmation)**

=====================================================

### ⭐ Modal Component

```jsx
function ConfirmModal({ open, onClose, onConfirm }) {
  if (!open) return null;

  return (
    <div style={{
      position:"fixed", top:0, left:0, width:"100%", height:"100%",
      background:"rgba(0,0,0,0.5)",
      display:"flex", alignItems:"center", justifyContent:"center"
    }}>
      <div style={{ background:"white", padding:20 }}>
        <h3>Are you sure?</h3>
        <p>This action cannot be undone.</p>

        <button onClick={onConfirm}>Yes, Delete</button>
        <button onClick={onClose}>Cancel</button>
      </div>
    </div>
  );
}
```

---

## ⭐ Usage

```jsx
function DeleteButton() {
  const [modalOpen, setModalOpen] = useState(false);

  const deleteItem = () => {
    console.log("Item deleted");
    setModalOpen(false);
  };

  return (
    <>
      <button onClick={() => setModalOpen(true)}>Delete</button>
      <ConfirmModal
        open={modalOpen}
        onClose={() => setModalOpen(false)}
        onConfirm={deleteItem}
      />
    </>
  );
}
```

---

### ✔ Explanation

* Modal overlays entire screen
* Prevents accidental deletion
* Works for critical UI operations (delete user, remove order, etc.)

---

# =====================================================

# ✅ **29. Full-Screen Loader While Page Fetches Data**

=====================================================

### ⭐ Loader UI

```jsx
function FullscreenLoader() {
  return (
    <div style={{
      position:"fixed", top:0, left:0, width:"100%", height:"100%",
      display:"flex", alignItems:"center", justifyContent:"center",
      background:"rgba(255,255,255,0.8)"
    }}>
      <div className="spinner" />
    </div>
  );
}
```

---

## ⭐ Usage in Page

```jsx
function Page() {
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetch("/api/page")
      .then(res => res.json())
      .then(() => setLoading(false));
  }, []);

  if (loading) return <FullscreenLoader />;

  return <h1>Page Data Loaded</h1>;
}
```

---

### ✔ Explanation

* Full-screen overlay blocks UI until data loads
* Used often in dashboards, admin panels
* Ensures page layout avoids visual jumping

---

# =====================================================

# ✅ **30. Skeleton Loading Screen**

=====================================================

### ⭐ Skeleton CSS

```css
.skeleton {
  background: #eee;
  height: 20px;
  margin-bottom: 10px;
  border-radius: 4px;
  overflow: hidden;
  position: relative;
}

.skeleton::after {
  content: "";
  position: absolute;
  top:0;
  left: -100%;
  height:100%;
  width:100%;
  background: linear-gradient(90deg, transparent, #ddd, transparent);
  animation: shimmer 1.2s infinite;
}

@keyframes shimmer {
  100% { left: 100%; }
}
```

---

## ⭐ Skeleton Component

```jsx
function UserSkeleton() {
  return (
    <div>
      <div className="skeleton" style={{ width: "60%" }}></div>
      <div className="skeleton" style={{ width: "40%" }}></div>
      <div className="skeleton" style={{ width: "80%" }}></div>
    </div>
  );
}
```

---

## ⭐ Use in Page

```jsx
function UserPage() {
  const [loading, setLoading] = useState(true);
  const [user, setUser] = useState(null);

  useEffect(() => {
    fetch("/api/user")
      .then(res => res.json())
      .then(data => {
        setUser(data);
        setLoading(false);
      });
  }, []);

  if (loading) return <UserSkeleton />;

  return <h2>{user.name}</h2>;
}
```

---

### ✔ Explanation

* Skeleton approximates the layout before data loads
* Provides better UX than spinner
* Prevents layout shifting (CLS issues)

---

# 🎯 FINAL INTERVIEW SUMMARY

| Feature            | Technique                             |
| ------------------ | ------------------------------------- |
| Accordion          | Track active index in state           |
| Sidebar            | CSS transition + toggle state         |
| Confirmation Modal | Controlled component + overlay        |
| Fullscreen Loader  | Fixed-position overlay while fetching |
| Skeleton Loading   | Animated shimmer placeholders         |

These patterns appear in **real production UIs**, especially admin dashboards, CRMs, and e-commerce apps.

---

