<template>
<!-- click radio twice to zoom in to specific location -->
  <div>
    <Navbar />
    <h1 style="color: #BC4749; font-family: merriweather; font-size: 30px;
    padding-top: 20px; padding-left: 175px; ">
    </h1>
    <b-select  v-model="location"  @change="getlatlong()">
      <b-select-option value="Botanic Gardens">Botanic</b-select-option>
      <b-select-option value="Marina Bay Sands">Marina</b-select-option>
      <b-select-option  value="Universal Studios Singapore" >USS</b-select-option>
      <b-select-option>a</b-select-option>
      <b-select-option>a</b-select-option>
    </b-select>
    <!-- <inputtype="radio" id="bg" name="location" value="Botanic Gardens">
    <label for="bg">Botanic Gardens</label><br>
    <input v-model="location" type="radio" id="mbs" name="location"  @change="getlatlong()">
    <label for="mbs">Marina Bay Sands</label><br>
    <input v-model="location" type="radio" id="uss" name="location"@change="getlatlong()">
    <label for="uss">Universal Studios Singapore</label> -->
    <l-map style="height: 300px" :zoom="zoom" :center="center">
      <l-tile-layer :url="url" :attribution="attribution">
      </l-tile-layer>
      <l-marker v-for="item in markers" :key="item" :lat-lng="item.coord">
          <!-- <l-popup>
            <div id='latlong'>
              {{ item.coord }}
            </div>
            <button @click="addlocation">Add in Itinerary</button>
          </l-popup> -->
      <l-tooltip :content="item.name" :options="options">
        <!-- <button @click="addlocation">Add in Itinerary</button> -->
      </l-tooltip>
      </l-marker>
    </l-map>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";

export default {
  data() {
    return {
      location: "Botanic Gardens",
      url: "https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",
      attribution:
        '&copy; <a target="_blank" href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      zoom: 11,
      center: [1.3521, 103.8198],
      // Singapore LatLng
      markers: [
        { name: "Botanic Gardens", coord: [1.3138, 103.8159] },
        { name: "Marina Bay Sands", coord: [1.2847, 103.861] },
        { name: "Universal Studios Singapore", coord: [1.254, 103.8238] },
      ],
    };
  },
  async fetch() {
    // fetch the marker here
    // override this.markers
    // v-for upstairs
    // getlatlong refer to this.markers
  },
  components: { Navbar },
  methods: {
    getlatlong: function () {
      var dict = {
        "Botanic Gardens": [1.3138, 103.8159],
        "Marina Bay Sands": [1.2847, 103.861],
        "Universal Studios Singapore": [1.254, 103.8238],
      };
      this.zoom = 15;
      setTimeout(() => {
        this.center = dict[this.location];
        console.log(this.location);
      }, 300);
    },
  },
};
</script>