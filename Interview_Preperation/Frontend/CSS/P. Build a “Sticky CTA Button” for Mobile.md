Below is a **production-ready “Sticky CTA Button”** pattern used in mobile e-commerce apps (Flipkart, Amazon, Swiggy, Zomato, Uber, Airbnb).

It meets **all requirements**:

* ✔ Fixed at bottom
* ✔ Full width
* ✔ Shadow/elevation
* ✔ Does **not shift layout**
* ✔ Perfect mobile UX
* ✔ Pure CSS

---

# ✅ **Sticky CTA Button Preview**

---

# ✅ **FULL WORKING SOLUTION (HTML + CSS)**

---

# 🔹 **HTML**

```html
<div class="page-content">
  <p>Scroll this content...</p>
  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
  <p>More content below...</p>
  <p style="margin-bottom: 200vh;">Keep scrolling to test sticky CTA.</p>
</div>

<button class="sticky-cta">Buy Now — $49</button>
```

---

# 🔹 **CSS**

```css
/* Page content */
.page-content {
  padding: 20px;
  font-size: 18px;
}

/* Sticky CTA Button */
.sticky-cta {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;

  width: 100%;
  padding: 16px;
  font-size: 18px;
  font-weight: bold;
  color: white;
  background: #ff4c29;
  border: none;

  box-shadow: 0 -3px 12px rgba(0,0,0,0.25);
  cursor: pointer;

  display: flex;
  justify-content: center;
  align-items: center;
  
  z-index: 999;
}

/* Mobile-friendly touch target */
.sticky-cta {
  min-height: 60px;
}

/* Optional Hover Behavior (desktop only) */
@media (hover: hover) {
  .sticky-cta:hover {
    background: #e63f22;
  }
}
```

---

# ✅ **INTERVIEW-READY EXPLANATION**

---

# **1. Fixed Bottom Position (Correct Mobile Strategy)**

```css
position: fixed;
bottom: 0;
left: 0;
right: 0;
```

This ensures:

* CTA **always visible**
* CTA does **not move** when scrolling
* CTA does **not take up space in the layout** (no layout shift)

---

# **2. Full-Width Button**

```css
width: 100%;
```

This spans the entire bottom width, just like real mobile shopping apps.

---

# **3. Elevation / Shadow**

```css
box-shadow: 0 -3px 12px rgba(0,0,0,0.25);
```

Shadow above the CTA gives:

* Floating appearance
* Clear separation from content
* Better visual hierarchy
* Real mobile UX feel

---

# **4. Clickable Without Layout Shift**

We **do NOT** place the CTA inside content.
We place it *outside* and use:

```html
<button class="sticky-cta">...</button>
```

`position: fixed` ensures it **does not push content up/down**.

✔ Prevents unwanted movement
✔ Essential for real production UX

---

# **5. Responsive + Mobile-Friendly**

```css
min-height: 60px;
font-size: 18px;
```

Ensures:

* Large enough for fingers (Apple HIG recommends 44–60px)
* Works on all mobile screens
* Strong visibility

---

# **6. High Z-index**

```css
z-index: 999;
```

Prevents overlap from:

* Carousels
* Fixed headers
* Bottom nav bars

---

# 🎯 **Final Result**

| Requirement      | Achieved                            |
| ---------------- | ----------------------------------- |
| Sticky at bottom | ✔ `position: fixed`                 |
| Full width       | ✔ `left: 0; right: 0; width:100%`   |
| Elevation/shadow | ✔ box-shadow                        |
| No layout shift  | ✔ Fixed outside DOM flow            |
| Real mobile UX   | ✔ CTA large, visible, easy to click |

---

