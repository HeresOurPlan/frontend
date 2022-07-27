<template>
<!-- click radio twice to zoom in to specific location -->
  <div style="background-color:#FCF6E7">
    <Navbar />
    <h1 style="color: #BC4749; font-family: Bookman Old Style; font-size: 30px;
    padding-top: 20px; padding-left: 175px; ">
    </h1>
    <div class="mt-3"><strong>Activities in your Itinerary: </strong></div><br/>
    <b-select 
      v-model="location"
      :options = "activities"
      value-field = "address"
      text-field = "address"
      @change="getlatlong()">
      <!-- <b-select-option v-for="item in fetched" :value="item.title"> {{ item.title }} </b-select-option>
      <b-select-option value="Botanic Gardens">Botanic</b-select-option>
      <b-select-option value="Marina Bay Sands">Marina</b-select-option>
      <b-select-option  value="Universal Studios Singapore" >USS</b-select-option>
      <b-select-option>a</b-select-option>
      <b-select-option>a</b-select-option> -->
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
      <l-marker v-for="item in activities" :key="item" :lat-lng="item.locationCoord">
          <!-- <l-popup>
            <div id='latlong'>
              {{ item.coord }}
            </div>
            <button @click="addlocation">Add in Itinerary</button>
          </l-popup> -->
      <l-tooltip :content="item.address" :options="options">
        <!-- <button @click="addlocation">Add in Itinerary</button> -->
      </l-tooltip>
      </l-marker>
    </l-map>


  <br/><br/><br/><br/>

    <div class = "icons">
        <a href ="/new_loc_map"><i class="fa-regular fa-square-plus fa-3x" style="color:black;"></i></a>
    </div>

  <br/><br/><br/><br/>    <br/>

  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";

export default {
  data() {
    return {
      // location: "Botanic Gardens",
      // url: "https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",
      // attribution:
      //   '&copy; <a target="_blank" href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      // zoom: 11,
      // center: [1.3521, 103.8198],
      // // Singapore LatLng
      // indivactivity: this.indivactivity,
      // or is it indivactivity: []
      fetched: false,
      activities: [],
      value: null
    };
  },
  fetchOnServer: false,
  async fetch() {
    // fetch the marker here
    // override this.markers
    // v-for upstairs
    // getlatlong refer to this.markers
    this.activities = await this.$axios.$get("http://localhost:8080/activities");
    console.log(this.activities)
    },

  components: { Navbar },
  methods: {
    getlatlong: function () {
      var dict = this.activities;
      this.zoom = 15;
      setTimeout(() => {
        this.center = dict[this.location];
        console.log(this.location);
      }, 300);
    },
  },
};
</script>


<style>
    .icons{
        text-align: center;
    }
</style>