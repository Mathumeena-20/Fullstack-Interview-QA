# 🚀 **ReactJS Interview Questions (2+ Years Experience)**

## 🔹 **Core React Fundamentals**

1. **What are the main features of React?**
2. **Explain Virtual DOM and how React uses it.**
3. **What is JSX and why do we use it?**
4. **What are React components? Difference between class and functional components?**
5. **What are props vs state? When do you use each?**
6. **Why is state immutable in React?**
7. **What is the significance of keys in React lists?**

---

# 🔹 **Hooks (Very important for 2+ years)**

### **useState**

1. How does `useState` work internally?
2. Why does React batch state updates?
3. What happens if you update a state based on previous state incorrectly?

### **useEffect**

4. Difference between **useEffect**, **useLayoutEffect**, and **useInsertionEffect**.
5. What is the dependency array? What happens if you leave it empty?
6. How to avoid infinite renders in `useEffect`?
7. How do you clean up side effects?

### **Other Hooks**

8. What is `useMemo` and when to use it?
9. What is `useCallback` and how does it prevent re-renders?
10. Difference between `useRef` and `useState`.
11. How does `useContext` work?
12. What is `useReducer` and when do you prefer it over `useState`?

---

# 🔹 **React Performance Optimization**

1. What is React memoization? (`React.memo`, `useMemo`, `useCallback`)
2. What causes unnecessary re-renders?
3. How do you optimize a large list in React?

   * `React.memo`
   * Windowing (e.g., react-window, react-virtualized)
4. What is code splitting and lazy loading?
5. What is React Profiler?

---

# 🔹 **Advanced React Concepts**

1. What are **controlled vs uncontrolled components**?
2. What is **lifting state up**?
3. Explain **prop drilling** and how to avoid it.
4. Difference between **Context API** and **Redux**.
5. What is **render props**?
6. What are **higher-order components (HOCs)**?
7. What is **Reconciliation** in React?
8. How does React Fiber architecture work?

---

# 🔹 **React Router**

1. How does client-side routing work?
2. Difference between:

   * `<BrowserRouter>`
   * `<HashRouter>`
3. How to redirect programmatically in React Router?
4. What are nested routes?
5. What is lazy loading in React Router?

---

# 🔹 **Redux / State Management (Important for 2+ years)**

1. What is Redux and why use it?
2. Explain Redux data flow.
3. What is an action, reducer, store?
4. Difference between Redux Thunk and Redux Saga.
5. What is RTK (Redux Toolkit) and why is it recommended today?
6. What is reselect?
7. What does "immutability" mean in Redux?

---

# 🔹 **API Integration**

1. How do you call an API using `fetch` or `axios`?
2. How do you handle:

   * loading state
   * error state
   * retry logic
3. What is debounce vs throttle in API calls?
4. How do you cancel API requests in React?

---

# 🔹 **Testing**

1. What is Jest?
2. What is React Testing Library (RTL)?
3. What is the difference between:

   * Unit testing
   * Integration testing
4. How to test:

   * components
   * hooks
   * API calls

---

# 🔹 **React Build & Deployment**

1. Difference between development and production builds?
2. What is tree shaking?
3. What is Webpack and how does it bundle React code?
4. What is environment variable handling in React?

---

# 🔹 **Scenario-Based Questions (Most important!)**

1. **How will you avoid re-rendering of child components unnecessarily?**
2. **You have a slow page — how will you debug and optimize it?**
3. **API call is getting fired multiple times — what could be the reason?**
4. **How to design a scalable folder structure for a large React project?**
5. **How will you store JWT tokens securely?**
6. **How to implement pagination efficiently?**
7. **Component is not updating even after state change — why?**

Here you go — **40 more real business-style ReactJS problems**, grouped by topic, all designed for interview-style practice (2+ years experience).
These problems simulate tasks you’d do in real companies.

---

# 🚀 **MORE BUSINESS-STYLE REACTJS PROBLEMS**

---

# ✅ **SECTION 1 — Data Display & UI Logic (Practical Workflows)**

### **1. Customer List with Status Badges**

Display customers with badges:

* Active (green)
* Inactive (red)
* Pending (yellow)

### **2. Product Grid with Lazy Loading Images**

Use Intersection Observer to load images only when visible.

### **3. Infinite Scroll Chat Window**

Load older messages when user scrolls to top.

### **4. Notification Dropdown**

Show latest 10 notifications with “Mark as read”.

### **5. “Recently Viewed” Section**

Store viewed product IDs in `localStorage` → display them.

---

# ✅ **SECTION 2 — Filtering, Searching & Sorting**

### **6. Multi-Filter Dashboard**

Filters:

* checkbox (in-stock)
* brand list
* price range slider
* rating filter

### **7. Advanced Search with Debounce**

Only search after 300ms delay.

### **8. Server-Side Sorting**

Click column header → call API with `sortBy=name&order=asc`.

### **9. Search Employees by Multiple Fields**

Search by:

* name
* email
* department

### **10. Custom Table Component with Sorting Arrows**

Reusable table with:

* sorting arrows
* highlight sorted column

---

# ✅ **SECTION 3 — Forms & Validation**

### **11. Sign-up Form with Complex Validation**

Validation:

* strong password
* email format
* confirm password
* mobile number validation

### **12. Multi-Step Form (Stepper UI)**

Steps:

1. Personal Data
2. Address
3. Review & Submit

### **13. Dynamic Form Fields**

Add/remove phone number fields dynamically.

### **14. Upload Resume with File Size Limit**

Reject file > 2MB.

### **15. Validate PAN/Aadhar or other ID formats (India-specific)**

Check valid length and structure.

---

# ✅ **SECTION 4 — State Management (Context, Redux, Reducers)**

### **16. Global Alert System**

Any component can trigger toast notifications via Context.

### **17. Theme Settings Stored Globally**

Theme + font size + color scheme.

### **18. Shopping Cart with Redux Toolkit**

Slice includes: add, remove, quantity change.

### **19. Employee Onboarding Wizard (Redux State)**

Each step saved in Redux slice.

### **20. Save App Preferences to Local Storage**

Sync preferences state with localStorage using useEffect.

---

# ✅ **SECTION 5 — API Integration & Async Ops**

### **21. Retry Failed API Calls**

Retry 3 times before showing error message.

### **22. Cancel API Request on Component Unmount**

Fetch abort controller.

### **23. Auto Refresh Access Token**

Use interceptor or fetch wrapper to refresh expired token.

### **24. Save Form Draft to API Every 10 Seconds**

Use intervals.

### **25. Show “Offline Mode” Banner When Internet Disconnects**

Use `navigator.onLine`.

---

# ✅ **SECTION 6 — UI/UX Features**

### **26. Accordion FAQ Section**

Only one accordion open at a time.

### **27. Toggleable Sidebar with Animation**

Expand → collapse with smooth transition.

### **28. Modal Confirmation Dialog**

Ask before deleting critical items.

### **29. Full-Screen Loader While Page Fetches Data**

### **30. Skeleton Loading Screen**

Skeleton placeholders before data loads.

---

# ✅ **SECTION 7 — Routing & Deep Linking**

### **31. User Profile Route**

Route: `/users/:id` → fetch and display data.

### **32. Query Parameter Filters**

Products page filters synced to URL:
`?category=shoes&sort=price_asc`

### **33. Scroll to Section on Navigation Click**

Smooth scroll to specific section on page.

### **34. Custom 404 Page with Auto-Redirect**

---

# ✅ **SECTION 8 — Real-Time Features (WebSockets, Events)**

### **35. Stock Market Ticker**

Real-time price updates for selected stocks.

### **36. Live Location Tracker (Map API)**

Update location every 5s.

### **37. Real-Time Collaboration Indicator**

Show “X people editing this document”.

---

# ✅ **SECTION 9 — Performance Optimization**

### **38. Split Large List using React Window**

Render 10k rows efficiently.

### **39. Throttle Scroll Handler**

Improve performance by throttling expensive scroll events.

### **40. Memoized Select Dropdown**

Dropdown has 2000 options — only re-render when necessary.






Awesome — I’ll deliver **concise, practical solutions (approach + minimal code snippets)** for **all 40 problems** you asked for. These are ready-to-implement patterns you can paste into a React app and expand into full features during interview coding or take-home tasks.

I’ll keep each solution short: **what to do**, **why**, and **a tiny code example** (functional components + hooks). If you want any one expanded into a full working file, say its number and I’ll give the complete implementation.

# 🔧 SECTION 1 — Data Display & UI Logic

---

### 1) Customer List with Status Badges

**Idea:** Map customers → show pill with class based on status.

```jsx
function CustomerList({customers}) {
  return <ul>{customers.map(c=>(
    <li key={c.id}>{c.name} <span className={`badge ${c.status}`}>{c.status}</span></li>
  ))}</ul>
}
```

Use CSS `.badge.active{background:green}` etc.

---

### 2) Product Grid with Lazy Loading Images

**Idea:** Use `IntersectionObserver` to set `src` when visible.

```jsx
// on mount: create observer, observe img refs -> set data-src to src when intersecting
```

Or use `loading="lazy"` for simple cases.

---

### 3) Infinite Scroll Chat Window

**Idea:** On scroll-to-top, fetch previous messages and prepend; keep scroll position.

```jsx
const onScroll = e => {
  if (e.target.scrollTop < 50) fetchOlderMessages();
}
```

Preserve offset: record scrollHeight before prepend and set scrollTop after.

---

### 4) Notification Dropdown

**Idea:** Keep `notifications` state; mark as read toggles `read` flag.

```jsx
function markRead(id){ setNotifs(prev => prev.map(n=>n.id===id?{...n,read:true}:n)) }
```

---

### 5) “Recently Viewed” Section

**Idea:** Push productId to `localStorage` (unique, capped length). Read and fetch items for display.

```js
const addRecent = id => {
  const arr = JSON.parse(localStorage.getItem('recent')||'[]');
  const next = [id,...arr.filter(x=>x!==id)].slice(0,10);
  localStorage.setItem('recent', JSON.stringify(next));
}
```

---

# 🔧 SECTION 2 — Filtering, Searching & Sorting

---

### 6) Multi-Filter Dashboard

**Idea:** Keep filter state (`inStock`, `brands`, `min`, `max`, `rating`) and compute `filtered = products.filter(...)`. Use controlled inputs.

---

### 7) Advanced Search with Debounce

**Idea:** Debounce input (300ms) before calling search.

```jsx
useEffect(()=>{
  const id = setTimeout(()=>doSearch(q),300);
  return ()=>clearTimeout(id);
},[q]);
```

---

### 8) Server-Side Sorting

**Idea:** On header click set `sortBy` and call API with `?sortBy=...&order=...`. Show spinner while loading.

---

### 9) Search Employees by Multiple Fields

**Idea:** Build a combined predicate: `emp.name.includes(q)||emp.email.includes(q)||emp.dept.includes(q)`.

---

### 10) Custom Table Component with Sorting Arrows

**Idea:** Component `<Table columns data onSort />`. For header click toggle sort order and pass to parent. Render arrow icon based on `sort.col` and `sort.order`.

---

# 🔧 SECTION 3 — Forms & Validation

---

### 11) Sign-up Form with Complex Validation

**Idea:** use controlled inputs + validation function. Show errors per field.

```jsx
if(!/.+@.+\..+/.test(email)) setError("Invalid email");
if(password.length<8 || !/\d/.test(password)) setError("Weak password");
```

---

### 12) Multi-Step Form (Stepper UI)

**Idea:** `step` state; show step components; keep form data in top-level state. Validate per step before `setStep(step+1)`.

---

### 13) Dynamic Form Fields

**Idea:** Maintain array `phones`, map to inputs, provide add/remove handlers.

```jsx
setPhones(prev=>[...prev,""]);
```

---

### 14) Upload Resume with File Size Limit

**Idea:** On file select check `file.size` and reject if > 2MB.

```js
if(file.size > 2*1024*1024) setError("File too large");
```

---

### 15) Validate PAN/Aadhar (India-specific)

**Idea:** Regex checks: PAN `/^[A-Z]{5}[0-9]{4}[A-Z]{1}$/`, Aadhaar `/^\d{12}$/` and show appropriate message.

---

# 🔧 SECTION 4 — State Management

---

### 16) Global Alert System

**Idea:** `AlertContext` with `showAlert({type,msg})`. Provider stores alerts array and burners. Components call `useContext(AlertContext).showAlert(...)`.

---

### 17) Theme Settings Stored Globally

**Idea:** `ThemeContext` with state `{theme,fontSize}`; store in localStorage on change.

---

### 18) Shopping Cart with Redux Toolkit

**Idea:** Create `cartSlice` with `addItem, removeItem, updateQty`. Use `createSlice()` and `configureStore()`.

---

### 19) Employee Onboarding Wizard (Redux State)

**Idea:** Each wizard step writes to a slice. On submit combine and call API.

---

### 20) Save App Preferences to Local Storage

**Idea:** `useEffect(()=>localStorage.setItem('prefs', JSON.stringify(prefs)), [prefs])` and initialize from localStorage.

---

# 🔧 SECTION 5 — API Integration & Async Ops

---

### 21) Retry Failed API Calls

**Idea:** Implement `retryFetch(url, n)` with recursive attempts and exponential backoff.

---

### 22) Cancel API Request on Component Unmount

**Idea:** Use `AbortController` and pass `signal` to fetch; `controller.abort()` in cleanup.

---

### 23) Auto Refresh Access Token

**Idea:** Interceptor (axios) or wrapper to catch 401, call refresh endpoint, retry original request.

---

### 24) Save Form Draft to API Every 10 Seconds

**Idea:** `useEffect` with `setInterval` that posts current form state to `/drafts`. Clear interval on unmount.

---

### 25) Show “Offline Mode” Banner When Internet Disconnects

**Idea:** `window.addEventListener('online'/'offline')`; update state `isOnline` and render banner accordingly.

---

# 🔧 SECTION 6 — UI/UX Features

---

### 26) Accordion FAQ Section

**Idea:** Track `openId` and on click set it; if same id clicked set `null`. Only one open.

---

### 27) Toggleable Sidebar with Animation

**Idea:** CSS transition or use a library; `isOpen` state toggles class `open` to slide in/out.

---

### 28) Modal Confirmation Dialog

**Idea:** `<Confirm onConfirm onCancel message>`; show by setting `confirmProps` in parent.

---

### 29) Full-Screen Loader While Page Fetches Data

**Idea:** If `loading` true render overlay div centered spinner.

---

### 30) Skeleton Loading Screen

**Idea:** Render skeleton rectangles (CSS animation) while data fetching.

---

# 🔧 SECTION 7 — Routing & Deep Linking

---

### 31) User Profile Route `/users/:id`

**Idea:** `const {id} = useParams(); useEffect(()=>fetch(`/api/users/${id}`))`.

---

### 32) Query Parameter Filters

**Idea:** Sync filters to URL with `useSearchParams()` (react-router v6) so the URL is shareable.

---

### 33) Scroll to Section on Navigation Click

**Idea:** Use `ref.current.scrollIntoView({behavior:'smooth'})`.

---

### 34) Custom 404 Page with Auto-Redirect

**Idea:** Show helpful message and `useEffect(()=>setTimeout(()=>navigate('/'),3000),[])`.

---

# 🔧 SECTION 8 — Real-Time Features

---

### 35) Stock Market Ticker

**Idea:** WebSocket subscription to tick updates; update state per symbol and render a small horizontally scrolling ticker.

---

### 36) Live Location Tracker (Map API)

**Idea:** Use `navigator.geolocation.watchPosition()` to get updates and update marker on map (Google/Mapbox).

---

### 37) Real-Time Collaboration Indicator

**Idea:** WebSocket or presence channel; server emits current editor count; render small badge.

---

# 🔧 SECTION 9 — Performance Optimization

---

### 38) Split Large List using React Window

**Idea:** Use `react-window` or `react-virtualized` to render only visible rows for 10k+ items.

---

### 39) Throttle Scroll Handler

**Idea:** Use `lodash.throttle` or custom throttle to limit handler calls, avoiding heavy computation each scroll event.

---

### 40) Memoized Select Dropdown

**Idea:** Wrap expensive dropdown in `React.memo` and provide stable `options` prop (avoid re-creating arrays inline). Use `useCallback` for handlers.

---


