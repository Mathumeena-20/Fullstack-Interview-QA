# ✅ **Final Output Preview**

---

# ✅ **FULL WORKING SOLUTION (HTML + CSS)**

---

# 🔹 **HTML**

```html
<p class="truncate-2">
  Lorem ipsum dolor sit amet, consectetur adipiscing elit. 
  Integer non nibh nec lorem pellentesque aliquet vitae eget arcu. 
  Suspendisse potenti.
</p>
```

---

# 🔹 **CSS**

```css
.truncate-2 {
  display: -webkit-box;           /* required for WebKit browsers */
  -webkit-line-clamp: 2;          /* number of visible lines */
  -webkit-box-orient: vertical;   /* vertical layout */
  
  overflow: hidden;
  text-overflow: ellipsis;
}
```

---

# 🎯 **INTERVIEW-READY EXPLANATION**

---

## **1. Multi-line truncation is not built into CSS normally**

Browsers only natively support `text-overflow: ellipsis` for **single-line** text.

For multiple lines we use the “line clamp hack”:

```
display: -webkit-box
-webkit-line-clamp: 2
-webkit-box-orient: vertical
```

This technique is now supported by **all major modern browsers**.

---

## **2. Why `display: -webkit-box`?**

It enables the browser to treat the paragraph as a **block container with flexible lines**, which makes line clamping possible.

---

## **3. Why `-webkit-line-clamp: 2`?**

Directs the browser to:

* Render only **2 lines**
* Hide everything after that
* Apply ellipsis automatically

You can change the number:

```css
-webkit-line-clamp: 3;  /* for 3 lines */
```

---

## **4. Why `overflow: hidden` and `text-overflow: ellipsis`?**

These ensure:

* Overflow is hidden
* Ellipsis (`…`) appears
* No scrollbars

---

## **5. Browser Support**

As of 2023+, supported in:

| Browser         | Supported? |
| --------------- | ---------- |
| Chrome          | ✔          |
| Safari          | ✔          |
| Firefox         | ✔          |
| Edge            | ✔          |
| Mobile browsers | ✔          |

Multi-line ellipsis is now a **standard technique** used across SaaS dashboards, news apps, blogs, product cards, etc.

---

# ⭐ Optional Enhancement: Add Fade-Out Gradient

(Also CSS-only)

```css
.truncate-fade {
  position: relative;
  max-height: 3.2em;  /* roughly 2 lines */
  overflow: hidden;
}

.truncate-fade::after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 1em;
  background: linear-gradient(to bottom, transparent, white);
}
```

✔ Smooth fade
✔ Used in Instagram, Medium, LinkedIn

---

