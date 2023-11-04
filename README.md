# Gps
<!DOCTYPE html>
<html>
  <head>
    <title>LocationExplorer</title>
  </head>
  <body>
    <h1>LocationExplorer</h1>
    <div id="map"></div>

    <script>
      // Function to initialize the map and get user's location
      function initMap() {
        // Check if the browser supports geolocation
        if ('geolocation' in navigator) {
          navigator.geolocation.getCurrentPosition(function(position) {
            const userLocation = {
              lat: position.coords.latitude,
              lng: position.coords.longitude
            };

            // Create a map centered on the user's location
            const map = new google.maps.Map(document.getElementById('map'), {
              center: userLocation,
              zoom: 15
            });

            // Add a marker for the user's location
            new google.maps.Marker({
              position: userLocation,
              map: map,
              title: 'Your Location'
            });
          });
        } else {
          alert('Geolocation is not supported by your browser.');
        }
      }
    </script>

    <!-- Include the Google Maps JavaScript API -->
    <script
      src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&callback=initMap"
      async
      defer
    ></script>
  </body>
</html>
