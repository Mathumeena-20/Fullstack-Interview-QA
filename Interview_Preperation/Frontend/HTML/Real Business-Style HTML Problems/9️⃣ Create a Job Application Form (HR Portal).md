
# ✅ **HTML: Job Application Form (Semantic + Accessible)**

```html
<form action="/apply" method="POST" enctype="multipart/form-data" aria-labelledby="job-form-title">

  <h1 id="job-form-title">Job Application Form</h1>

  <!-- Name -->
  <div>
    <label for="name">Full Name</label>
    <input id="name" name="name" type="text" required>
  </div>

  <!-- Email -->
  <div>
    <label for="email">Email Address</label>
    <input id="email" name="email" type="email" required>
  </div>

  <!-- Phone -->
  <div>
    <label for="phone">Phone Number</label>
    <input id="phone" name="phone" type="tel" pattern="[0-9]{10}" required>
  </div>

  <!-- Resume Upload -->
  <div>
    <label for="resume">Upload Resume (PDF only)</label>
    <input id="resume" name="resume" type="file" accept=".pdf" required>
  </div>

  <!-- Role Applying For -->
  <div>
    <label for="role">Role Applying For</label>
    <select id="role" name="role" required>
      <option value="">Select a role...</option>
      <option value="frontend-developer">Frontend Developer</option>
      <option value="backend-developer">Backend Developer</option>
      <option value="fullstack-developer">Fullstack Developer</option>
      <option value="qa-engineer">QA Engineer</option>
    </select>
  </div>

  <!-- Preferred Location -->
  <div>
    <label for="location">Preferred Location</label>
    <select id="location" name="location" required>
      <option value="">Choose a location...</option>
      <option value="chennai">Chennai</option>
      <option value="bangalore">Bangalore</option>
      <option value="hyderabad">Hyderabad</option>
      <option value="remote">Remote</option>
    </select>
  </div>

  <!-- Experience -->
  <div>
    <label for="experience">Experience (Years)</label>
    <input 
      id="experience" 
      name="experience" 
      type="number" 
      min="0" 
      max="40"
      required>
  </div>

  <!-- Submit -->
  <button type="submit">Submit Application</button>

</form>
```

---

# ✅ **Explanation (Why This Passes All Requirements)**

---

# **1. File Upload Enabled**

```html
<input type="file" accept=".pdf">
```

### ✔ Allows only PDF files

### ✔ Required field

And form includes:

```html
enctype="multipart/form-data"
```

required for file uploads in real backend systems.

---

# **2. Proper Input Types**

* Name → `type="text"`
* Email → `type="email"`
* Phone → `type="tel"` with:

```html
pattern="[0-9]{10}"
```

* Experience → `type="number"`

Why?

✔ HTML5 validates automatically
✔ Mobile devices show the correct keyboard
✔ Prevents invalid input

---

# **3. Dropdown for Role**

```html
<select id="role" required>
  <option value="">Select a role...</option>
```

### ✔ Good UX

### ✔ Required

---

# **4. Preferred Location Dropdown**

```html
<select id="location" required>
```

HR portals frequently use location dropdowns.

---

# **5. Experience Input**

```html
<input type="number" min="0" max="40">
```

This prevents:

* Negative values
* Unrealistic experience values

---

# **6. Required Attributes for Validation**

Every essential field has:

```html
required
```

Ensures the form cannot be submitted empty.

---

# **7. Labels Connected with Inputs**

Each input uses:

```html
<label for="id">
<input id="id">
```

This is important for:
✔ Accessibility
✔ Mobile form usability
✔ Screen readers

---

# **8. Perfect Real-World HR Use Case**

This form matches what companies use for:

* Job portals
* Recruitment systems
* Done using only HTML
* Easily integrates into backend

---

# 🎯 **Interview Summary (What You Should Say):**

> I created a semantic, accessible job application form with proper labels, HTML5 input types, and validations. File uploads use `enctype="multipart/form-data"` and restrict resumes to PDFs. I used dropdowns for role and location, and a number input with min/max for experience. All fields are labeled and required, which aligns with real-world HR workflows.

---
