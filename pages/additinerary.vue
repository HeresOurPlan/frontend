<template>
  <div>
    <Navbar />

    <div class='myheading'>
        <b><i>Add Your Activity</i></b>
      </div><br>

    <div class="addItineraryDetails">
        <b-container fluid style="padding:10px;">
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Activity Name:
                </b-col>
                <b-col class="col-lg-4">
                  <input v-model="activityName" type="text" placeholder="Activity Name" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Address:
                </b-col>
                <b-col class="col-lg-4">
                  <input v-model="address" type="text" placeholder="Address" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Postal Code:
                </b-col>
                <b-col class="col-lg-4">
                  <input v-model="postal" type="text" placeholder="Postal Code" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Opening Hours (e.g. 00:00:00):
                </b-col>
                <b-col class="col-lg-4">
                  <input v-model="opening_hours" type="text" placeholder="Opening Hours" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Closing Hours (e.g. 23:59:59):
                </b-col>
                <b-col class="col-lg-4">
                  <input v-model="closing_hours" type="text" placeholder="Closing Hours" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Prior Booking Needed?
                </b-col>
                <b-col class="col-lg-4">
                  <select v-model="prior_booking" type="text" placeholder="Email" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                  <option value="" selected hidden disabled>Prior Booking Needed?</option>
                  <option value="Y">Yes</option>
                  <option value="N">No</option>
                  </select>
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Rank on Itinerary:
                </b-col>
                <b-col class="col-lg-4">
                  <input v-model="itineraryRank" type="number" placeholder="1-5" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Category:
                </b-col>
                <b-col class="col-lg-4">
                  <input v-model="category" type="text" placeholder="Category" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Website URL:
                </b-col>
                <b-col class="col-lg-4">
                  <input v-model="website" type="text" placeholder="Website URL" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Price Point:
                </b-col>
                <b-col class="col-lg-4">
                  <input v-model="price_point" type="text" placeholder="Price Point" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Location of Image:
                </b-col>
                <b-col class="col-lg-4">
                  <b-form-file style="width: 75%;text-align:left" placeholder="Choose a file" v-model="imgfiles"/>
                  <br><br>
                </b-col> 
            </b-row>
          <b-row><b-col class="col-lg-12">
          <div class="buttonHolder">
            <a href="/itinerary"><input
              type="button"
              value="Add"
              style="color: black; font-weight: bold"
              @click="submitForm"
            /></a>
          </div>
          </b-col></b-row>
        </b-container>
        
<b-container-fluid></b-container-fluid>

  </div><br><br><br><br>
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