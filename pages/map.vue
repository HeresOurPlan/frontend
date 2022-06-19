<template>
  <div>
    <Navbar />
    <h1 style="color: #BC4749; font-family: merriweather; font-size: 30px;
    padding-top: 20px; padding-left: 175px; ">
    </h1>
    <l-map style="height: 300px" :zoom="zoom" :center="center">
      <l-tile-layer :url="url" :attribution="attribution">
      </l-tile-layer>
      <l-marker :lat-lng="markerLatLng">
      </l-marker>
    </l-map>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";

export default {
  data () {
    return {
      url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
      attribution:
        '&copy; <a target="_blank" href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      zoom: 12,
      center: [1.3521, 103.8198],
      // Singapore LatLng
      markerLatLng: [1.3521, 103.8198]
    };
  },
  components: { Navbar }
}
</script>