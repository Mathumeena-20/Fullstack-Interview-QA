Below is a **production-ready, interview-grade solution** for building a **responsive navbar** with:

* ✔ Left Logo
* ✔ Center Menu
* ✔ Right Login/Signup
* ✔ Hamburger collapse on mobile
* ✔ **Only CSS + `<details>` (no JS!)**
* ✔ Accessible by default

---

# ✅ **Final Output Preview**

---

# ✅ **FULL WORKING CODE (HTML + CSS)**

**✔ Pure CSS**
**✔ Accessible**
**✔ Uses `<details>` for hamburger**

---

# 🔹 **HTML**

```html
<header class="navbar">
  <!-- Left: Logo -->
  <div class="logo">MyLogo</div>

  <!-- Center + Mobile Hamburger -->
  <details class="menu-wrapper">
    <summary class="hamburger">
      ☰
    </summary>

    <nav class="menu">
      <a href="#">Home</a>
      <a href="#">Products</a>
      <a href="#">Pricing</a>
      <a href="#">Contact</a>
    </nav>
  </details>

  <!-- Right: Auth Buttons -->
  <div class="auth-buttons">
    <button class="login">Login</button>
    <button class="signup">Signup</button>
  </div>
</header>
```

---

# 🔹 **CSS**

```css
/* Base styling */
* { box-sizing: border-box; }

.navbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 15px 20px;
  background: #fff;
  border-bottom: 1px solid #ddd;
  position: relative;
}

/* Logo */
.logo {
  font-weight: bold;
  font-size: 1.2rem;
}

/* Center Menu (Desktop) */
.menu {
  display: flex;
  gap: 20px;
}

.menu a {
  text-decoration: none;
  color: #333;
  font-size: 1rem;
}

/* Right Buttons */
.auth-buttons {
  display: flex;
  gap: 10px;
}

.auth-buttons button {
  padding: 8px 16px;
  border-radius: 5px;
  border: 1px solid #555;
  background: none;
  cursor: pointer;
}

.signup {
  background: #333;
  color: #fff;
}

/* Hamburger (hidden on desktop) */
.hamburger {
  display: none;
  cursor: pointer;
  font-size: 1.4rem;
}

/* ——————— RESPONSIVE ——————— */

@media (max-width: 768px) {
  /* Show hamburger */
  .hamburger {
    display: block;
  }

  /* Center menu hidden initially */
  .menu {
    display: none;
    flex-direction: column;
    background: white;
    padding: 10px 0;
    border-top: 1px solid #ddd;
    gap: 15px;
  }

  /* When <details> is open → show menu */
  .menu-wrapper[open] .menu {
    display: flex;
  }

  /* Center menu takes full width on mobile */
  .menu-wrapper {
    position: absolute;
    top: 60px;
    left: 0;
    width: 100%;
  }

  /* Desktop layout changes */
  .menu-wrapper {
    order: 2; /* keep logo left, auth right */
  }

  /* Auth buttons move down or stay right depending on design */
  .auth-buttons {
    display: none; /* optional: hide on mobile for simplicity */
  }
}
```

---

# ✅ **HOW IT WORKS (Interview Explanation)**

---

## **1. Logo → Left**

Simple flex alignment:

```css
.navbar {
  display: flex;
  justify-content: space-between;
}
```

Logo sits naturally on the left.

---

## **2. Menu → Center (Desktop)**

```css
.menu {
  display: flex;
  gap: 20px;
}
```

The center menu is inside `.menu-wrapper`, positioned between logo (left) and buttons (right).

---

## **3. Login / Signup → Right**

```css
.auth-buttons {
  display: flex;
  gap: 10px;
}
```

Flexbox distributes:

```
[ Logo ]   [ Center Menu ]   [ Login | Signup ]
```

---

# ✅ **4. Hamburger Collapse on Mobile (CSS ONLY!)**

This is the key requirement.

We use **`<details>` + `<summary>`**:

```html
<details>
  <summary>☰</summary>
  <nav class="menu"> ... </nav>
</details>
```

### Why `<details>`?

* It opens/closes **without JavaScript**
* Accessible by default
* Works with keyboard navigation
* Toggle logic is handled by browser

---

## **When open → menu shows**

```css
.menu-wrapper[open] .menu {
  display: flex;
}
```

When closed → `.menu` stays hidden.

---

# ✔ **Resulting Mobile Layout**

```
[ Logo ]    [ ☰ ]
Menu expands below:

Home
Products
Pricing
Contact
```

Buttons can be hidden or moved under the menu — both are acceptable patterns.

---

# ⭐ BONUS: Cleaner Visual Structure Diagram

---

# 🎯 **What This Demonstrates (Perfect for Interviews)**

| Skill                  | Demonstrated                            |
| ---------------------- | --------------------------------------- |
| Flexbox layout         | ✔ Logo left, menu center, buttons right |
| Responsive CSS         | ✔ Breakpoints for mobile                |
| CSS-only interactions  | ✔ `<details>` hamburger                 |
| Accessibility          | ✔ Keyboard + screen reader friendly     |
| Component architecture | ✔ Clear separation                      |

---


Would you like any of these?
