Below are **clean, interview-ready React solutions** for tasks **31–34**, including routing with params, query-param filters, smooth scrolling, and custom 404 auto-redirects.
These match real industry scenarios for **2+ years React developer** roles.

---

# ======================================================

# ✅ **31. User Profile Route (`/users/:id`)**

### Fetch user data based on dynamic route parameter

======================================================

## ⭐ Step 1 — Define Dynamic Route

```jsx
// App.jsx
import { Routes, Route } from "react-router-dom";
import UserProfile from "./UserProfile";

<Routes>
  <Route path="/users/:id" element={<UserProfile />} />
</Routes>
```

---

## ⭐ Step 2 — Use `useParams()` to load data

```jsx
import { useParams } from "react-router-dom";
import { useEffect, useState } from "react";

function UserProfile() {
  const { id } = useParams();
  const [user, setUser] = useState(null);

  useEffect(() => {
    fetch(`/api/users/${id}`)
      .then(res => res.json())
      .then(setUser);
  }, [id]);

  if (!user) return <p>Loading...</p>;

  return (
    <>
      <h2>{user.name}</h2>
      <p>Email: {user.email}</p>
    </>
  );
}
```

---

### ✔ Explanation

* `useParams()` extracts `id` from URL
* API is called on mount and whenever `id` changes
* Perfect for profile/details pages like GitHub, Amazon product page, etc.

---

# ======================================================

# ✅ **32. Query Parameter Filters**

### Sync filters with URL (?category=shoes&sort=price_asc)

======================================================

React Router v6.4+ uses `useSearchParams()`.

---

## ⭐ Step 1 — Read & write query params

```jsx
import { useSearchParams } from "react-router-dom";

function ProductsPage() {
  const [params, setParams] = useSearchParams();

  const category = params.get("category") || "";
  const sort = params.get("sort") || "price_asc";

  const updateFilter = (key, value) => {
    params.set(key, value);
    setParams(params); // updates URL & triggers rerender
  };

  return (
    <>
      <select
        value={category}
        onChange={(e) => updateFilter("category", e.target.value)}
      >
        <option value="">All</option>
        <option value="shoes">Shoes</option>
        <option value="bags">Bags</option>
      </select>

      <select
        value={sort}
        onChange={(e) => updateFilter("sort", e.target.value)}
      >
        <option value="price_asc">Price Low→High</option>
        <option value="price_desc">Price High→Low</option>
      </select>

      {/* Example: Using URL params in API call */}
      <ProductList category={category} sort={sort} />
    </>
  );
}
```

---

### ✔ Explanation

* URL always shows filters (`?category=shoes&sort=price_asc`)
* Page is shareable → deep-linkable
* Changing filters updates URL and re-renders page

This is exactly how **Amazon, Flipkart & Airbnb** sync filters.

---

# ======================================================

# ✅ **33. Scroll to Section on Navigation Click**

### Smooth scrolling to a specific page section

======================================================

## ⭐ HTML Structure

```html
<button onClick={() => scrollToSection("pricing")}>View Pricing</button>

<div id="pricing">Pricing Section</div>
```

---

## ⭐ Scroll Function

```jsx
const scrollToSection = (id) => {
  const element = document.getElementById(id);
  if (element) {
    element.scrollIntoView({ behavior: "smooth" });
  }
};
```

---

## ⭐ Example UI Component

```jsx
function Navbar() {
  return (
    <nav>
      <button onClick={() => scrollToSection("about")}>About</button>
      <button onClick={() => scrollToSection("pricing")}>Pricing</button>
      <button onClick={() => scrollToSection("faq")}>FAQ</button>
    </nav>
  );
}
```

---

### ✔ Explanation

* Uses browser’s native `scrollIntoView({ behavior: 'smooth' })`
* No library required
* Clean and smooth UX
* Used in landing pages and marketing sites

---

# ======================================================

# ✅ **34. Custom 404 Page with Auto-Redirect**

======================================================

### ⭐ Step 1 — Add 404 Route

```jsx
<Routes>
  <Route path="*" element={<NotFound />} />
</Routes>
```

---

## ⭐ Step 2 — Auto redirect after 3 seconds

```jsx
import { useEffect } from "react";
import { useNavigate } from "react-router-dom";

function NotFound() {
  const navigate = useNavigate();

  useEffect(() => {
    const timer = setTimeout(() => {
      navigate("/");
    }, 3000);

    return () => clearTimeout(timer);
  }, []);

  return (
    <div style={{ padding: 40 }}>
      <h1>404 - Page Not Found</h1>
      <p>Redirecting to home in 3 seconds...</p>
    </div>
  );
}
```

---

### ✔ Explanation

* `path="*"` catches all undefined routes
* Redirects automatically using `useNavigate()`
* Practical for live apps where old URLs may break (SaaS dashboards, e-commerce)

---

# 🎯 FINAL INTERVIEW SUMMARY (Short Version)

| Feature              | Core Concept                             |
| -------------------- | ---------------------------------------- |
| User profile route   | `useParams()` + fetch data by ID         |
| Query params filters | `useSearchParams()` to sync URL          |
| Scroll to section    | `scrollIntoView({ behavior: "smooth" })` |
| Custom 404           | Catch-all route + auto redirect          |

These are real-world React Router tasks used in production environments.

---

