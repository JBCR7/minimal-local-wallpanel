# minimal-local-wallpanel 
A bloat-free, zero-dependency HTML/CSS dashboard template for legacy hardware and local-first home automation.

A zero-dependency, vanilla HTML5 and CSS3 dashboard layout designed to act as a lightweight UI for local-first systems. Perfect for legacy tablets, low-power e-ink displays, or old monitors where modern single-page apps (SPAs) lag.

## ⚡ Why This Approach?
* **Zero Dependencies:** No frameworks, no external JS engines, no white-space sensitive YAML.
* **Legacy-Friendly:** Runs flawlessly on older web views and weak hardware.
* **Local-First Ready:** Easy to hook into raw local sockets, MQTT bridges, or micro-services.

## 🚀 How to Use It
1. Clone this repository or download the `index.html` file.
2. Double-click `index.html` to run it completely offline in any browser—no server required.

## 🔌 Hooking Up Local Data / Sensors
To dynamically update fields (like power metrics or temperatures) without adding bloat, insert a simple native script at the bottom of the HTML file:

```javascript
// Example: Polling a local microcontroller or sensor endpoint
async function updateMetrics() {
    try {
        const response = await fetch('http://localhost:8080/api/sensors');
        const data = await response.json();
        document.querySelector('.metric-value').innerText = data.temperature + " °F";
    } catch (err) {
        console.error("Local sensor offline", err);
    }
}
setInterval(updateMetrics, 5000); // Polls every 5 seconds
