Below are **clean, production-ready React solutions** for tasks **21–25**.
These cover **retry APIs, canceling requests, token refresh logic, auto-save drafts, and offline detection** — all **real-world interview topics** for 2+ years experience.

---

# ======================================================

# ✅ **21. Retry Failed API Calls (Retry 3 Times)**

======================================================

## ⭐ Generic Retry Function

```js
async function fetchWithRetry(url, options = {}, retries = 3) {
  try {
    const res = await fetch(url, options);
    if (!res.ok) throw new Error("Server error");
    return res.json();
  } catch (err) {
    if (retries === 1) throw err;
    return fetchWithRetry(url, options, retries - 1);
  }
}
```

---

## ⭐ Usage in a Component

```jsx
useEffect(() => {
  fetchWithRetry("/api/data", {}, 3)
    .then(setData)
    .catch(() => setError("Failed after 3 retries"));
}, []);
```

---

### ✔ Explanation

* If API fails, it retries up to 3 times
* Only after 3 failures shows error
* Useful for unstable network or backend APIs

---

# ======================================================

# ✅ **22. Cancel API Request on Component Unmount (AbortController)**

======================================================

---

## ⭐ API Call with AbortController

```jsx
useEffect(() => {
  const controller = new AbortController();

  fetch("/api/users", { signal: controller.signal })
    .then(res => res.json())
    .then(setUsers)
    .catch(err => {
      if (err.name === "AbortError") {
        console.log("Request cancelled");
      }
    });

  // Cancel request on unmount
  return () => controller.abort();
}, []);
```

---

### ✔ Explanation

* `AbortController` stops the fetch immediately
* Prevents memory leaks
* React will not try to update state on unmounted component

---

# ======================================================

# ✅ **23. Auto Refresh Access Token (Using Axios Interceptor)**

======================================================

### Scenario:

* Access token expires → API returns 401
* Automatically call `/refresh-token`
* Retry original request

---

## ⭐ Axios Setup

```js
import axios from "axios";

const api = axios.create({
  baseURL: "/api"
});

let isRefreshing = false;
let failedQueue = [];

// -----------------------------------
// Request Interceptor → attach token
// -----------------------------------
api.interceptors.request.use((config) => {
  config.headers.Authorization = "Bearer " + localStorage.getItem("accessToken");
  return config;
});

// -----------------------------------
// Response Interceptor → handle 401
// -----------------------------------
api.interceptors.response.use(
  (res) => res,
  async (error) => {
    const original = error.config;

    // If token expired
    if (error.response.status === 401 && !original._retry) {
      original._retry = true;

      if (!isRefreshing) {
        isRefreshing = true;

        const refreshToken = localStorage.getItem("refreshToken");

        const { data } = await axios.post("/api/refresh", { refreshToken });
        localStorage.setItem("accessToken", data.accessToken);

        isRefreshing = false;

        failedQueue.forEach((cb) => cb(data.accessToken));
        failedQueue = [];
      }

      return new Promise((resolve) => {
        failedQueue.push((newToken) => {
          original.headers.Authorization = "Bearer " + newToken;
          resolve(api(original));
        });
      });
    }

    return Promise.reject(error);
  }
);

export default api;
```

---

### ✔ Explanation

* Interceptor catches **401 Unauthorized** errors
* Refresh token API is triggered
* Once new token is received → retry original request
* Prevents logout on token expiry
* Used in **all real enterprise React apps**

---

# ======================================================

# ✅ **24. Save Form Draft to API Every 10 Seconds**

======================================================

---

## ⭐ Auto-Save with `setInterval`

```jsx
function FormDraft() {
  const [form, setForm] = useState({ title: "", description: "" });

  useEffect(() => {
    const interval = setInterval(() => {
      fetch("/api/save-draft", {
        method: "POST",
        body: JSON.stringify(form)
      });
      console.log("Draft saved");
    }, 10000); // every 10 sec

    return () => clearInterval(interval);
  }, [form]);

  return (
    <>
      <input
        placeholder="Title"
        onChange={(e) => setForm({ ...form, title: e.target.value })}
      />

      <textarea
        placeholder="Description"
        onChange={(e) => setForm({ ...form, description: e.target.value })}
      />
    </>
  );
}
```

---

### ✔ Explanation

* Saves draft every 10 seconds
* Cleanup stops interval when component unmounts
* Used for forms where users may leave page accidentally (blogs, CRM forms)

---

# ======================================================

# ✅ **25. Show “Offline Mode” Banner When Internet Disconnects**

======================================================

---

## ⭐ Detect Offline/Online Events

```jsx
function OfflineBanner() {
  const [online, setOnline] = useState(navigator.onLine);

  useEffect(() => {
    const goOnline = () => setOnline(true);
    const goOffline = () => setOnline(false);

    window.addEventListener("online", goOnline);
    window.addEventListener("offline", goOffline);

    return () => {
      window.removeEventListener("online", goOnline);
      window.removeEventListener("offline", goOffline);
    };
  }, []);

  if (online) return null;

  return (
    <div style={{ background: "orange", padding: 10 }}>
      ⚠ You are offline — Showing cached data
    </div>
  );
}
```

---

### ✔ Explanation

* Uses `navigator.onLine`
* Listens to global `online` and `offline` events
* Immediately shows banner when disconnected
* Useful for PWAs, mobile-first apps

---

# 🎯 FINAL INTERVIEW SUMMARY (Super Quick)

| Feature        | Key Technique                      |
| -------------- | ---------------------------------- |
| Retry API      | Recursive retry logic              |
| Cancel request | AbortController                    |
| Token refresh  | Axios interceptors                 |
| Auto-save      | setInterval + cleanup              |
| Offline banner | navigator.onLine + event listeners |

These are **real enterprise patterns** React developers must know.

---

