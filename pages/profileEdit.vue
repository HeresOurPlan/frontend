<template>
    <div>
        <Navbar />
            <h1 style="color: #BC4749; font-family: Bookman Old Style; font-size: 30px;
            padding-top: 20px; padding-left: 175px; ">
            </h1>
                <b-container fluid>
            <b-row align-h="center" align-v="center" style="height:100%">
                <b-col>
                    <div class='name'>
                        (Name)
                    </div>
                </b-col>
                <b-col>
                    <label class="custom-file-upload">
                    <input type="file"/>
                    
                    <div class="profileCircle" 
                      style="transform: translateX(25%) translateY(5%);">
                    </div>
                    <div class="profileCircle:hover">
                      <i class="fas fa-camera"></i>
                    </div>
                    </label>
                </b-col>
                </b-row>
        </b-container>

        
        <b-container fluid style="padding:10px;">
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Username:
                </b-col>
                <b-col class="col-lg-4">
                  <input v-model="username" type="text" placeholder="Username" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Password:
                </b-col>
                <b-col class="col-lg-4">
                  <input v-model="password" type="password" placeholder="Password" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Name:
                </b-col>
                <b-col class="col-lg-4">
                  <input v-model="name" type="text" placeholder="Name" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
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
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    DoB:
                </b-col>
                <b-col class="col-lg-4">
                  <input v-model="dob" type="date" placeholder="DOB" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Email:
                </b-col>
                <b-col class="col-lg-4">
                  <input v-model="email" type="text" placeholder="Email" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Contact Number:
                </b-col>
                <b-col class="col-lg-4">
                  <input v-model="contact" type="text" placeholder="Contact Number" style = "background-color: #F2E8CF; width: 75%;
                  color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
                </b-col> 
            </b-row>

            <br>
            <div class="buttonHolder">
                <router-link to ="/profilePage">
                <input type='button' value = "Edit" style="color: black; font-weight: bold;" @click="editProfile">
                </router-link>
            </div>
        </b-container>
    </div>



</template>

<script>
import Navbar from "@/components/Navbar.vue";
import Vue from 'vue'
import VTooltip from 'v-tooltip'

Vue.use(VTooltip)

export default {
  components: { Navbar },
  data() {
    return {
      fetched: false,
      editing: false,
      password: "",
      name: "",
      gender: "",
      dob: "",
      email: "",
      contact: ""
    }
  },

  fetchOnServer: false,
  async fetch() {
      const username = this.getCurrentUserName();
      this.fetched = await this.$axios.$get(
        `http://localhost:8080/user/${username}`,
        {
          password: this.password,
          name: this.name,
          gender: this.gender,
          dob: this.dob,
          email: this.email,
          contact: this.contact
        }  
      );
      console.log(this.fetched)
    },
    methods: {
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
        },

      async editProfile() {
        const username = this.getCurrentUserName();
        this.editing = await this.$axios.$put(
          `http://localhost:8080/profileEdit/${username}`,
          {
            password: this.password,
            name: this.name,
            gender: this.gender,
            dob: this.dob,
            email: this.email,
            contact: this.contact
          }
        )
      }

    }

   }
</script>

<style>
  body {
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
    cursor:pointer;
  }

  .imageFile {
      border: 1px solid black;
      display: inline-block;
      padding: 6px 12px;
      cursor: pointer;
    }

  .buttonHolder {
      text-align: center;
    }

  .profileCircle{
      position: relative;
      width: 90px;
      height: 90px;
      -webkit-border-radius: 45px;
      -moz-border-radius: 45px;
      border-radius: 45px;
      background: black;
      transform: translateX(-20px);
      cursor:pointer;
    }
  .profileCircle:hover{
      position: relative;
      width: 90px;
      height: 90px;
      -webkit-border-radius: 45px;
      -moz-border-radius: 45px;
      border-radius: 45px;
      background: linear-gradient(to bottom, black 25%,#eae5e5 100%);
      transform: translateX(-20px);
      cursor:pointer;
  }

.name{
    color:#BC4749;
    font-family:Bookman Old Style;
    font-size: 45px;
    padding-top: 3%;
    text-align: right;
    font-style: italic;
    font-weight: bold;
}

</style>