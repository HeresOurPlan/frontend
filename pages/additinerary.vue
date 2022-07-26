<template>
  <div>
    <Navbar />

    <div class='myheading'>
        <b><i> Add Your Activity </i></b>
      </div><br>

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
        v-model="postal"
        placeholder="Postal Code"
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
        v-model="opening_hours"
        placeholder="Opening Hours (e.g. 2359)"
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
        v-model="closing_hours"
        placeholder="Closing Hours (e.g. 2359)"
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
        v-model="prior_booking"
        placeholder="Prior Booking"
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
          Prior Booking
        </option>
        <option value="Yes">Yes</option>
        <option value="No">No</option>
      </select>
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
        v-model="category"
        placeholder="Category"
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
        v-model="website"
        placeholder="Website"
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
        v-model="price_point"
        placeholder="Price Point"
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
      <i style="font-family: Bookman Old Style">Image of Location:</i>
      <br />
          <b-form-file style="width: 50%" placeholder="Choose a file" class="text-left" v-model="imgfiles"/>
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
      itineraryRank: "",
      website: "",
      closing_hours: "",
      opening_hours: "",
      price_point: "",
      category: "",
      postal:"",
      prior_booking:"",
      imgfiles: [],
    };
  },

fetchOnServer: false,

  async mounted() {
    this.indivactivity = await this.$axios.$get(
      "http://localhost:8080/activities"
    );
    console.log(this.indivactivity);
    if (sessionStorage.getItem('address') !== null) {
      this.address = sessionStorage.getItem('address')
      sessionStorage.removeItem('address')
    }
  },

  components: { Navbar },
  methods: {
    async submitForm() {
      console.log(this.activityName);
      console.log(this.address);
      console.log(this.itineraryRank);
      console.log(this.website);
      console.log(this.category);
      console.log(this.opening_hours);
      console.log(this.closing_hours);
      console.log(this.prior_booking)
      console.log(this.imgfiles);
      const username = this.getCurrentUserName();
      // const formData = new FormData()
      // formData.append("activityId", "1")
      // formData.append("username", this.getCurrentUserName())
      // formData.append("activityName", this.activityName)
      // formData.append("address", this.address)
      // formData.append("locationCoord", this.locationCoord)
      // formData.append("rank", this.itineraryRank)
      // formData.append("description", this.description)
      // formData.append("imgfiles", this.imgfiles)
      
      const new_activity = await this.$axios.$post(
        `http://localhost:8080/activity`,
        {
          activity_name: this.activityName,
          postal: this.postal,
          closing_hours: this.closing_hours,
          address: this.address,
          locationCoord: this.locationCoord,
          opening_hours: this.opening_hours,
          prior_booking: this.prior_booking,
          price_point: this.price_point,
          website: this.website,
          category: this.category,

        }
      );
      const new_useractivity = await this.$axios.$post(
        `http://localhost:8080/useractivities`,
        {
          username: username,
          activity: new_activity.id,
          itineraryRank: this.itineraryRank,
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

.myheading {
        color: #bc4749;
        font-family: Bookman Old Style;
        font-size: 50px;
        padding-top: 20px;
        text-align: center;
}

</style>