<template>
  <div>
    <Navbar />
    <h1
      style="
        color: #bc4749;
        font-family: merriweather;
        font-size: 50px;
        padding-top: 20px;
        padding-left: 2%;
        text-align: center;
      "
    >
      <strong>
        <i> Add Your Activity </i>
      </strong>
    </h1>

    <div class="addItineraryDetails">
      <input
        v-model="activityName"
        placeholder="Name of Activity"
        style="
          background-color: #f2e8cf;
          width: 25%;
          color: black;
          border: 5px solid #f2e8cf;
          border-radius: 10px;
          box-sizing: border-box;
        "
      />
      <br /><br />
      <input
        v-model="address"
        placeholder="Address"
        style="
          background-color: #f2e8cf;
          width: 25%;
          color: black;
          border: 5px solid #f2e8cf;
          border-radius: 10px;
          box-sizing: border-box;
        "
      />
      <br /><br />
      <input
        v-model="locationCoord"
        placeholder="Coordinates"
        style="
          background-color: #f2e8cf;
          width: 25%;
          color: black;
          border: 5px solid #f2e8cf;
          border-radius: 10px;
          box-sizing: border-box;
        "
      />
      <br /><br />
      <select
        v-model="itineraryRank"
        placeholder="Rank on Itinerary (1-5)"
        style="
          background-color: #f2e8cf;
          width: 25%;
          color: black;
          border: 5px solid #f2e8cf;
          border-radius: 10px;
          box-sizing: border-box;
        "
      >
        <option value="" selected hidden disabled>
          Rank on Itinerary (1-5)
        </option>
        <option value="1">1</option>
        <option value="2">2</option>
        <option value="3">3</option>
        <option value="4">4</option>
        <option value="5">5</option>
      </select>
      <br /><br />
      <input
        v-model="description"
        placeholder="Description"
        style="
          background-color: #f2e8cf;
          width: 25%;
          color: black;
          border: 5px solid #f2e8cf;
          border-radius: 10px;
          box-sizing: border-box;
        "
      />
      <br /><br />
      <i style="font-family: merriweather">Location of Image:</i>
      <label class="custom-file-upload">
        <b-form-file v-model="imgfiles" />
      </label>
    </div>

    <div class="buttonHolder">
      <input
        type="button"
        value="Add"
        style="color: black; font-weight: bold"
        @click="submitForm"
      />
    </div>
  </div>
</template>

<script lang="ts">
import Navbar from "@/components/Navbar.vue";
import Vue from "vue";
import jwt_decode from "jwt-decode"

export default Vue.extend({
  name: "Itinerary",
  data() {
    return {
      fetched: false,
      indivactivity: [],
      activityName: "",
      address: "",
      locationCoord: "",
      itineraryRank: "",
      description: "",
      imgfiles: [],
    };
  },

  async fetch() {
    this.indivactivity = await this.$axios.$get(
      "http://localhost:8080/activities"
    );
    console.log(this.indivactivity);
  },

  components: { Navbar },
  methods: {
    async test() {
      const result = await this.$axios.$post(
        "http://localhost:8080/activities"
      );
      console.log(result["Test"]["category"]);
    },

    async submitForm() {
      console.log(this.username);
      console.log(this.activityName);
      console.log(this.address);
      console.log(this.locationCoord);
      console.log(this.itineraryRank);
      console.log(this.description);
      console.log(this.imgfiles);
      const formData = new FormData()
      formData.append("activityId", "1")
      formData.append("username", this.getCurrentUserName())
      formData.append("activityName", this.activityName)
      formData.append("address", this.address)
      formData.append("locationCoord", this.locationCoord)
      formData.append("rank", this.itineraryRank)
      formData.append("description", this.description)
      formData.append("imgfiles", this.imgfiles)
      const result = await this.$axios.$post(
        "http://localhost:8080/addactivity/image",
        formData,
        {
            "Content-Type": "multipart/form-data"
        }
      );
    },
    getCurrentUserName() {
        if (process.browser) {
          const token = localStorage.getItem("token")
          if (token === null) {
            return "Guest"
          } else {
            const decoded_token = jwt_decode(token)
            console.log(decoded_token)
            return decoded_token["user"]
          }
        }
      }
  },
});
</script>


<style>
.buttonHolder {
  text-align: center;
}
.addItineraryDetails {
  text-align: center;
}
input[type="file"] {
  display: none;
}
.imageFile {
  border: 1px solid black;
  display: inline-block;
  padding: 6px 12px;
  cursor: pointer;
}
input[type="button"] {
  background-color: #a7c957;
  border: none;
  color: white;
  padding: 5px 50px;
  text-decoration: none;
  margin: 2px 1px;
  cursor: pointer;
  border-radius: 15px;
  font-style: italic;
  text-align: center;
}
body {
  background-color: #fcf6e7;
}

.icons {
  text-align: center;
}

.locations {
  background-color: maroon;
  color: white;
  border: none;
  margin: 15px;
  padding: 20px 50px;
  cursor: pointer;
  font-style: italic;
  border-radius: 15px;
}

.scrollable {
  overflow-y: auto;
  white-space: nowrap;
}

.square {
  width: 100px;
  height: 100px;
}
</style>