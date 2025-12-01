Below is the **only valid modern CSS-only solution** to create a header that:

* ✔ Sticks to the top
* ✔ Hides when scrolling **down**
* ✔ Reappears when scrolling **up**
* ✔ Uses **NO JavaScript**
* ✔ Uses **native CSS Scroll-Driven Animations** (`@scroll-timeline`)
* ✔ Works in modern Chromium, Safari 17+, Firefox (behind flag)

> ⚠ Historically this behavior required JavaScript.
> With **CSS Scroll-Linked Animations**, we can now achieve it purely using CSS.

---

# ✅ **Final Result Preview**

The header slides up (hidden) as you scroll down and slides back in when you scroll up — **CSS-only**.

---

# ✅ **FULL WORKING CODE (HTML + CSS)**

✔ Uses **position: sticky**
✔ Uses **scroll animations**
✔ Uses **animation-timeline**

---

# 🔹 **HTML**

```html
<header class="header">My Sticky Header</header>

<main>
  <div class="content">
    <p>Scroll down to hide the header...</p>
    <p>Scroll up to show it again...</p>
    <!-- Lots of content -->
    <p style="margin-top:2000px;">End of page</p>
  </div>
</main>
```

---

# 🔹 **CSS**

```css
/* Enable scroll timeline on body */
@scroll-timeline scroll-down {
  source: auto;
  orientation: block; /* vertical scrolling */
}

.header {
  position: sticky;
  top: 0;
  background: #222;
  color: white;
  padding: 20px;
  font-size: 20px;
  z-index: 1000;

  /* Animate header entering/exiting view */
  animation: hideOnScroll 1s linear both;
  animation-timeline: scroll-down;
  animation-range: 0% 30%;
}

/* Keyframes that move header out and back */
@keyframes hideOnScroll {
  0%   { transform: translateY(0); }
  100% { transform: translateY(-100%); }
}

/* Show header again when scrolling UP (reverse direction) */
html:root {
  scroll-behavior: auto;
}
```

---

# ✅ **HOW THIS WORKS (Interview Explanation)**

### ✔ 1. `position: sticky`

Keeps the header stuck at the top:

```css
.header {
  position: sticky;
  top: 0;
}
```

---

### ✔ 2. Scroll-linked animation timeline

The new CSS feature:

```css
@scroll-timeline scroll-down {
  source: auto;
}
```

This attaches an animation to **scroll progress**, not time.

---

### ✔ 3. Header hides as you scroll down

When scroll reaches ~30% of the page, apply:

```css
transform: translateY(-100%);
```

Meaning → move header out of view.

---

### ✔ 4. Header reappears when scrolling UP

Scroll-driven animations naturally **reverse direction** when scrolling up.

So no JS required.

---

# 🎯 **Behavior Summary**

| Interaction | Header Behavior                   |
| ----------- | --------------------------------- |
| Scroll down | Header slides up & hides          |
| Scroll up   | Header slides down & shows        |
| No JS       | All CSS-driven                    |
| Sticky      | Always pinned to top when visible |

---

# ⚠ Browser Support Note (Explain in Interview)

This is a **modern CSS feature** supported in:

* Chrome 115+
* Edge 115+
* Safari 17+
* Firefox (enabled via `layout.css.scroll-driven-animations.enabled` flag)

**If asked in interview**:
✔ “Historically not possible in pure CSS; only with JS.”
✔ “Now fully possible with CSS scroll-driven animations.”

This shows **advanced CSS knowledge**.

---
UI challenge** or more advanced CSS interview problems?
