<template>
  <div>
      <div class="HOP">
        Here's<br>
        Our<br>
        Plan<br>
      </div>
  
      <div class="loginDetails">
          <input v-model="username" type="text" placeholder="Username" style = "background-color: #F2E8CF; width: 25%;
          color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
          <br/><br/>
          <input v-model="password" type="password" placeholder="Password" style = "background-color: #F2E8CF; width: 25%;
          color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
          <br/><br/>
      </div>

      <b-alert :show="alertShown" :variant="alertVariant">
        {{ alertMsg }}
      </b-alert>

      <div class="buttonHolder">
        <b-button type='button' style="font-weight: bold;" @click="submitForm">
          Login
        </b-button>
      </div>

    <br>

    <router-link to ="/forgotpassword">
        <p align='center' style="color: black;"><i><u>Forgot your password?</u></i></p>
    </router-link><br>

    <h6 align='center' style="color:#bc4749">New user?</h6>
    <router-link to ="/registrationpage">
        <p align='center' style="color: black;"><i><u>Register here</u></i></p>
    </router-link>

  </div>
  
</template>


<script>
export default {
  name: 'LoginPage',
  data() {
    return {
      username: "",
      password: "",
      alertMsg: "",
      alertShown: false,
      alertVariant: "success"
    }
  },
  methods: {
    async submitForm() {
      console.log(this.username);
      console.log(this.password);
      const result = await this.$axios.post("http://localhost:8080/login", {
        username: this.username,
        password: this.password
      })
      if (result.data.login_result) {
        this.alertShown = true
        this.alertMsg = "Login successful"
        this.alertVariant = "success"
        if (process.client) {
          console.log(Object.keys(result.headers))
          localStorage.setItem("token", result.headers["authorization"])
        }
        window.location.href = "/main"
      } else {
        this.alertShown = true
        this.alertMsg = "Login failed"
        this.alertVariant = "danger"
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
  background-color: #A7C957;
  border: none;
  color: white;
  padding: 5px 100px;
  text-decoration: none;
  margin: 2px 1px;
  cursor: pointer;
  border-radius: 15px;
  font-style: italic;
  text-align: center; 
  }
  .loginDetails{ text-align: center; }
  .buttonHolder{ text-align: center; }

  .HOP{
  color:#BC4749;
  font-family:Bookman Old Style;
  font-size: 70px;
  padding: 50px;
  line-height:80px;
  text-align: center;
  font-style:italic;
  font-weight:bold;
}

</style>