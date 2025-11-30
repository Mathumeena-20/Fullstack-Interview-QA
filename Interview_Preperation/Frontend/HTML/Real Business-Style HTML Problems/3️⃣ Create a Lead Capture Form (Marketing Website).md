# ✅ **HTML Solution (Accessible + Validated + No JS)**

```html
<form action="/subscribe" method="POST" aria-labelledby="form-title" novalidate>

  <h2 id="form-title">Newsletter Subscription</h2>

  <!-- Name -->
  <div>
    <label for="name">Full Name</label>
    <input 
      id="name" 
      name="name" 
      type="text" 
      required 
      aria-required="true"
      aria-describedby="name-error"
    >
    <span id="name-error" class="error" role="alert">
      Please enter your name.
    </span>
  </div>

  <!-- Email -->
  <div>
    <label for="email">Email Address</label>
    <input 
      id="email" 
      name="email" 
      type="email" 
      required 
      aria-required="true"
      aria-describedby="email-error"
    >
    <span id="email-error" class="error" role="alert">
      Enter a valid email address.
    </span>
  </div>

  <!-- Phone -->
  <div>
    <label for="phone">Phone Number</label>
    <input 
      id="phone" 
      name="phone" 
      type="tel" 
      pattern="[0-9]{10}" 
      required 
      aria-required="true"
      aria-describedby="phone-error"
    >
    <span id="phone-error" class="error" role="alert">
      Enter a 10-digit phone number.
    </span>
  </div>

  <!-- Subscribe Checkbox -->
  <div>
    <input 
      id="subscribe" 
      name="subscribe" 
      type="checkbox"
      aria-labelledby="subscribe-label"
    >
    <label id="subscribe-label" for="subscribe">Subscribe for Updates</label>
  </div>

  <!-- Submit Button -->
  <button type="submit">Submit</button>

</form>
```

---

# ✅ **Why This Form Is Perfect (Explanation)**

---

# **1. Semantic + Accessible Structure**

* `<form>` is labeled using `aria-labelledby`
* `<label>` tags connect to inputs with `for` & `id`
* Screen readers announce: *“Full Name, required, edit text”*

---

# **2. Required Fields**

Each required field includes:

```html
required aria-required="true"
```

* `required` → HTML validation
* `aria-required="true"` → screen reader validation

---

# **3. Built-in HTML5 Validation**

* Name → required
* Email → `type="email"`
* Phone → `pattern="[0-9]{10}"`

Browser automatically blocks the form until inputs are valid.

---

# **4. Error Messages Without JavaScript**

```html
<span id="name-error" class="error" role="alert">Please enter your name.</span>
```

* `role="alert"` ensures screen readers speak the error
* `aria-describedby` links the input to error message
* These messages appear when validation fails (via CSS later)

Even with **no JavaScript**, HTML5 validation + ARIA provide accessibility.

---

# **5. Patterns for Phone Numbers**

```html
pattern="[0-9]{10}"
```

Ensures a 10-digit number.

---

# **6. Checkbox With Accessible Label**

```html
<input id="subscribe" type="checkbox">
<label for="subscribe">Subscribe for Updates</label>
```

Correct pairing for screen-reader compatibility.

---

# **7. `novalidate` on form (optional)**

```html
<form novalidate>
```

* Prevents browser bubble tooltips
* Allows custom messages inside `<span>` to be used
* Required by many interview tasks

---

# 🎯 Interview Summary (Use This When Asked)

> This form uses semantic labels, ARIA attributes, required fields, type-based HTML5 validations, and accessible error messages without JavaScript. Screen readers can read all labels and error messages, and the structure follows form best practices.

---
