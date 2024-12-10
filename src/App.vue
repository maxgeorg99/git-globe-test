<template>
  <div id="app">
    <MyGlobe :routes="routes" />
  </div>
</template>

<script>
import MyGlobe from './components/MyGlobe.vue';

export default {
  name: 'App',
  components: {
    MyGlobe,
  },
  data() {
    return {
      routes: [
        { startLat: 40.7128, startLng: -74.0060, endLat: 48.8566, endLng: 2.3522, color: 'rgba(255, 165, 0, 0.8)', order: 1 }, // New York to Paris
        { startLat: 40.7128, startLng: -74.0060, endLat: 51.5074, endLng: -0.1278, color: 'rgba(0, 255, 0, 0.8)', order: 2 }, // New York to London
        { startLat: 40.7128, startLng: -74.0060, endLat: 52.5200, endLng: 13.4050, color: 'rgba(0, 0, 255, 0.8)', order: 3 }, // New York to Berlin
        { startLat: 40.7128, startLng: -74.0060, endLat: 41.9028, endLng: 12.4964, color: 'rgba(255, 0, 0, 0.8)', order: 4 }, // New York to Rome
        { startLat: 40.7128, startLng: -74.0060, endLat: 50.8503, endLng: 4.3517, color: 'rgba(128, 0, 128, 0.8)', order: 5 }, // New York to Brussels
        { startLat: 40.7128, startLng: -74.0060, endLat: 60.1695, endLng: 24.9354, color: 'rgba(0, 128, 128, 0.8)', order: 6 }, // New York to Helsinki
        { startLat: 40.7128, startLng: -74.0060, endLat: 59.3293, endLng: 18.0686, color: 'rgba(255, 215, 0, 0.8)', order: 7 }, // New York to Stockholm
        { startLat: 40.7128, startLng: -74.0060, endLat: 55.7558, endLng: 37.6173, color: 'rgba(255, 69, 0, 0.8)', order: 8 }, // New York to Moscow
        { startLat: 40.7128, startLng: -74.0060, endLat: 53.3498, endLng: -6.2603, color: 'rgba(0, 191, 255, 0.8)', order: 9 }, // New York to Dublin
        { startLat: 40.7128, startLng: -74.0060, endLat: 48.2082, endLng: 16.3738, color: 'rgba(75, 0, 130, 0.8)', order: 10 } , // New York to Vienna
        { startLat: 40.7128, startLng: -74.0060, endLat: 52.3676, endLng: 4.9041, color: 'rgba(244, 164, 96, 0.8)', order: 11 }, // New York to Amsterdam
        { startLat: 40.7128, startLng: -74.0060, endLat: 39.9042, endLng: -3.7038, color: 'rgba(0, 255, 127, 0.8)', order: 12 }, // New York to Madrid
        { startLat: 40.7128, startLng: -74.0060, endLat: 45.4642, endLng: 9.1900, color: 'rgba(255, 140, 0, 0.8)', order: 13 }, // New York to Milan
        { startLat: 40.7128, startLng: -74.0060, endLat: 38.7223, endLng: -9.1393, color: 'rgba(0, 0, 139, 0.8)', order: 14 }, // New York to Lisbon
        { startLat: 40.7128, startLng: -74.0060, endLat: 47.4979, endLng: 19.0402, color: 'rgba(139, 0, 139, 0.8)', order: 15 }, // New York to Budapest
        { startLat: 40.7128, startLng: -74.0060, endLat: 50.0755, endLng: 14.4378, color: 'rgba(255, 20, 147, 0.8)', order: 16 }, // New York to Prague
        { startLat: 40.7128, startLng: -74.0060, endLat: 59.436, endLng: 24.7536, color: 'rgba(123, 104, 238, 0.8)', order: 17 }, // New York to Tallinn
        { startLat: 40.7128, startLng: -74.0060, endLat: 56.9496, endLng: 24.1052, color: 'rgba(173, 216, 230, 0.8)', order: 18 }, // New York to Riga
        { startLat: 40.7128, startLng: -74.0060, endLat: 54.6872, endLng: 25.2797, color: 'rgba(199, 21, 133, 0.8)', order: 19 }, // New York to Vilnius
      ],
    };
  },
};
</script>
