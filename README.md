Check if the browser supports geolocation
Set options for hih accuracy like 5 second timeout with no caching. 
Use watchPosition to track the users location continously. emit the latitude and longitude with socket mention as "send-location". check any errors in the console.
Initialize a map centered at coordinates (0,0) with zoom coordinates 5 using leaflet. use the map from openstreetmap.
Add openstreet tile to the map
create an empty object marker
when recieving the location data via the socket , extract its is, latitude,longitude and centre of the  map on the new coordinates
if  a marker for the id exist , update its position . else create new marker and add the new coordinates to the map.
