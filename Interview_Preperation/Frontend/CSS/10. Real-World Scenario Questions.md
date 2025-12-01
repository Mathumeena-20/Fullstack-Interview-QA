# ✅ **1. How do you center a div horizontally and vertically using Flexbox?**

### **CSS**

```css
.container {
  display: flex;
  justify-content: center; /* horizontal */
  align-items: center;      /* vertical */
  height: 100vh;
}
```

### **HTML**

```html
<div class="container">
  <div class="box">Centered</div>
</div>
```

✔ This is the simplest and most common method.

---

# ✅ **2. How do you create a sticky header?**

`position: sticky` keeps an element fixed **until its parent scrolls away**.

### Example

```css
header {
  position: sticky;
  top: 0;
  background: white;
  padding: 10px;
  z-index: 100;
}
```

✔ No JS needed
✔ Sticks only when scrolling past its initial position

---

# ✅ **3. How to create a 3-column layout with CSS Grid?**

### Example

```css
.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
```

✔ `repeat(3, 1fr)` = 3 equal columns
✔ Use `gap` for spacing

---

# ✅ **4. How to prevent layout shift in images without CSS tricks?**

**Set `width` and `height` attributes in HTML.**
Browsers use these to compute the **aspect ratio** and reserve space → no layout shift.

### Example

```html
<img src="photo.jpg" width="800" height="600" alt="">
```

✔ Prevents CLS (Cumulative Layout Shift)
✔ No extra CSS required
✔ Recommended by Google Lighthouse

---

# ✅ **5. How would you style a responsive navigation menu?**

Use Flexbox for desktop, and a column layout for smaller screens → using modern CSS features like `clamp()` and container queries or simple flex-wrap.

### Example (no JS version)

```css
.nav {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}

.nav a {
  padding: .5rem 1rem;
}
```

For dropdown toggle (JS optional):

```css
@media (max-width: 600px) {
  .nav {
    flex-direction: column;
  }
}
```

✔ Items wrap on small screens
✔ No complicated media queries necessary if using `flex-wrap`

---

# ✅ **6. How do you truncate multi-line text with ellipsis?**

Use `-webkit-line-clamp`.

### **CSS**

```css
.text {
  display: -webkit-box;
  -webkit-line-clamp: 3;    /* number of lines */
  -webkit-box-orient: vertical;
  overflow: hidden;
}
```

✔ Works on all modern browsers
✔ Perfect for card descriptions, previews, etc.

---

# ✅ **7. How do you handle dark mode in CSS?**

### **Method 1 — Using prefers-color-scheme**

```css
:root {
  --bg: #ffffff;
  --text: #000;
}

@media (prefers-color-scheme: dark) {
  :root {
    --bg: #111;
    --text: #eee;
  }
}

body {
  background: var(--bg);
  color: var(--text);
}
```

✔ Automatically switches based on system settings
✔ Uses CSS variables for theme control

---

### **Method 2 — Toggle using a class**

```css
:root {
  --bg: #fff;
  --text: #000;
}
.dark {
  --bg: #111;
  --text: #eee;
}
body {
  background: var(--bg);
  color: var(--text);
}
```

### JS for toggling:

```js
document.body.classList.toggle('dark');
```

---

# ✅ **8. How to create a card layout that is responsive without media queries?**

Use **CSS Grid with `auto-fit` or `auto-fill` + `minmax()`**.

### Example

```css
.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}
```

✔ Cards automatically resize
✔ 1 → 2 → 3 → 4 columns depending on width
✔ No media queries needed
✔ Perfect for real-world UI (Amazon, Flipkart, Netflix)

---

# 🎯 Quick Summary Table

| Question             | Short Answer                                    |
| -------------------- | ----------------------------------------------- |
| Center div           | `justify-content:center` + `align-items:center` |
| Sticky header        | `position: sticky; top: 0;`                     |
| 3-column grid        | `grid-template-columns: repeat(3, 1fr)`         |
| Prevent layout shift | Add `width` & `height` attributes               |
| Responsive nav       | Flexbox + flex-wrap or media queries            |
| Multi-line ellipsis  | `-webkit-line-clamp`                            |
| Dark mode            | CSS variables + prefers-color-scheme            |
| Responsive cards     | `auto-fit` + `minmax()`                         |

---


✔ A complete CSS interview cheat-sheet
