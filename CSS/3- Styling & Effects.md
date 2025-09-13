## 1️⃣ Media Queries – Used in Responsive Design

**Explanation:**

* Media queries allow CSS to **adapt styles based on device characteristics** (width, height, orientation, resolution).
* Commonly used for **responsive web design**.

**Example:**

```html
<style>
body { background: lightblue; }

/* For screens smaller than 600px */
@media (max-width: 600px) {
  body { background: lightgreen; }
}
</style>
```

👉 Background changes when the viewport width is less than `600px`.

---

## 2️⃣ Difference between Transitions & Animations

**Explanation:**

* **Transitions** → Smoothly animate changes between two states (need a trigger like hover).
* **Animations** → Run continuously or in loops using `@keyframes` (don’t need a trigger).

**Example:**

```html
<style>
/* Transition */
.button {
  background: blue; color: white; padding: 10px;
  transition: background 0.5s;
}
.button:hover { background: red; }

/* Animation */
@keyframes bounce {
  0%   { transform: translateY(0); }
  50%  { transform: translateY(-20px); }
  100% { transform: translateY(0); }
}
.box {
  width: 50px; height: 50px; background: green;
  animation: bounce 1s infinite;
}
</style>

<button class="button">Hover Me</button>
<div class="box"></div>
```

---

## 3️⃣ Difference between `opacity` and `visibility: hidden`

**Explanation:**

* **opacity: 0** → element is **still in the layout**, clickable if not overridden.
* **visibility: hidden** → element is **invisible but still takes space**.
* **display: none** → element is **removed from the layout**.

**Example:**

```html
<p style="opacity:0;">Opacity 0 (invisible, space occupied, clickable)</p>
<p style="visibility:hidden;">Visibility hidden (invisible, space occupied, not clickable)</p>
<p style="display:none;">Display none (removed from layout)</p>
```

---

## 4️⃣ CSS Animation with Keyframes

**Explanation:**

* `@keyframes` defines animation steps.
* `animation: name duration iteration timing-function;`

**Example:**

```html
<style>
@keyframes colorChange {
  0%   { background: red; }
  50%  { background: yellow; }
  100% { background: green; }
}
.box {
  width:100px; height:100px;
  animation: colorChange 3s infinite alternate;
}
</style>

<div class="box"></div>
```

---

## 5️⃣ CSS Transforms (translate, rotate, scale, skew)

**Explanation:**

* **translate(x,y)** → moves element.
* **rotate(deg)** → rotates element.
* **scale(x,y)** → resizes element.
* **skew(x,y)** → skews element.

**Example:**

```html
<style>
.box1 { transform: translate(50px,20px); background:red; width:50px; height:50px; }
.box2 { transform: rotate(45deg); background:blue; width:50px; height:50px; }
.box3 { transform: scale(1.5,1.5); background:green; width:50px; height:50px; }
.box4 { transform: skew(20deg,10deg); background:purple; width:50px; height:50px; }
</style>

<div class="box1"></div>
<div class="box2"></div>
<div class="box3"></div>
<div class="box4"></div>
```

---

## 6️⃣ Box-shadow & Text-shadow

**Explanation:**

* **box-shadow** → adds shadow around elements.
* **text-shadow** → adds shadow to text.

**Syntax:**
`box-shadow: offsetX offsetY blurRadius color;`
`text-shadow: offsetX offsetY blurRadius color;`

**Example:**

```html
<div style="width:100px; height:100px; background:lightblue; 
     box-shadow: 5px 5px 10px gray;">
  Box with shadow
</div>

<p style="font-size:30px; text-shadow: 2px 2px 5px red;">
  Shadow Text
</p>
```

---

## 7️⃣ Gradient Backgrounds – Linear vs Radial

**Explanation:**

* **linear-gradient** → blends colors in a straight line (horizontal, vertical, diagonal).
* **radial-gradient** → blends colors outward from a center point.

**Example:**

```html
<div style="width:200px; height:100px; background: linear-gradient(to right, red, yellow, green);">
  Linear Gradient
</div>

<div style="width:200px; height:100px; background: radial-gradient(circle, red, yellow, green);">
  Radial Gradient
</div>
```

---

## 8️⃣ Relative Colors (HSL, RGBA) vs Absolute Colors (HEX, RGB)

**Explanation:**

* **Absolute colors** → fixed color values.

  * HEX: `#ff0000` (red)
  * RGB: `rgb(255,0,0)`
* **Relative colors** → allow **opacity/adjustments**.

  * RGBA: `rgba(255,0,0,0.5)` (red with 50% transparency)
  * HSL: `hsl(0,100%,50%)` (hue, saturation, lightness)

**Example:**

```html
<p style="color:#ff0000;">HEX Red</p>
<p style="color:rgb(255,0,0);">RGB Red</p>
<p style="color:rgba(255,0,0,0.5);">RGBA Red with 50% opacity</p>
<p style="color:hsl(0,100%,50%);">HSL Red</p>
```

---
