<template>
    <div>
    <Navbar />
    <h1 style="color: #BC4749; font-family: merriweather; font-size: 30px;
    padding-top: 20px; ">Double click to select
    </h1>
  <l-map style="height: 300px" :zoom="zoom" :center="center" @dblclick="onMapClick">
    <l-tile-layer
      :url="tileProvider.url"
      :attribution="tileProvider.attribution"
    />
    <l-marker
      v-if="position.lat && position.lng"
      visible
      draggable
      :icon="icon"
      :lat-lng.sync="position"
      @dragstart="dragging = true"
      @dragend="dragging = false"
    >
      <l-tooltip :options="{ permanent: true }" >
        <b>{{this.address}}</b>
        <br>
        <hr />
        <b>LAT: {{this.position.lat}}</b>
        <br>
        <b>LONG: {{this.position.lng}}</b>
        <br>
        
      </l-tooltip>
    </l-marker>
  </l-map>
  <br>
    <div class="col-md-12 text-center">
      <b-btn class="btn btn-danger" @click="storingcoords" align="center">
            <a href="additinerary.vue" name="addedActivity" style="color: white; font-weight: bold;">
              Add This Activity!
            </a>
      </b-btn>
    </div>
  </div>
</template>
<script>
import Navbar from "@/components/Navbar.vue";
export default {
  props: {
     value: {
      type: Object,
      required: true
    },
    defaultLocation: {
      type: Object,
      default: () => ({
        lat: 8.9806,
        lng: 38.7578
      })
    }
  },
  data() {
    return {
      loading:false,
      userLocation: {},
      position: {},
      address:"",
      tileProvider: {
        attribution:
          '&copy; <a target="_blank" href="http://osm.org/copyright">OpenStreetMap</a> contributors',
        url: "https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
      },
      zoom: 11,
      center: [1.3521,103.8198],
      dragging:false
    };
  },
  mounted() {
    this.getUserPosition();
  },
    watch: {
    position: {
      deep: true,
      async handler(value) {
        this.address = await this.getAddress();
        this.$emit("input", { position: value, address: this.address });
      }
    }
  },
  computed: {
    tooltipContent() {
      if (this.dragging) return "...";
      if (this.loading) return "Loading...";
    }
  },
  methods: {
    async getAddress() {
      this.loading = true;
      let address = "Unresolved address";
      try {
        const { lat, lng } = this.position;
        const result = await fetch(
          `https://nominatim.openstreetmap.org/reverse?format=jsonv2&lat=${lat}&lon=${lng}`
        );
        if (result.status === 200) {
          const body = await result.json();
          address = body.display_name;
        }
      } catch (e) {
        console.error("Reverse Geocode Error->", e);
      }
      this.loading = false;
      return address;
    },
    onMapClick(value) {
      // place the marker on the clicked spot
      this.position = value.latlng;
    },
    getUserPosition() {
      if (navigator.geolocation) {
        // get GPS position
        navigator.geolocation.getCurrentPosition(pos => {
          // set the user location
          this.userLocation = {
            lat: pos.coords.latitude,
            lng: pos.coords.longitude
          };
        });
      }
    },
    // storingcoords() {
    //   if (this.onMapClick != ""):
    //     to_store = this.onMapClick;
    //     console.log(to_store);
    //     this.$session.set("addActivity", to_store);
    //   else:
    //     return "Click on a location!";
    // }

  }
};
</script>