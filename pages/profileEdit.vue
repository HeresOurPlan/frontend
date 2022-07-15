<template>
    <div>
        <Navbar />
            <h1 style="color: #BC4749; font-family: merriweather; font-size: 30px;
            padding-top: 20px; padding-left: 175px; ">
            </h1>
                <b-container fluid>
            <b-row align-h="center" align-v="center" style="height:100%">
                <b-col>
                    <h1 style="color:#BC4749;
                        font-family:merriweather;
                        font-size: 45px;
                        padding-top: 3%;
                        text-align: right;
                        font-style: italic;
                        font-weight: bold;">
                        Zachary Lian
                    </h1>
                </b-col>
                <b-col>
                    <label class="custom-file-upload">
                    <input type="file"/>
                    <div class="profileCircle" style="transform: translateX(25%) translateY(5%);">
                    </div>
                    </label>
                </b-col>
                </b-row>
        </b-container>

        
        <b-container fluid style="padding-bottom:90px; padding-top:3%">
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="text-align:right;font-family: Georgia;font-style:italic;font-weight:bold;">
                    Username:
                </b-col>
                <b-col class="col-lg-4">
                  <input v-model="username" type="text" placeholder="Username" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="text-align:right;font-family: Georgia;font-style:italic;font-weight:bold">
                    Password:
                </b-col>
                <b-col class="col-lg-4">
                  <input v-model="password" type="text" placeholder="Password" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="text-align:right;font-family: Georgia;font-style:italic;font-weight:bold">
                    Name:
                </b-col>
                <b-col class="col-lg-4">
                  <input v-model="name" type="text" placeholder="Name" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="text-align:right;font-family: Georgia;font-style:italic;font-weight:bold">
                    Gender:
                </b-col>
                <b-col class="col-lg-4">
                  <select v-model="gender" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                      <option value="undefined" disabled hidden>Select Gender</option>
                      <option value="Female">Female</option>
                      <option value="Male">Male</option>
                      <option value="Others">Others</option>
                  </select>
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="text-align:right;font-family: Georgia;font-style:italic;font-weight:bold">
                    DoB:
                </b-col>
                <b-col class="col-lg-4">
                  <input v-model="dob" type="date" placeholder="DOB" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="text-align:right;font-family: Georgia;font-style:italic;font-weight:bold">
                    Email:
                </b-col>
                <b-col class="col-lg-4">
                  <input v-model="email" type="text" placeholder="Email" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="text-align:right;font-family: Georgia;font-style:italic;font-weight:bold">
                    Contact Num:
                </b-col>
                <b-col class="col-lg-4">
                  <input v-model="contact" type="text" placeholder="Contact Number" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                </b-col> 
            </b-row>

            <br><br>
            <div class="buttonHolder">
                <router-link to ="/profileEdit">
                <input type='button' value = "Edit" style="color: black; font-weight: bold;" @click="submitForm">
                </router-link>
            </div>
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
  input[type="file"] {
  display: none;
  }
  .imageFile {
      border: 1px solid black;
      display: inline-block;
      padding: 6px 12px;
      cursor: pointer;
    }
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