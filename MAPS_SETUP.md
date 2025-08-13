# Google Maps API Setup Instructions

## To enable Google Maps and Places API functionality:

### 1. Get a Google Maps API Key
1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select existing one
3. Enable the following APIs:
   - Maps JavaScript API
   - Places API
4. Create credentials (API Key)
5. Restrict the API key to your domain for security

### 2. Replace the API Key
In `explore.html`, find this line:
```html
<script async defer 
  src="https://maps.googleapis.com/maps/api/js?key=AIzaSyB1t6Q16fCeXMoyoemq3UFW-8OW2Om2-S8&libraries=places&callback=initMap">
</script>
```

Replace `YOUR_GOOGLE_MAPS_API_KEY` with your actual API key: `AIzaSyB1t6Q16fCeXMoyoemq3UFW-8OW2Om2-S8`

### 3. For Development (Optional)
You can also use the app without Google Maps API - it will work with the static data and show a basic map placeholder.

## Features Available:

✅ **Search Functionality**: Search for places by name, city, or state
✅ **Filter by Category**: Filter places by monuments, temples, beaches, mountains, cities
✅ **Tourist Places Database**: 12+ popular Indian destinations with real images
✅ **Interactive Map**: Google Maps integration with markers
✅ **Place Details**: Modal popups with detailed information
✅ **Wishlist**: Save favorite places to local storage
✅ **Responsive Design**: Works on desktop and mobile
✅ **API Integration**: Connects to backend when available
✅ **Demo Mode**: Works without backend for testing

## API Endpoints:
- POST `/api/auth/register` - User registration
- POST `/api/auth/login` - User login  
- GET `/api/places` - Get all places
- GET `/api/reviews` - Get reviews

The app includes fallback functionality and will work even if the backend is not running!
