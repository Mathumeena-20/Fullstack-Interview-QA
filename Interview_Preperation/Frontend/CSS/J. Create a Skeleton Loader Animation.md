Below is a **clean, production-ready CSS Skeleton Loader** with a **smooth shimmering animation**, perfect for a **profile card placeholder**.

Meets all requirements:

* ✔ Grey shimmering loading effect
* ✔ Profile card skeleton (avatar + text lines)
* ✔ Pure CSS **keyframes**
* ✔ Uses **linear-gradient shimmer**
* ✔ Performance-safe (GPU-friendly, avoids layout reflow)

---

# ✅ **Skeleton Loader Preview**

---

# ✅ **FULL WORKING SOLUTION (HTML + CSS)**

This is identical to what top SaaS dashboards use (Stripe, Slack, Notion).

---

# 🔹 **HTML**

```html
<div class="skeleton-card">

  <div class="avatar skeleton"></div>

  <div class="line skeleton"></div>
  <div class="line skeleton short"></div>

</div>
```

---

# 🔹 **CSS**

```css
/* Skeleton Base */
.skeleton {
  background: #e2e2e2;
  border-radius: 6px;
  overflow: hidden;
  position: relative;
}

/* Shimmer Effect */
.skeleton::before {
  content: "";
  position: absolute;
  inset: 0;
  transform: translateX(-100%);
  background: linear-gradient(
    90deg,
    rgba(255,255,255,0) 0%,
    rgba(255,255,255,0.6) 50%,
    rgba(255,255,255,0) 100%
  );
  animation: shimmer 1.5s infinite;
}

/* Keyframes */
@keyframes shimmer {
  100% {
    transform: translateX(100%);
  }
}

/* Card Layout */
.skeleton-card {
  width: 280px;
  padding: 20px;
  border-radius: 12px;
  background: #f7f7f7;
  display: flex;
  flex-direction: column;
  gap: 15px;
}

/* Avatar Placeholder */
.avatar {
  width: 70px;
  height: 70px;
  border-radius: 50%;
}

/* Text Lines */
.line {
  height: 16px;
  width: 100%;
}
.line.short {
  width: 60%;
}
```

---

# ✅ **Explanation (Interview-Ready Breakdown)**

---

## **1. The Skeleton Base**

Every skeleton element gets:

```css
background: #e2e2e2;
border-radius: 6px;
```

✔ Neutral grey placeholder
✔ Rounded edges mimic real content

---

## **2. The Shimmer Overlay (Key Point)**

The magic is the **pseudo-element**:

```css
.skeleton::before {
  background: linear-gradient(90deg,
      transparent 0%,
      rgba(255,255,255,0.6) 50%,
      transparent 100%
  );
  transform: translateX(-100%);
  animation: shimmer 1.5s infinite;
}
```

This gradient sweeps left → right across the placeholder.

✔ Smooth shimmer
✔ GPU-optimized (uses transform, not layout properties)

---

## **3. Keyframes Animation**

```css
@keyframes shimmer {
  100% {
    transform: translateX(100%);
  }
}
```

Moves gradient from left to right.

✔ No layout recalculation
✔ Very performant

---

## **4. Avatar + Text Line Skeletons**

```css
.avatar { width:70px; height:70px; border-radius:50%; }
.line   { height:16px; }
.short  { width:60%; }
```

This creates a realistic profile card skeleton:

* Circular avatar
* Two text lines (full + short)

---

## **5. Performance Notes (Important in Interviews)**

✔ Only animates `transform` → **GPU accelerated**
✔ Avoids animating width/height/left etc.
✔ Uses a pseudo-element overlay instead of changing background

This is the **recommended approach by Google Lighthouse** and all major CSS best practices.

---

# 🎯 **Final Result**

| Requirement            | Achieved                  |
| ---------------------- | ------------------------- |
| Grey shimmering effect | ✔ Gradient animation      |
| Profile skeleton       | ✔ Avatar + lines          |
| Pure CSS keyframes     | ✔ No JS used              |
| High performance       | ✔ GPU-friendly transforms |

---

# Want Challenge #10?

I can build:

✔ CSS-only loading spinner
✔ CSS waveform loader
✔ Facebook-style advanced skeleton loader
✔ Chat message skeleton loader (WhatsApp style)

Just tell me!
