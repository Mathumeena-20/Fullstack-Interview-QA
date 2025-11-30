
# ✅ **Accessible Modal (HTML Skeleton Only)**

```html
<!-- Modal Overlay -->
<div class="modal-overlay" hidden>

  <!-- Modal Container -->
  <div 
    class="modal" 
    role="dialog" 
    aria-modal="true" 
    aria-labelledby="modal-title" 
    aria-describedby="modal-desc" 
    tabindex="-1"
  >

    <!-- Modal Header -->
    <header>
      <h2 id="modal-title">Subscribe to Newsletter</h2>

      <!-- Close Button -->
      <button 
        type="button" 
        class="close-btn" 
        aria-label="Close modal"
      >
        ×
      </button>
    </header>

    <!-- Modal Content -->
    <div id="modal-desc">
      <p>Sign up to receive the latest news and updates.</p>
    </div>

    <!-- Modal Footer (optional) -->
    <footer>
      <button type="button">Confirm</button>
      <button type="button">Cancel</button>
    </footer>

  </div>
</div>
```

---

# ✅ **Explanation (Why This Is a Perfect Accessible Modal Skeleton)**

---

# **1. Modal Overlay**

```html
<div class="modal-overlay" hidden>
```

* `hidden` attribute keeps modal off-screen until activated
* Overlay traps attention and prevents background interaction

---

# **2. Modal Container with Correct ARIA Attributes**

```html
<div role="dialog" aria-modal="true">
```

### ✔ `role="dialog"`

Tells assistive technologies: *“This is a modal dialog.”*

### ✔ `aria-modal="true"`

Indicates that:

* Interaction outside the dialog is disabled
* Screen readers must stay inside modal

### ✔ `tabindex="-1"`

Allows JavaScript to focus the modal:

```js
modal.focus()
```

This is required for **focus trap**, ensuring keyboard users stay inside.

---

# **3. Title & Description with ARIA Referencing**

```html
aria-labelledby="modal-title"
aria-describedby="modal-desc"
```

### Why?

Screen readers will announce:

* Modal Title
* Modal Description
  Automatically upon opening.

### Example:

```
"Subscribe to Newsletter — Sign up to receive updates"
```

---

# **4. Header + Close Button**

```html
<button aria-label="Close modal">×</button>
```

### Why accessible?

* Close button must always be keyboard-focusable
* `aria-label` gives meaningful text
* Screen reader says:
  **“Close modal — button”**

---

# **5. Content Block**

```html
<div id="modal-desc">
  <p>...</p>
</div>
```

* Linked via `aria-describedby`
* Allows screen readers to read modal body

---

# **6. Focusable Action Buttons**

```html
<footer>
  <button>Confirm</button>
  <button>Cancel</button>
</footer>
```

Users can tab through actions inside modal.

---

# **7. Focus Management (What JS Would Do)**

While no JS is required here, **the structure supports**:

* Focusing modal on open (`tabindex="-1"`)
* Trapping focus inside modal
* Closing with ESC key
* Returning focus to original element

The interviewer will understand you know accessibility best practices.

---

# 🎯 **Interview Summary (Say This Answer):**

> I used a `<div role="dialog">` with `aria-modal="true"` for the modal container. The modal has a title referenced via `aria-labelledby` and description via `aria-describedby`, which ensures screen readers announce them correctly. I included a close button with `aria-label` and made the modal focusable using `tabindex="-1"` so JavaScript can set focus when it opens. This structure supports focus trapping, keyboard accessibility, and full ARIA compliance.

---

