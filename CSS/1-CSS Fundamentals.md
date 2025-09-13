## 1️⃣ Difference between `relative`, `absolute`, `fixed`, and `sticky` positioning

**Explanation:**

* **relative** → Positions the element *relative to its normal position*.
* **absolute** → Positions the element *relative to its nearest positioned ancestor* (not the viewport unless no ancestor is positioned).
* **fixed** → Positions the element relative to the **viewport** (stays fixed when scrolling).
* **sticky** → Behaves like **relative**, but “sticks” to a position when scrolling past it.

**Example:**

```html
<div style="position: relative; top: 20px;">Relative Box</div>
<div style="position: absolute; top: 50px; left: 100px;">Absolute Box</div>
<div style="position: fixed; bottom: 10px; right: 10px;">Fixed Box</div>
<div style="position: sticky; top: 0; background: yellow;">Sticky Header</div>
```

---

## 2️⃣ Inline, Inline-block, and Block-level elements

**Explanation:**

* **inline** → Takes only as much width as needed, does not start a new line. (e.g., `<span>`, `<a>`)
* **block** → Takes full width available, always starts on a new line. (e.g., `<div>`, `<p>`)
* **inline-block** → Behaves like inline, but allows setting width/height.

**Example:**

```html
<span style="background: lightblue;">Inline</span>
<span style="background: lightgreen;">Elements</span>

<div style="background: pink;">Block Element 1</div>
<div style="background: lightyellow;">Block Element 2</div>

<span style="display:inline-block; width:100px; height:50px; background:orange;">
Inline-block
</span>
```

---

## 3️⃣ Relative vs Absolute Units

**Explanation:**

* **Absolute units** → Do not scale with screen size (px, pt, cm, in).
* **Relative units** → Adjust based on parent or viewport (em, rem, %, vw, vh).

**Example:**

```html
<p style="font-size: 16px;">16px (absolute)</p>
<p style="font-size: 2em;">2em (relative to parent font-size)</p>
<p style="font-size: 2rem;">2rem (relative to root font-size)</p>
<p style="width: 50%;">50% (relative to parent width)</p>
<p style="width: 50vw;">50vw (relative to viewport width)</p>
<p style="height: 50vh;">50vh (relative to viewport height)</p>
```

---

## 4️⃣ Pseudo-classes vs Pseudo-elements

**Explanation:**

* **Pseudo-class** → Defines a *special state* of an element (e.g., `:hover`, `:focus`).
* **Pseudo-element** → Selects *part of an element* (e.g., `::before`, `::after`).

**Example:**

```html
<style>
a:hover { color: red; }              /* Pseudo-class */
p::first-line { font-weight: bold; } /* Pseudo-element */
p::after { content: " ✅"; }
</style>

<a href="#">Hover over me</a>
<p>This is a paragraph with styled first line.</p>
```

---

## 5️⃣ Difference between `id`, `class`, and `attribute` selectors

**Explanation:**

* **id selector (`#id`)** → Unique to a single element.
* **class selector (`.class`)** → Can be applied to multiple elements.
* **attribute selector (`[attr=value]`)** → Selects elements based on attributes.

**Example:**

```html
<style>
#unique { color: red; }         /* ID selector */
.common { color: green; }       /* Class selector */
input[type="text"] { border: 1px solid blue; } /* Attribute selector */
</style>

<p id="unique">This is unique</p>
<p class="common">This is common</p>
<input type="text" placeholder="Text field">
<input type="password" placeholder="Password field">
```

---

## 6️⃣ Inline CSS vs Internal CSS vs External CSS

**Explanation:**

* **Inline CSS** → Inside HTML element using `style=""`. (highest priority)
* **Internal CSS** → Inside `<style>` in the same HTML file.
* **External CSS** → In a separate `.css` file linked with `<link>`.

**Example:**

```html
<!-- Inline -->
<p style="color: red;">Inline CSS</p>

<!-- Internal -->
<style>
p { color: blue; }
</style>
<p>Internal CSS</p>

<!-- External -->
<link rel="stylesheet" href="styles.css">
<p>External CSS</p>
```

---

## 7️⃣ Specificity Hierarchy in CSS

**Order of priority:**

1. Inline styles → `style=""`
2. ID selectors → `#id`
3. Class, attribute, pseudo-class selectors → `.class, [attr], :hover`
4. Element selectors → `div, p, h1`
5. Universal selector → `*`

**Example:**

```html
<style>
p { color: black; }          /* Least priority */
p.common { color: green; }   /* Higher */
#unique { color: blue; }     /* Even higher */
</style>

<p id="unique" class="common" style="color:red;">
This will be RED (inline has highest priority)
</p>
```

---

## 8️⃣ CSS Combinators (`>`, `+`, `~`, space)

**Explanation:**

* **descendant (space)** → Selects all descendants.
* **child (>)** → Selects direct children only.
* **adjacent sibling (+)** → Selects next sibling only.
* **general sibling (\~)** → Selects all siblings after.

**Example:**

```html
<style>
div p { color: blue; }      /* Descendant */
div > p { color: green; }   /* Direct child */
h1 + p { color: red; }      /* Adjacent sibling */
h1 ~ p { font-style: italic; } /* All siblings */
</style>

<div>
  <p>Direct child of div</p>
  <span><p>Descendant inside span</p></span>
</div>
<h1>Heading</h1>
<p>Adjacent paragraph</p>
<p>Another sibling paragraph</p>
```

---

## 9️⃣ Inheritance in CSS

**Explanation:**

* Some CSS properties are **inherited** (like `color`, `font-family`).
* Others (like `margin`, `padding`, `border`) are **not inherited**.

**Example:**

```html
<style>
div { color: blue; font-family: Arial; }
</style>

<div>
  <p>This text is blue (inherited)</p>
  <span>Even span inherits blue</span>
</div>
```



Do you want me to also prepare these in a **short cheat-sheet format** (just differences and one-liner examples) for quick **last-minute interview revision**?
