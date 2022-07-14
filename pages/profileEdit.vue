<template>
    <div>
        <Navbar />
            <h1 style="color: #BC4749; font-family: merriweather; font-size: 30px;
            padding-top: 20px; padding-left: 175px; ">
            </h1>
        
        <b-container>
            <div class="profileDetails">
                <i style = "font-family: merriweather;">Username:</i>
                  <input v-model="username" type="text" placeholder="Username" style = "background-color: #F2E8CF; width: 25%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                  <br/><br/>
                <i style = "font-family: merriweather;">Password:</i>
                  <input v-model="password" type="password" placeholder="Password" style = "background-color: #F2E8CF; width: 25%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                  <br/><br/>
                <i style = "font-family: merriweather;">Name:</i>
                  <input v-model="name" type="text" placeholder="Name" style = "background-color: #F2E8CF; width: 25%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                  <br/><br/>
                <i style = "font-family: merriweather;">Gender:</i>
                  <select v-model="gender" type="text" style = "background-color: #F2E8CF; width: 25%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                      <option value="" disabled hidden>Select Gender</option>
                      <option value="Female">Female</option>
                      <option value="Male">Male</option>
                      <option value="Others">Others</option>
                  </select>
                  <br/><br/>
                <i style = "font-family: merriweather;">DOB:</i>
                  <input v-model="dob" type="text" placeholder="DOB" style = "background-color: #F2E8CF; width: 25%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                  <br/><br/>
                <i style = "font-family: merriweather;">Email:</i>
                  <input v-model="email" type="text" placeholder="Email" style = "background-color: #F2E8CF; width: 25%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                  <br/><br/>
                <i style = "font-family: merriweather;">Contact Num:</i>
                  <input v-model="contact" type="text" placeholder="Contact Number" style = "background-color: #F2E8CF; width: 25%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                  <br/><br/>
              <!-- placeholder in input should be current values in DB -->
              <!-- cannot Align the input names in one column -->
            </div>
            <div class="buttonHolder">
              <input type='button' value = "Edit" style="color: black; font-weight: bold;" @click="submitForm">
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
    this.fetched = await this.$axios.$get("http://localhost:8080/user");
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
</style>

<!-- How to make it single page, have a layover to Confirm the edit, refer to figma -->