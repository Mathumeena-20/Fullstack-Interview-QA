Below are **clean, production-style React solutions** for **35–37**, covering real-time stock tickers, live map tracking, and collaborative editing indicators.
These are **high-value interview tasks** for 2+ years React developers.

---

# =====================================================

# ✅ **35. Stock Market Ticker (Real-Time Price Updates)**

=====================================================

You can simulate real-time updates using:
✔ WebSockets (actual real-time)
✔ setInterval (mock real-time for demo/interviews)

Below example uses **WebSocket-style logic**.

---

## ⭐ Example using WebSocket API (Mock)

```jsx
import { useEffect, useState } from "react";

function StockTicker({ symbols }) {
  const [prices, setPrices] = useState({});

  useEffect(() => {
    // Fake WebSocket (replace with real ws URL)
    const ws = new WebSocket("wss://example.com/stocks");

    ws.onopen = () => {
      ws.send(JSON.stringify({ type: "subscribe", symbols }));
    };

    ws.onmessage = (event) => {
      const data = JSON.parse(event.data); // {symbol: "AAPL", price: 150.98}

      setPrices(prev => ({
        ...prev,
        [data.symbol]: data.price
      }));
    };

    return () => ws.close();
  }, [symbols]);

  return (
    <div>
      <h2>Live Stock Prices</h2>
      {symbols.map(s => (
        <p key={s}>
          {s}: {prices[s] ? prices[s].toFixed(2) : "Loading..."}
        </p>
      ))}
    </div>
  );
}
```

---

### ✔ Explanation

* Opens WebSocket connection
* Subscribes to selected stocks
* Updates UI instantly via `onmessage`
* Works perfectly for dashboards, finance apps, crypto tickers

**Replace the WebSocket URL with any real-time stream API** (e.g., Polygon.io, Finnhub, Binance WebSocket).

---

# =====================================================

# ✅ **36. Live Location Tracker (Map API)**

### Update user location every 5 seconds

=====================================================

We use:
✔ Browser Geolocation API
✔ setInterval loop
✔ Google Maps or Leaflet (example shows simple coordinates)

---

## ⭐ Location Tracking Component

```jsx
function LiveLocationTracker() {
  const [location, setLocation] = useState({ lat: null, lng: null });

  useEffect(() => {
    const updateLocation = () => {
      navigator.geolocation.getCurrentPosition(
        pos => {
          setLocation({
            lat: pos.coords.latitude,
            lng: pos.coords.longitude
          });
        },
        err => console.error(err),
        { enableHighAccuracy: true }
      );
    };

    updateLocation(); // initial
    const interval = setInterval(updateLocation, 5000);

    return () => clearInterval(interval);
  }, []);

  return (
    <>
      <h2>Live Location (updates every 5s)</h2>
      {location.lat ? (
        <p>Lat: {location.lat} | Lng: {location.lng}</p>
      ) : (
        <p>Detecting location…</p>
      )}
    </>
  );
}
```

---

## ⭐ Map Integration (Example with Google Maps)

If using Google Maps package:

```jsx
<Map center={location} zoom={14}>
  <Marker position={location} />
</Map>
```

---

### ✔ Explanation

* `navigator.geolocation.getCurrentPosition()` retrieves live location
* `setInterval` updates it every 5 seconds
* Can easily plug into Google Maps or Leaflet
* Perfect for delivery apps, live tracking, field team tracking

---

# =====================================================

# ✅ **37. Real-Time Collaboration Indicator**

### “X people editing this document”

=====================================================

This simulates Google Docs-style collaborative editing.

Best done with:
✔ WebSockets
✔ Firebase Realtime DB
✔ Socket.io

Below example uses mock WebSocket/Sockets.

---

## ⭐ Collaboration Presence Component

```jsx
import { useEffect, useState } from "react";

function CollaborationIndicator({ docId }) {
  const [editingUsers, setEditingUsers] = useState([]);

  useEffect(() => {
    const ws = new WebSocket("wss://example.com/collab");

    ws.onopen = () => {
      ws.send(JSON.stringify({ type: "join", docId }));
    };

    ws.onmessage = (event) => {
      const data = JSON.parse(event.data);

      // Example: { type: 'presence', users: ['A', 'B', 'C'] }
      if (data.type === "presence") {
        setEditingUsers(data.users);
      }
    };

    return () => {
      ws.send(JSON.stringify({ type: "leave", docId }));
      ws.close();
    };
  }, [docId]);

  return (
    <div style={{ background: "#f4f4f4", padding: 10, display: "inline-block" }}>
      {editingUsers.length > 0 ? (
        <p>👥 {editingUsers.length} people editing this document</p>
      ) : (
        <p>You're the only one here.</p>
      )}
    </div>
  );
}
```

---

### ✔ How it works

* When component loads → user joins the WebSocket room
* Server broadcasts list of connected editors
* UI updates live
* When user leaves/unmounts → send “leave” message

This is how tools like:
🟦 Google Docs
🟧 Notion
🟩 Figma
show real-time collaborators.

---

# 🎯 FINAL INTERVIEW SUMMARY

| Feature                 | Technology             | Key Concept                 |
| ----------------------- | ---------------------- | --------------------------- |
| Stock ticker            | WebSockets             | Real-time push updates      |
| Live tracker            | Geolocation + Interval | GPS refresh every 5 seconds |
| Collaboration indicator | WebSocket/Sockets      | Presence tracking           |

These are excellent to demonstrate real-time frontend skills.

---

