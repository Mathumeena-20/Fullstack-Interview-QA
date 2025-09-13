## 1️⃣ Flexbox – Properties & When to Use

**Explanation:**

* **Flexbox** (Flexible Box Layout) is used for **1D layouts** (either row or column).
* Makes alignment, spacing, and distribution of items easier.

**Main properties (on container):**

* `display: flex;` → activates flexbox.
* `flex-direction: row | column | row-reverse | column-reverse`.
* `justify-content: flex-start | center | space-between | space-around | space-evenly`.
* `align-items: flex-start | center | flex-end | stretch | baseline`.
* `flex-wrap: wrap | nowrap`.

**On items:**

* `flex: grow shrink basis`.
* `align-self: override align-items for one item`.

**Example:**

```html
<div style="display:flex; justify-content:space-around; align-items:center; height:150px; background:#eee;">
  <div style="background:red; width:50px; height:50px;"></div>
  <div style="background:blue; width:50px; height:50px;"></div>
  <div style="background:green; width:50px; height:50px;"></div>
</div>
```

👉 Use Flexbox when you need **alignment in one direction (row/column)**.

---

## 2️⃣ CSS Grid – How it’s Different from Flexbox

**Explanation:**

* **CSS Grid** is for **2D layouts** (rows + columns).
* Lets you define a full grid system.
* Difference: **Flexbox = 1D**, **Grid = 2D**.

**Main properties:**

* `display: grid;`
* `grid-template-columns: repeat(3, 1fr);`
* `grid-template-rows: auto 200px auto;`
* `gap: 10px;`

**Example:**

```html
<div style="display:grid; grid-template-columns: 1fr 1fr 1fr; gap:10px;">
  <div style="background:lightcoral;">1</div>
  <div style="background:lightblue;">2</div>
  <div style="background:lightgreen;">3</div>
  <div style="background:lightyellow;">4</div>
</div>
```

👉 Use Grid when you need **complex layouts with rows and columns**.

---

## 3️⃣ Absolute vs Relative Positioning

**Explanation:**

* **relative** → element is positioned relative to its *normal position*.
* **absolute** → element is positioned relative to the *nearest positioned ancestor*.

**Example:**

```html
<div style="position:relative; width:200px; height:200px; background:lightgray;">
  <div style="position:absolute; top:20px; left:20px; background:red; width:50px; height:50px;">
    Absolute
  </div>
</div>
```

👉 If the parent has `position: relative;`, the child `absolute` will be positioned inside it.

---

## 4️⃣ Floats in CSS & Why Rarely Used Now

**Explanation:**

* **float** → originally designed for wrapping text around images.
* Floated elements are taken out of normal document flow.
* Before Flexbox/Grid, floats were used for layouts (columns, menus).
* Now **rarely used** because Flexbox & Grid are more powerful and flexible.

**Example:**

```html
<img src="https://via.placeholder.com/80" style="float:left; margin:10px;">
<p>This text flows around the image because of float.</p>
```

---

## 5️⃣ Difference between `inline-flex` and `flex`

**Explanation:**

* `display: flex;` → makes the container a **block-level flex container** (takes full width).
* `display: inline-flex;` → makes the container an **inline-level flex container** (only as wide as content).

**Example:**

```html
<div style="display:flex; background:lightgray;">
  <div style="background:red; width:50px; height:50px;"></div>
  <div style="background:blue; width:50px; height:50px;"></div>
</div>

<div style="display:inline-flex; background:lightgray; margin-top:10px;">
  <div style="background:red; width:50px; height:50px;"></div>
  <div style="background:blue; width:50px; height:50px;"></div>
</div>
<p>Text continues right after inline-flex box.</p>
```

---

## 6️⃣ How `z-index` Works in CSS

**Explanation:**

* **z-index** → controls the **stacking order** of elements (which element appears on top).
* Only works on elements with `position: relative | absolute | fixed | sticky`.
* Higher `z-index` = on top.

**Example:**

```html
<div style="position:relative; width:100px; height:100px; background:red; z-index:1;">
  Box 1
</div>
<div style="position:relative; width:100px; height:100px; background:blue; margin-top:-50px; z-index:2;">
  Box 2 (On top of Box 1)
</div>
```

---

✅ That covers all **CSS Layout & Positioning interview questions with examples**.

Do you want me to also prepare a **Flexbox vs Grid comparison table** for quick interview recall?
