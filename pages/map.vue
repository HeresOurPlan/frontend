<template>
  <div>
    <Navbar />
    <h1 style="color: #BC4749; font-family: merriweather; font-size: 30px;
    padding-top: 20px; padding-left: 175px; ">
    </h1>
    <l-map style="height: 300px" :zoom="zoom" :center="center">
      <l-tile-layer :url="url" :attribution="attribution">
      </l-tile-layer>
      <l-marker v-for="item in markers" :key="item" :lat-lng="item.coord">
      <l-tooltip :content="item.name" :options="options"></l-tooltip>
      </l-marker>
    </l-map>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";

export default {
  
  data () {
    return {
      location: 'Botanic Gardens',
      url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
      attribution:
        '&copy; <a target="_blank" href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      zoom: 11,
      center: [1.3521,103.8198],
      // Singapore LatLng
      markers: [{name: "Botanic Gardens", coord: [1.3138, 103.8159]},
                {name:"Marina Bay Sands", coord: [1.2847, 103.8610]},
                {name:"Universal Studios Singapore", coord: [1.2540, 103.8238]}]
    };
  },
  components: { Navbar },
  // methods: { 
  //   getlatlong: function() {
  //       var dict = {
  //       "Botanic Gardens": [1.3138, 103.8159],
  //       "Marina Bay Sands" : [1.2847, 103.8610],
  //       "Universal Studios Singapore" : [1.2540, 103.8238]
  //       };
  //       this.markerLatLng.push = dict[this.location];
  //       this.center = dict[this.location];
  //       console.log(this.location)
  //       console.log(dict[this.location]);
        
  //     // console.log(this.location);
  //     // console.log(dict[this.location]);
  //     // return {
  //     //   url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
  //     //   attribution:
  //     //     '&copy; <a target="_blank" href="http://osm.org/copyright">OpenStreetMap</a> contributors',
  //     //   zoom: 12,
  //     //   center: dict[this.location],
  //     //   // Singapore LatLng
  //     //   markerLatLng: dict[this.location]
  //   }
  //  }
}
</script>