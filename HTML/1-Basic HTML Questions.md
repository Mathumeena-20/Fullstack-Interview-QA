## 1. **What is HTML and Why is it Important in Web Development?**

### ✅ Explanation:

**HTML (HyperText Markup Language)** is the fundamental language used to create and structure web pages. It allows the inclusion of text, images, links, videos, forms, and other web elements.

### ✅ Importance:

* **Provides Structure:** Defines the layout and organization of a web page.
* **Foundation for Web:** Works with CSS (for styling) and JavaScript (for interactivity).
* **Enables Accessibility:** Allows browsers and screen readers to understand content.
* **SEO:** Proper HTML structure improves search engine visibility.

### ✅ Example:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Sample Page</title>
</head>
<body>
    <h1>Welcome to My Website</h1>
    <p>This is an example of an HTML page.</p>
</body>
</html>
```

---

## 2. **Explain the Difference Between HTML4, HTML5, and XHTML.**

| Feature            | HTML4                         | XHTML                     | HTML5                         |
| ------------------ | ----------------------------- | ------------------------- | ----------------------------- |
| Syntax             | Less strict                   | Very strict (XML rules)   | Flexible                      |
| Multimedia Support | Requires plugins (like Flash) | Requires plugins          | Native audio, video, canvas   |
| Error Handling     | Browser ignores minor errors  | Strict, errors break page | Tolerant like HTML4           |
| Semantics          | Limited                       | Limited                   | Rich semantic tags introduced |
| Compatibility      | Older browsers                | XML compliant browsers    | Modern browsers               |

### ✅ Example:

#### HTML4

```html
<html>
<head><title>HTML4 Example</title></head>
<body><h1>HTML4 Page</h1></body>
</html>
```

#### XHTML

```html
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head><title>XHTML Example</title></head>
<body><h1>XHTML Page</h1></body>
</html>
```

#### HTML5

```html
<!DOCTYPE html>
<html>
<head><title>HTML5 Example</title></head>
<body><h1>HTML5 Page</h1></body>
</html>
```

---

## 3. **What are Semantic HTML Elements? Give Examples.**

### ✅ Explanation:

Semantic elements **describe the meaning** of the content inside them, making it more understandable for browsers, developers, and screen readers.

### ✅ Common Semantic Tags:

* `<header>`: Defines the top of the page or section.
* `<nav>`: Contains navigation links.
* `<section>`: Groups related content.
* `<article>`: Self-contained content.
* `<footer>`: Defines the bottom of the page or section.

### ✅ Example:

```html
<header>
    <h1>My Blog</h1>
</header>
<nav>
    <a href="/">Home</a> | <a href="/about">About</a>
</nav>
<section>
    <article>
        <h2>First Post</h2>
        <p>This is my first blog post.</p>
    </article>
</section>
<footer>
    <p>&copy; 2025 My Blog</p>
</footer>
```

---

## 4. **What is the Difference Between `<div>` and `<span>`?**

| Feature  | `<div>`                     | `<span>`              |
| -------- | --------------------------- | --------------------- |
| Type     | Block-level element         | Inline element        |
| Purpose  | Groups block content        | Groups inline content |
| Use Case | Layout sections, containers | Styling parts of text |

### ✅ Example:

```html
<div style="background-color: lightblue;">
    <p>This is inside a block-level div.</p>
</div>

<p>This is a <span style="color: red;">highlighted</span> word using span.</p>
```

---

## 5. **What are the Different Types of HTML Headings? Why are They Important?**

### ✅ Explanation:

There are **6 levels of headings**: `<h1>` to `<h6>`.

* `<h1>`: Most important (main heading)
* `<h6>`: Least important (smallest heading)

### ✅ Importance:

* Defines the content hierarchy.
* Helps **SEO** (Search Engines prioritize `<h1>`).
* Enhances **Accessibility** for screen readers.

### ✅ Example:

```html
<h1>Main Title</h1>
<h2>Section Title</h2>
<h3>Subsection Title</h3>
<h4>Smaller Heading</h4>
<h5>Minor Heading</h5>
<h6>Least Important Heading</h6>
```

---

## 6. **What is the Difference Between Block-Level and Inline Elements?**

| Feature  | Block-Level Element            | Inline Element             |
| -------- | ------------------------------ | -------------------------- |
| Display  | Starts on a new line           | Stays on the same line     |
| Width    | Occupies full width by default | Occupies only needed width |
| Examples | `<div>`, `<p>`, `<h1>`         | `<span>`, `<a>`, `<img>`   |

### ✅ Example:

```html
<div>This is a block element. It takes full width.</div>
<span>This is an inline element. It stays within the text.</span>
```

---

## 7. **Explain the Structure of an HTML Document.**

### ✅ Structure:

```html
<!DOCTYPE html> <!-- Document type declaration -->
<html> <!-- Root element -->
<head> <!-- Metadata and resources -->
    <title>Page Title</title>
</head>
<body> <!-- Visible content -->
    <h1>Welcome!</h1>
    <p>This is a sample web page.</p>
</body>
</html>
```

### ✅ Key Parts:

* `<!DOCTYPE html>`: Declares HTML5 document.
* `<html>`: Root of the HTML page.
* `<head>`: Contains metadata, title, CSS/JS links.
* `<body>`: All visible content goes here.

---

## 8. **What is the Purpose of the `<!DOCTYPE>` Declaration?**

### ✅ Explanation:

* Tells the browser **which version of HTML** to use.
* Forces browsers to use **standards-compliant rendering mode**.
* Avoids "quirks mode" which can cause inconsistent rendering.

### ✅ Example:

```html
<!DOCTYPE html>
```

This declares that the document is an **HTML5** document.

---

### 🔥 If you want, I can also help you prepare:

* ✅ Scenario-based HTML questions
* ✅ Practical mini-projects
* ✅ Front-end integration questions (HTML + CSS + JS)

Let me know if you’d like me to prepare those for you! 😊
