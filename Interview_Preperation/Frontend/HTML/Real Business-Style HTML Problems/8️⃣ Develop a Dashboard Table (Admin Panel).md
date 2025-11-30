# ✅ **HTML: Admin User List Table (Semantic + Accessible)**

```html
<main>

  <h1>User Management</h1>

  <!-- User List Table -->
  <table aria-label="User list" role="table">

    <!-- Table Header -->
    <thead>
      <tr>

        <th scope="col">Profile</th>

        <th scope="col">
          Name
          <!-- Sort icon placeholder -->
          <span aria-hidden="true">⇅</span>
        </th>

        <th scope="col">
          Email
          <span aria-hidden="true">⇅</span>
        </th>

        <th scope="col">Role</th>

        <th scope="col">
          Joined
          <span aria-hidden="true">⇅</span>
        </th>

      </tr>
    </thead>

    <!-- Table Body -->
    <tbody>

      <tr>
        <td>
          <img src="user1.jpg" alt="John Doe profile picture" width="40" height="40">
        </td>
        <td>John Doe</td>
        <td>john@example.com</td>
        <td>Admin</td>
        <td>2023-04-12</td>
      </tr>

      <tr>
        <td>
          <img src="user2.jpg" alt="Sarah Wilson profile picture" width="40" height="40">
        </td>
        <td>Sarah Wilson</td>
        <td>sarah@example.com</td>
        <td>Editor</td>
        <td>2022-11-04</td>
      </tr>

      <tr>
        <td>
          <img src="user3.jpg" alt="Michael Chen profile picture" width="40" height="40">
        </td>
        <td>Michael Chen</td>
        <td>michael@example.com</td>
        <td>Viewer</td>
        <td>2023-01-30</td>
      </tr>

    </tbody>

    <!-- Table Footer for Pagination -->
    <tfoot>
      <tr>
        <td colspan="5" role="navigation" aria-label="Pagination">
          <nav>
            <ul>
              <li><a href="#">Previous</a></li>
              <li><a href="#" aria-current="page">1</a></li>
              <li><a href="#">2</a></li>
              <li><a href="#">3</a></li>
              <li><a href="#">Next</a></li>
            </ul>
          </nav>
        </td>
      </tr>
    </tfoot>

  </table>

</main>
```

---

# ✅ **Explanation (Why This Structure Is Perfect for Admin Dashboards)**

---

# **1. Accessible Table Structure**

We use:

* `<table>`
* `<thead>`
* `<tbody>`
* `<tfoot>`
* `<th scope="col">`

These help:
✔ Screen readers
✔ Sorting
✔ Better indexing
✔ Business dashboards

---

# **2. Profile Image Thumbnail**

```html
<img src="user1.jpg" alt="John Doe profile picture" width="40" height="40">
```

Why this is correct:

* Uses meaningful `alt` text
* Sets explicit width/height (prevents layout shift)
* Real UI pattern in admin dashboards

---

# **3. Sort Icons (No JS, Accessible)**

```html
<span aria-hidden="true">⇅</span>
```

* Decorative only → hidden from screen readers
* Looks like a sort icon, but no JS needed
* Admin dashboards typically show sort hints visually

---

# **4. Pagination Using `<tfoot>`**

```html
<tfoot>
  <tr>
    <td colspan="5">
      <nav>
        <ul>
```

Why this is excellent:

* Pagination belongs semantically at the end of data
* `<tfoot>` is placed before `<tbody>` in HTML but rendered at bottom
* `<nav>` improves accessibility
* `aria-current="page"` marks the active page
* Proper HTML-only pagination placeholder

---

# **5. Role Management Columns**

Columns:

* Profile
* Name
* Email
* Role
* Joined date

This mimics **real admin dashboards**.

---

# **6. ARIA Labeling for Accessibility**

```html
<table aria-label="User list">
```

This ensures:

* Screen readers announce the table as “User list”
* Matching WCAG accessibility requirements

---

# **7. SEO-Friendly Headings**

```html
<h1>User Management</h1>
```

* Great for both SEO and admin UX

---

# 🎯 **Interview-Safe Spoken Summary**

> I created an accessible admin-style user list table using `<thead>`, `<tbody>`, and `<tfoot>`. Each column header uses `<th scope="col">` for accessibility. I added profile thumbnail images with descriptive alt text. Sorting icons are decorative and marked with `aria-hidden="true"`. Pagination is placed in the `<tfoot>` with a proper `<nav>` and `aria-current` for active indicators. This structure follows real admin dashboard patterns and is screen-reader-friendly.

---
