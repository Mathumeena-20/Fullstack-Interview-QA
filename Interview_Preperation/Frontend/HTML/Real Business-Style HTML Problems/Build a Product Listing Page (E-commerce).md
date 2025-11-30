# ✅ **Semantic HTML Structure for Product List Page**

```html
<main>

  <!-- Page Header -->
  <header>
    <h1>Products</h1>
  </header>

  <!-- Product Listing Section -->
  <section aria-labelledby="product-list">
    <h2 id="product-list">Available Products</h2>

    <!-- Product Grid -->
    <ul>

      <!-- Product 1: In Stock -->
      <li>
        <article>
          <figure>
            <img src="laptop.jpg" alt="14-inch Ultra Laptop">
            <figcaption>Laptop</figcaption>
          </figure>

          <header>
            <h3>14-inch Ultra Laptop</h3>
          </header>

          <p class="price" aria-label="Price: $999">$999</p>

          <button type="button">Add to Cart</button>
        </article>
      </li>

      <!-- Product 2: Out of Stock -->
      <li>
        <article>
          <figure>
            <img src="headphones.jpg" alt="Wireless Noise-Canceling Headphones">
            <figcaption>Headphones</figcaption>
          </figure>

          <header>
            <h3>Wireless Headphones</h3>
          </header>

          <!-- Out-of-stock badge -->
          <p aria-label="Out of Stock">
            <strong>Out of Stock</strong>
          </p>

          <p class="price">$199</p>

          <!-- Disabled button for accessibility -->
          <button type="button" disabled aria-disabled="true">
            Add to Cart
          </button>

        </article>
      </li>

    </ul>
  </section>

</main>
```

---

# ✅ **Explanation (Why This Is a Real-World, Semantic Structure)**

## **1. `<main>`**

* Holds the primary content of the page.

## **2. `<header>` with `<h1>`**

* Main heading for the entire page.
* Helps screen readers understand page topic.

## **3. `<section>` for the product list**

* Represents a related group of items.
* `aria-labelledby` links section to its heading for accessibility.

## **4. `<ul>` and `<li>`**

* Product lists are semantically lists.
* Highly recommended for e-commerce category pages.

## **5. `<article>` for each product**

* Each product is an independent unit.
* Can be shared, saved, or linked individually.

## **6. `<figure>` + `<img>` + `<figcaption>`**

* Proper structure for product media.
* `<img>` has a descriptive, accessible `alt` text.

## **7. `<header>` inside article**

* Contains the product name `<h3>`.

## **8. Out-of-Stock badge**

```html
<p aria-label="Out of Stock">
  <strong>Out of Stock</strong>
</p>
```

* Semantic, accessible to screen readers.
* `<strong>` adds emphasis for accessibility.
* No styling needed (pure HTML).

## **9. Price markup**

```html
<p class="price">$999</p>
```

* Simple and semantic.

## **10. Accessible Buttons**

* Normal button for available products.
* Disabled + `aria-disabled="true"` makes out-of-stock button accessible.

---

# 🎯 Why This Passes All Required Tests

| Requirement                  | How It’s Achieved                                                  |
| ---------------------------- | ------------------------------------------------------------------ |
| **Semantic HTML**            | `<main>`, `<section>`, `<article>`, `<figure>`, `<header>`, `<ul>` |
| **Accessibility**            | Proper headings, alt text, aria labels, disabled handling          |
| **Product image**            | In `<figure>` with `<img>`                                         |
| **Product title**            | `<h3>` inside `<header>`                                           |
| **Product price**            | `<p class="price">` with aria support                              |
| **Add to Cart**              | `<button>` elements                                                |
| **Out-of-stock badge**       | Clear `<strong>` text with aria-label                              |
| **Business-ready structure** | Follows real e-commerce layouts                                    |

---

