<template>
    <div>
        <Navbar />

        <b-container fluid style="padding-top:30px;height:150px;padding-bottom:50px">
            <b-row align-h="center">
                <b-col cols="6">
                    <h1 style="color:#BC4749;
                               font-family:merriweather;
                               font-size: 70px;
                               padding-right: 50px;
                               text-align: left;
                               font-style: italic;
                               font-weight: bold;
                               text-align: right">
                        (Name)
                    </h1>
                </b-col>
                <b-col cols="4">
                    <div class="profileCircle" style="transform: translateX(50%);"></div>
                </b-col>
                </b-row>
        </b-container>

        
        <b-container fluid style="padding-bottom:90px;">
            <b-row style="padding-bottom:10px">
                <b-col style="text-align:right;font-family: Georgia;font-style:italic;font-weight:bold">
                    Username:
                </b-col>
                <b-col>
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col style="text-align:right;font-family: Georgia;font-style:italic;font-weight:bold">
                    Password:
                </b-col>
                <b-col>
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col style="text-align:right;font-family: Georgia;font-style:italic;font-weight:bold">
                    Name:
                </b-col>
                <b-col>
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col style="text-align:right;font-family: Georgia;font-style:italic;font-weight:bold">
                    Gender:
                </b-col>
                <b-col>
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col style="text-align:right;font-family: Georgia;font-style:italic;font-weight:bold">
                    DoB:
                </b-col>
                <b-col>
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col style="text-align:right;font-family: Georgia;font-style:italic;font-weight:bold">
                    Email:
                </b-col>
                <b-col>
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col style="text-align:right;font-family: Georgia;font-style:italic;font-weight:bold">
                    Contact Num:
                </b-col>
                <b-col>
                </b-col> 
            </b-row>
              <!-- placeholder in input should be current values in DB -->
              <!-- cannot Align the input names in one column -->
              

            <br><br>
            <div class="buttonHolder">
                <router-link to ="/profileEdit">
                <input type='button' value = "Edit" style="color: black; font-weight: bold;" @click="submitForm">
                </router-link>
            </div>
            <!-- cannot get edit text to change to white. -->
        </b-container>
    </div>


</template>

<script>
import Navbar from "@/components/Navbar.vue";

export default {
  components: { Navbar },
  data() {
    return {
      fetched: false
    }
  },
  fetchOnServer: false,

    async fetch() {
    this.fetched = await this.$axios.$get("http://localhost:5000/activities");
    console.log(this.fetched)
    },
   }
</script>

<style>
  body{
    background-color: #FCF6E7;
  }
  input[type=button] {
  background-color: #BC4749;
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
  .profileDetails{ text-align: center; }
  .buttonHolder{ text-align: center; }

.profileCircle{
        position: relative;
        /* top: 100%;
        left: 100%; */
        /* margin-top:-40px;
        margin-left:-60px; */
        width: 90px;
        height: 90px;
        -webkit-border-radius: 45px;
        -moz-border-radius: 45px;
        border-radius: 45px;
        background: black;
        transform: translateX(-20px);
}
</style>

<!-- How to make it single page, have a layover to Confirm the edit, refer to figma -->