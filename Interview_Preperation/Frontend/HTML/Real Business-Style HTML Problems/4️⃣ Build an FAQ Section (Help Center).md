# ✅ **Semantic, Accessible FAQ Section (HTML-Only)**

```html
<section aria-labelledby="faq-title">
  <header>
    <h1 id="faq-title">Frequently Asked Questions</h1>
  </header>

  <!-- FAQ 1 -->
  <details>
    <summary aria-expanded="false" aria-controls="faq1">
      <h2>What is your return policy?</h2>
    </summary>
    <div id="faq1">
      <p>
        We offer a 30-day return policy for all unused products in their original packaging.
      </p>
    </div>
  </details>

  <!-- FAQ 2 -->
  <details>
    <summary aria-expanded="false" aria-controls="faq2">
      <h2>How long does shipping take?</h2>
    </summary>
    <div id="faq2">
      <p>
        Shipping usually takes 3–5 business days depending on your location.
      </p>
    </div>
  </details>

  <!-- FAQ 3 -->
  <details>
    <summary aria-expanded="false" aria-controls="faq3">
      <h2>Do you offer international delivery?</h2>
    </summary>
    <div id="faq3">
      <p>
        Yes, we ship to over 40 countries with additional shipping charges.
      </p>
    </div>
  </details>

</section>
```

---

# ✅ **Explanation (Why This Is Semantic & Accessible)**

---

# **1. Semantic `<section>` + `<header>`**

```html
<section aria-labelledby="faq-title">
  <header>
    <h1 id="faq-title">Frequently Asked Questions</h1>
  </header>
</section>
```

* `<section>` groups the FAQ content semantically
* `<header>` contains the heading
* `aria-labelledby` ensures screen readers announce the section correctly
* `<h1>` is SEO-friendly for a page’s main FAQ title

---

# **2. Collapsible Answers Using `<details>` & `<summary>`**

HTML5 built-in interactive element:

```html
<details>
  <summary>...</summary>
  <p>...</p>
</details>
```

Benefits:

✔ No JavaScript needed
✔ Keyboard accessible
✔ Toggle support for screen readers
✔ SEO visible content (Google indexes inside `<details>`)

---

# **3. Proper Heading Hierarchy (SEO + Accessibility)**

Each FAQ uses:

```html
<h2>FAQ Question</h2>
```

Why `<h2>`?

* `<h1>` = main title
* `<h2>` = sub-topics (each FAQ question)
* Search engines treat each `<h2>` as a **query keyword**

**Perfect for SEO-optimized FAQs**.

---

# **4. ARIA Attributes (`aria-expanded`)**

### Why needed?

`<summary>` toggles open/closed state, but some screen readers benefit from explicit states.

### Example:

```html
<summary aria-expanded="false">
```

When the user opens the dropdown, browsers automatically update `aria-expanded` when styling + scripting is added.
Even without JS, screen readers interpret `<details open>` as expanded.

If we add `open`, it becomes expanded:

```html
<details open>
  <summary aria-expanded="true">...</summary>
</details>
```

This improves accessibility.

---

# **5. `aria-controls`**

Links summary to the answer:

```html
<summary aria-controls="faq1">
```

Screen readers know which content the summary controls.

---

# **6. Content Accessibility**

* Questions are clearly marked with semantic headings
* Answers are inside `<p>` blocks
* Screen readers detect open/closed states
* Fully navigable by keyboard:

  * Tab → Focus summary
  * Enter/Space → Toggle

---

# ⭐ Interview-Ready Summary to Say Out Loud

> I built the FAQ section using semantic HTML (`<section>`, `<header>`, `<h1>`, `<h2>`), with collapsible answers using `<details>` and `<summary>`. Each summary includes `aria-expanded` and `aria-controls` for accessibility. The content has a correct heading hierarchy, is keyboard+narrator friendly, and SEO-optimized.

---

