## 1️⃣ CSS Variables (Custom Properties)

**Explanation:**

* Declared using `--var-name` inside a selector (often `:root` for global use).
* Accessed with `var(--var-name)`.
* Useful for **theme management, reusability, and consistency**.

**Example:**

```html
<style>
:root {
  --main-color: blue;
  --padding: 10px;
}
.box {
  background: var(--main-color);
  padding: var(--padding);
}
</style>

<div class="box">This uses CSS variable</div>
```

---

## 2️⃣ Absolute Units (px) vs Relative Units (em, rem) in Font Sizing

**Explanation:**

* **px** → fixed size, does not change with parent/root.
* **em** → relative to **parent’s font-size**.
* **rem** → relative to **root (html) font-size**.

**Example:**

```html
<style>
html { font-size: 16px; }
.parent { font-size: 20px; }
.child-em { font-size: 2em; }  /* 40px (20px x 2) */
.child-rem { font-size: 2rem; } /* 32px (16px x 2) */
</style>

<div class="parent">
  <p class="child-em">Font-size with em</p>
  <p class="child-rem">Font-size with rem</p>
</div>
```

---

## 3️⃣ CSS Transitions vs JavaScript Animations

**Explanation:**

* **CSS Transitions** → smooth change between states, triggered by events (hover, focus).
* **JavaScript Animations** → allow complex control (timelines, pauses, conditions).

**Example:**

```html
<style>
/* CSS Transition */
.box {
  width: 100px; height: 100px; background: red;
  transition: width 1s;
}
.box:hover { width: 200px; }
</style>

<div class="box"></div>

<script>
// JavaScript Animation
const box = document.querySelector('.box');
box.addEventListener('click', () => {
  let pos = 100;
  const id = setInterval(() => {
    if (pos >= 300) clearInterval(id);
    else { pos++; box.style.width = pos + "px"; }
  }, 10);
});
</script>
```

👉 CSS is simple for small effects, JS is needed for advanced/interactive animations.

---

## 4️⃣ Mobile-first vs Desktop-first Responsive Design

**Explanation:**

* **Mobile-first** → default styles for small screens, then use `min-width` media queries for larger.
* **Desktop-first** → default styles for desktop, then use `max-width` media queries for smaller.

**Example:**

```css
/* Mobile-first */
body { font-size: 14px; }
@media (min-width: 768px) { body { font-size: 18px; } }

/* Desktop-first */
body { font-size: 18px; }
@media (max-width: 768px) { body { font-size: 14px; } }
```

---

## 5️⃣ Vendor Prefixes in CSS

**Explanation:**

* Some properties need browser-specific prefixes before being standardized.
* Examples:

  * `-webkit-` (Chrome, Safari)
  * `-moz-` (Firefox)
  * `-ms-` (IE/Edge)
* Ensure **cross-browser compatibility**.

**Example:**

```css
.box {
  -webkit-user-select: none; /* Safari/Chrome */
  -moz-user-select: none;    /* Firefox */
  -ms-user-select: none;     /* IE */
  user-select: none;         /* Standard */
}
```

---

## 6️⃣ `object-fit` & `object-position` (for images/videos)

**Explanation:**

* `object-fit` → controls how media fits its container.

  * `fill`, `contain`, `cover`, `none`, `scale-down`.
* `object-position` → sets alignment inside container.

**Example:**

```html
<img src="https://via.placeholder.com/150" 
     style="width:200px; height:150px; object-fit:cover; object-position: top;">
```

👉 Image will **cover** container, aligned to top.

---

## 7️⃣ Relative Path vs Absolute Path in CSS

**Explanation:**

* **Relative path** → based on location of CSS file.
* **Absolute path** → full URL or root-based path.

**Example:**

```css
/* Relative path (CSS file in styles/ folder) */
background-image: url("../images/bg.png");

/* Absolute path */
background-image: url("https://example.com/images/bg.png");
```

---

## 8️⃣ Clip-paths in CSS

**Explanation:**

* `clip-path` defines a visible area (rest is hidden).
* Shapes: `circle()`, `ellipse()`, `polygon()`, `inset()`.

**Example:**

```html
<img src="https://via.placeholder.com/200" 
     style="clip-path: circle(50% at 50% 50%);">
```

👉 Creates a circular cropped image.

---

## 9️⃣ `will-change` Property

**Explanation:**

* Tells the browser which properties will change → optimizes performance.
* Use sparingly (overuse wastes memory).

**Example:**

```css
.box {
  will-change: transform;
  transition: transform 0.5s;
}
.box:hover { transform: scale(1.2); }
```

👉 Browser pre-optimizes for smoother animation.

---

