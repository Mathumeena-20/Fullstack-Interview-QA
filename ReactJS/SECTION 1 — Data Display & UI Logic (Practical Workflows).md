Below are **clean, interview-ready React solutions with explanation + code examples** for all 5 real business UI scenarios.
These cover **status badges, lazy loading, infinite scroll, notification dropdown, and localStorage usage** — perfect for **2+ years React developer interviews**.

---

# ===============================================

# ✅ **1. Customer List with Status Badges**

# ===============================================

### Requirements:

* Show customers in a list
* Status badge colors:

  * **Active → Green**
  * **Inactive → Red**
  * **Pending → Yellow**

---

## ⭐ Example Component

```jsx
const statusStyles = {
  active: { background: "green", color: "white" },
  inactive: { background: "red", color: "white" },
  pending: { background: "goldenrod", color: "black" }
};

function CustomerList({ customers }) {
  return (
    <ul>
      {customers.map(c => (
        <li key={c.id} style={{ marginBottom: 10 }}>
          {c.name}{" "}
          <span style={{ padding: "4px 8px", borderRadius: 4, ...statusStyles[c.status] }}>
            {c.status.toUpperCase()}
          </span>
        </li>
      ))}
    </ul>
  );
}
```

### ✔ Explanation

* Color-coded badges using dynamic styling based on status
* Keys for stable rendering
* Good for CRM dashboards

---

# ===============================================

# ✅ **2. Product Grid with Lazy Loading (Intersection Observer)**

# ===============================================

Lazy load images **only when visible** → huge performance improvement.

---

## ⭐ Lazy Image Component

```jsx
function LazyImage({ src, alt }) {
  const imgRef = useRef();

  useEffect(() => {
    const observer = new IntersectionObserver(
      entries => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            imgRef.current.src = src;
            observer.unobserve(imgRef.current);
          }
        });
      },
      { threshold: 0.2 }
    );

    observer.observe(imgRef.current);

    return () => observer.disconnect();
  }, [src]);

  return <img ref={imgRef} alt={alt} width="200" height="200" />;
}
```

### Product Grid:

```jsx
function ProductGrid({ products }) {
  return (
    <div style={{ display: "grid", gridTemplateColumns: "repeat(4, 1fr)", gap: 20 }}>
      {products.map(p => (
        <LazyImage key={p.id} src={p.image} alt={p.name} />
      ))}
    </div>
  );
}
```

### ✔ Explanation

* IntersectionObserver watches for visibility
* When visible → image loads
* Prevents loading 100+ images at once
* Big performance win for e-commerce apps

---

# ===============================================

# ✅ **3. Infinite Scroll Chat Window**

# ===============================================

### Requirements:

* Load older messages when user scrolls to top
* Like WhatsApp / Slack behavior

---

## ⭐ Chat Component

```jsx
function ChatWindow() {
  const [messages, setMessages] = useState([]);
  const chatRef = useRef();

  // Load initial messages
  useEffect(() => {
    loadMoreMessages();
  }, []);

  const loadMoreMessages = async () => {
    const older = await fetch("/api/messages?before=" + messages[0]?.id)
      .then(res => res.json());
    setMessages(prev => [...older, ...prev]);
  };

  const handleScroll = () => {
    if (chatRef.current.scrollTop === 0) {
      loadMoreMessages();
    }
  };

  return (
    <div
      ref={chatRef}
      onScroll={handleScroll}
      style={{ height: 400, overflowY: "scroll", border: "1px solid #ccc" }}
    >
      {messages.map(m => (
        <div key={m.id}>{m.text}</div>
      ))}
    </div>
  );
}
```

### ✔ Explanation

* Watch when scroll reaches **top = 0**
* Prepend old messages into the array
* Preserve scroll position for smooth experience
* Common interview question

---

# ===============================================

# ✅ **4. Notification Dropdown with “Mark as Read”**

# ===============================================

### Requirements:

* Show last 10 notifications
* Allow marking each as read

---

## ⭐ Example Component

```jsx
function NotificationDropdown({ notifications, markRead }) {
  return (
    <div style={{ border: "1px solid #ddd", width: 250, padding: 10 }}>
      <h4>Notifications</h4>

      {notifications.slice(0, 10).map(n => (
        <div key={n.id} style={{ opacity: n.read ? 0.6 : 1 }}>
          <p>{n.text}</p>
          {!n.read && (
            <button onClick={() => markRead(n.id)}>Mark as read</button>
          )}
          <hr />
        </div>
      ))}
    </div>
  );
}
```

### Parent state management:

```jsx
function App() {
  const [notifications, setNotifications] = useState(initialData);

  const markRead = (id) => {
    setNotifications(notifs =>
      notifs.map(n => n.id === id ? { ...n, read: true } : n)
    );
  };

  return <NotificationDropdown notifications={notifications} markRead={markRead} />;
}
```

### ✔ Explanation

* Limit to latest 10 notifications
* Marking read updates the UI
* Mimics real-world dropdown patterns (Facebook, Gmail)

---

# ===============================================

# ✅ **5. “Recently Viewed” Section using localStorage**

# ===============================================

### Requirement:

* Store viewed product IDs
* Display them when user returns

---

## ⭐ Hook for Local Storage

```jsx
function useRecentlyViewed() {
  const [items, setItems] = useState(() => {
    return JSON.parse(localStorage.getItem("recently-viewed")) || [];
  });

  const addItem = (id) => {
    const updated = [id, ...items.filter(i => i !== id)].slice(0, 10);
    setItems(updated);
    localStorage.setItem("recently-viewed", JSON.stringify(updated));
  };

  return { items, addItem };
}
```

---

## ⭐ Usage inside Product Page:

```jsx
function ProductPage({ product }) {
  const { items, addItem } = useRecentlyViewed();

  useEffect(() => {
    addItem(product.id);
  }, [product.id]);

  return (
    <>
      <h1>{product.name}</h1>
      <RecentlyViewed ids={items} />
    </>
  );
}
```

---

## ⭐ Display Recently Viewed:

```jsx
function RecentlyViewed({ ids }) {
  return (
    <div>
      <h3>Recently Viewed</h3>
      {ids.map(id => (
        <p key={id}>Product #{id}</p>
      ))}
    </div>
  );
}
```

### ✔ Explanation

* Stores up to last 10 viewed items
* Avoids duplicates
* Loads stored products on page open
* Used in e-commerce websites like Amazon

---

# ===============================================

# 🎯 Final Interview Summary

# ===============================================

| Feature               | Main Concept                    |
| --------------------- | ------------------------------- |
| Customer badges       | Conditional styling             |
| Lazy loading images   | IntersectionObserver            |
| Infinite scroll chat  | Scroll listener + prepend items |
| Notification dropdown | Local state + list updates      |
| Recently viewed       | localStorage persistence        |

These problems test **real-world React skills**, not just theory.

---
