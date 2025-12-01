Below is a **production-ready, SaaS-style Pricing Table** that satisfies all requirements:

* ✔ Three equal-height pricing cards
* ✔ Middle card highlighted as *Recommended*
* ✔ Responsive stacking on mobile
* ✔ Uses **pure Flexbox**
* ✔ Clean, scalable, interview-ready code

---

# ✅ **Pricing Table Preview**

---

# ✅ **FULL WORKING SOLUTION (HTML + CSS)**

---

# 🔹 **HTML**

```html
<section class="pricing-table">

  <!-- Card 1 -->
  <div class="pricing-card">
    <h3>Basic</h3>
    <p class="price">$9 / month</p>
    <ul>
      <li>1 project</li>
      <li>Email support</li>
      <li>Community access</li>
    </ul>
    <button class="btn">Choose Plan</button>
  </div>

  <!-- Card 2 — Recommended -->
  <div class="pricing-card recommended">
    <div class="badge">Recommended</div>
    <h3>Pro</h3>
    <p class="price">$19 / month</p>
    <ul>
      <li>5 projects</li>
      <li>Priority support</li>
      <li>Advanced analytics</li>
    </ul>
    <button class="btn">Choose Plan</button>
  </div>

  <!-- Card 3 -->
  <div class="pricing-card">
    <h3>Enterprise</h3>
    <p class="price">$49 / month</p>
    <ul>
      <li>Unlimited projects</li>
      <li>Dedicated manager</li>
      <li>Custom integrations</li>
    </ul>
    <button class="btn">Choose Plan</button>
  </div>

</section>
```

---

# 🔹 **CSS**

```css
/* Container */
.pricing-table {
  display: flex;
  gap: 20px;
  padding: 20px;
  flex-wrap: wrap;        /* allows stacking on mobile */
  justify-content: center;
}

/* Cards */
.pricing-card {
  flex: 1;                /* all cards equal width */
  min-width: 250px;       /* ensures wrap nicely on small screens */
  max-width: 350px;

  display: flex;
  flex-direction: column; /* ensures equal height with flex:1 children */

  background: #fff;
  padding: 25px;
  border-radius: 12px;
  border: 1px solid #ddd;
  box-shadow: 0 4px 14px rgba(0,0,0,0.08);

  position: relative;
}

/* Recommended card */
.recommended {
  border: 2px solid #4e7cff;
  transform: scale(1.05);
  z-index: 2;
}
.recommended .badge {
  position: absolute;
  top: -12px;
  left: 50%;
  transform: translateX(-50%);
  background: #4e7cff;
  color: white;
  padding: 5px 12px;
  border-radius: 20px;
  font-size: 14px;
}

/* Price styling */
.price {
  font-size: 1.8rem;
  margin: 15px 0;
  color: #222;
  font-weight: bold;
}

/* Features list */
.pricing-card ul {
  margin-bottom: 20px;
  flex: 1;                /* pushes button to bottom, making equal height */
}
.pricing-card ul li {
  margin-bottom: 10px;
}

/* Button */
.btn {
  padding: 12px 20px;
  border: none;
  width: 100%;
  background: #4e7cff;
  color: white;
  border-radius: 8px;
  cursor: pointer;
  font-size: 1rem;
}

.btn:hover {
  background: #3c66d1;
}

/* Responsive: stack on mobile */
@media (max-width: 768px) {
  .pricing-card {
    max-width: 100%;
    transform: none;
  }
}
```

---

# ✅ **INTERVIEW-READY EXPLANATION**

---

# **1. Equal Height Cards Using Flexbox**

Inside each `.pricing-card`, we use:

```css
flex-direction: column;
```

And then:

```css
ul { flex: 1; }
```

This pushes the button to the bottom, ensuring **all cards become equal height**, no matter the text length.

✔ Classic SaaS layout trick
✔ No fixed heights

---

# **2. Highlighting the Recommended Card**

```css
.recommended {
  transform: scale(1.05);
  border: 2px solid #4e7cff;
}
```

✔ Slight scale makes the middle card pop
✔ Border color emphasizes it visually
✔ Badge placed above using absolute positioning

---

# **3. Responsive Stacking (Mobile)**

Using flex-wrap + min-width:

```css
.flex-wrap: wrap;
min-width: 250px;
```

Cards automatically drop to fewer columns as the screen shrinks.

And a final breakpoint:

```css
@media (max-width: 768px) {
  .pricing-card { max-width: 100%; }
}
```

✔ Cards stack vertically
✔ No horizontal scroll
✔ Mobile-first friendly

---

# **4. Centered Layout with Auto-Sizing Columns**

```css
.pricing-table {
  display: flex;
  justify-content: center;
}
```

Combined with:

```css
flex: 1;
max-width: 350px;
```

✔ Perfectly spaced columns
✔ Scales from 1 → 2 → 3 columns smoothly

---

# 🎯 **Final Result**

| Requirement                 | Achieved                               |
| --------------------------- | -------------------------------------- |
| Three equal-height cards    | ✔ `flex-direction: column` + `flex: 1` |
| Recommended card emphasized | ✔ Scale + border + badge               |
| Responsive stacking         | ✔ `flex-wrap: wrap` + media query      |
| Real SaaS component style   | ✔ Cards, buttons, shadows              |

---

