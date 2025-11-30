# ✅ **1. Difference Between Block-level, Inline, and Inline-block Elements**

## **Block-level Elements**

* Take **full width** available.
* Always start on a **new line**.
* You can set **width, height, margin, padding**.
* Examples:
  `<div>`, `<section>`, `<p>`, `<h1>`, `<ul>`

### Example:

```html
<div style="background: lightblue;">Block 1</div>
<div style="background: lightgreen;">Block 2</div>
```

---

## **Inline Elements**

* Do **not** start on a new line.
* Take **only the width of their content**.
* Cannot set **width** or **height**.
* Examples:
  `<span>`, `<a>`, `<strong>`, `<em>`

### Example:

```html
<span style="background: yellow;">Inline 1</span>
<span style="background: orange;">Inline 2</span>
```

---

## **Inline-block Elements**

* Behave like **inline** (stay in same line)
* But allow **width**, **height**, **margin**, **padding** like a block element.
* Example:
  `<button>`, `<input>`, or applying `display: inline-block;`

### Example:

```html
<div style="display:inline-block; width:100px; background: pink;">Box 1</div>
<div style="display:inline-block; width:100px; background: purple;">Box 2</div>
```

---

# ✅ **2. What Are Semantic HTML Tags? Why Are They Important?**

## **Semantic HTML tags**

These are tags that **describe meaning** and **structure** rather than appearance.

Examples:

* `<header>`
* `<footer>`
* `<nav>`
* `<article>`
* `<section>`
* `<main>`
* `<aside>`

## **Why Important?**

1. **Improves SEO**
   Search engines understand the structure better.

2. **Accessibility**
   Screen readers identify the purpose of content.

3. **Maintainability**
   Code becomes more readable and organized.

4. **Browser Optimization**
   Browsers can better interpret document structure.

### Example (Semantic vs Non-semantic)

❌ Non-semantic:

```html
<div id="header"></div>
<div id="content"></div>
<div id="footer"></div>
```

✔ Semantic:

```html
<header></header>
<main></main>
<footer></footer>
```

---

# ✅ **3. Difference Between `<div>` and `<section>`**

| Feature       | `<div>`           | `<section>`                      |
| ------------- | ----------------- | -------------------------------- |
| Meaning       | No meaning        | Has semantic meaning             |
| Purpose       | General container | Group related content            |
| SEO           | No SEO value      | Helps SEO                        |
| Accessibility | Not useful        | Screen readers identify sections |

### Easy Explanation:

* **Use `<div>` when the element has no specific meaning.**
* **Use `<section>` when content represents a standalone section with a heading.**

### Example:

```html
<section>
  <h2>About Our Company</h2>
  <p>We build modern web apps.</p>
</section>

<div class="card">
  <p>This is just a styling container.</p>
</div>
```

---

# ✅ **4. Purpose of `<header>`, `<article>`, and `<aside>` Tags**

## **<header>**

Used for introductory content or navigation.

Contains:

* Logo
* Page title
* Navigation menu

Example:

```html
<header>
  <h1>My Blog</h1>
  <nav>...</nav>
</header>
```

---

## **<article>**

Represents an **independent piece of content** that can stand alone.

Examples:

* Blog post
* News article
* Forum post

Example:

```html
<article>
  <h2>How to Learn HTML</h2>
  <p>HTML is the backbone of the web...</p>
</article>
```

---

## **<aside>**

Used for **side content** that supports the main content.

Examples:

* Ads
* Sidebars
* Related posts

Example:

```html
<aside>
  <h3>Related Articles</h3>
</aside>
```

---

# ✅ **5. What is the DOM? How Does the Browser Construct It From HTML?**

## **DOM (Document Object Model)**

The DOM is a **tree representation** of the entire HTML document.
It allows JavaScript to **read and manipulate** web pages.

Example DOM tree:

```
html
│
├── head
└── body
      ├── header
      ├── main
      └── footer
```

---

## **How the Browser Constructs the DOM? (Step-by-step)**

### 1. **HTML parsing begins**

The browser reads the HTML file line-by-line.

### 2. **Browser tokenizes HTML**

Converts HTML into small units (tokens).

### 3. **Tokens → Nodes**

Each token becomes a node (element, text, comment).

### 4. **Nodes form a tree**

These nodes get combined into the **DOM Tree**.

### 5. CSS + JS applied afterwards**

CSSOM + DOM → Render Tree
JavaScript can modify DOM using the tree.

---

### Simple Example:

HTML:

```html
<body>
  <h1>Hello</h1>
  <p>Welcome!</p>
</body>
```

DOM Tree:

```
body
├── h1
│    └── "Hello"
└── p
     └── "Welcome!"
```


