<h1 align= "center">Real-Time Location Tracking with Geolocation, Socket.IO, and Leaflet</h1>

1. ✅ **Check if the browser supports geolocation**  
   Use the `navigator.geolocation` API to verify support.

2. ⚙️ **Set geolocation options**  
   - Enable high accuracy  
   - Set timeout to `5000` ms (5 seconds)  
   - Set `maximumAge` to `0` (no caching)

3. 📍 **Use `watchPosition()`**  
   Continuously track the user's location.  
   On location update, **emit latitude and longitude** using a `Socket.IO` event:
   
   socket.emit("send-location", { latitude, longitude });
   
🐞 Check for errors
Print any geolocation errors to the browser console using:
console.error(error);

🗺️ Initialize a Leaflet map

Centered at coordinates (0, 0)

Set zoom level to 5

const map = L.map("map").setView([0, 0], 5);
🌍 Add OpenStreetMap tile layer

L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
  attribution: '&copy; OpenStreetMap contributors',
}).addTo(map);
📌 Create an empty markers object
This will be used to store and update multiple user markers dynamically:

const markers = {};
🔄 On receiving location data from Socket.IO

Extract the id, latitude, and longitude

Center the map on the new coordinates

If a marker for the id exists, update its position

Else, create a new marker and add it to the map:
