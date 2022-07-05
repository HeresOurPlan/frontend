<template>
    <div>
        <Navbar />
            <h1 style="color: #BC4749; font-family: merriweather; font-size: 30px;
            padding-top: 20px; padding-left: 175px; ">
            </h1>
        <b-container fluid>
            <b-row>
            <b-col>
        <h1 style="color:#BC4749; font-family:merriweather; font-size: 70px; padding-left: 50px; text-align: left">
        <strong>
                <i>
                    Here's<br>
                    Our<br>
                    Plan<br>
                </i>
            </strong>
            </h1>
            </b-col>
            <b-col>
                <div class="profileCircle"></div>
            </b-col>
            </b-row>
        </b-container>

        
        <b-container fluid>
            <div class="profileDetails">
                <i style = "font-family: merriweather;">Username:</i>
                <br/><br/>
                <i style = "font-family: merriweather;">Password:</i>
                <br/><br/>
                <i style = "font-family: merriweather;">Name:</i>
                <br/><br/>
                <i style = "font-family: merriweather;">Gender:</i>
                <br/><br/>
                <i style = "font-family: merriweather;">DOB:</i>
                <br/><br/>
                <i style = "font-family: merriweather;">Email:</i>
                <br/><br/>
                <i style = "font-family: merriweather;">Contact Num:</i>
                <br/><br/>
              <!-- placeholder in input should be current values in DB -->
              <!-- cannot Align the input names in one column -->
            </div>
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
        width: 40px;
        height: 40px;
        -webkit-border-radius: 20px;
        -moz-border-radius: 20px;
        border-radius: 20px;
        background: black;
        transform: translateX(-20px);
}
</style>

<!-- How to make it single page, have a layover to Confirm the edit, refer to figma -->