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
                        {{fetched.name}}
                    </div>
                </b-col>
                <b-col>
                    <div class="profileCircle" style="transform: translateX(25%) translateY(5%)"></div>
                </b-col>
                </b-row>
        </b-container>

        
        <b-container fluid style="padding:22.5px;">
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Username:
                </b-col>
                <b-col class="col-lg-4">
                  <div style = "background-color: #FCF6E7; width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;font-style:italic">
                    {{fetched.username}}
                  </div>
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Password:
                </b-col>
                <b-col class="col-lg-4">
                  <div style = "background-color: #FCF6E7; width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;font-style:italic">
                    {{fetched.password}}
                  </div>
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Name:
                </b-col>
                <b-col class="col-lg-4">
                  <div style = "background-color: #FCF6E7; width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;font-style:italic">
                    {{fetched.name}}
                  </div>
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Gender:
                </b-col>
                <b-col class="col-lg-4">
                  <div style = "background-color: #FCF6E7; width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;font-style:italic">
                    {{fetched.gender}}
                  </div>
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    DoB:
                </b-col>
                <b-col class="col-lg-4">
                  <div style = "background-color: #FCF6E7; width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;font-style:italic">
                    {{fetched.dob}}
                  </div>
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Email:
                </b-col>
                <b-col class="col-lg-4">
                  <div style = "background-color: #FCF6E7; width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;font-style:italic">
                    {{fetched.email}}
                  </div>
                </b-col> 
            </b-row>
            <b-row style="padding-bottom:10px">
                <b-col class="col-lg-6" style="width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;text-align:right;font-family:Georgia, 'Times New Roman', Times, serif;font-style:italic;font-weight:bold">
                    Contact Number:
                </b-col>
                <b-col class="col-lg-4">
                  <div style = "background-color: #FCF6E7; width: 75%; color: black; border: 5px solid #FCF6E7; border-radius: 10px; box-sizing: border-box;font-style:italic">
                    {{fetched.contact}}
                  </div>
                </b-col> 
            </b-row>

            <br>
            <div class="buttonHolder">
                <router-link to ="/profileEdit">
                <input type='button' value = "Edit" style="color: black; font-weight: bold;">
                </router-link>
            </div>
        </b-container>
    </div>


</template>

<script>
import Navbar from "@/components/Navbar.vue";
import jwt_decode from "jwt-decode"

export default {
  components: { Navbar },
  data() {
    return {
      fetched: false,
      sessionUser: this.user,
      username: this.getCurrentUserName(),
      password: "",
      name: "",
      gender: "",
      dob: "",
      email: "",
      contact: "",
      imgfiles: []
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
        }

      

    }

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
        width: 90px;
        height: 90px;
        -webkit-border-radius: 45px;
        -moz-border-radius: 45px;
        border-radius: 45px;
        background: black;
        transform: translateX(-20px);
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

<!-- How to make it single page, have a layover to Confirm the edit, refer to figma -->