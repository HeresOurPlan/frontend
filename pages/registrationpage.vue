<template>
  <div>
    <h1 style="color:#BC4749; font-family:merriweather; font-size: 70px; padding-left: 50px;">
      <strong>
      <i>
        Here's<br>
        Our<br>
        Plan<br>
      </i>
      </strong>
    </h1>
  
    <div class="loginDetails">
        <input v-model="email" type="email" placeholder="Email" style = "background-color: #F2E8CF; width: 25%;
        color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
        <br/><br/>
        <input v-model="username" type="text" placeholder="Username" style = "background-color: #F2E8CF; width: 25%;
        color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
        <br/><br/>
        <select v-model="gender" style = "background-color: #F2E8CF; width: 25%;
        color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
          <option value="default" selected="selected">Select Gender</option>
          <option value="Female">Female</option>
          <option value="Male">Male</option>
          <option value="Others">Others</option>
        </select>
        <br/><br/>
        <input v-model="dob" type="date" placeholder="Date of Birth" style = "background-color: #F2E8CF; width: 25%;
        color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
        <br/><br/>
        <input v-model="contact" type="tel" placeholder="Contact Number" pattern="[0-9]{8}" style = "background-color: #F2E8CF; width: 25%;
        color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
        <br/><br/>
        <input v-model="password" type="password" placeholder="Password" style = "background-color: #F2E8CF; width: 25%;
        color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
        <br/><br/>
        <input v-model="confirm_password" type="password" placeholder="Re-type Password" style = "background-color: #F2E8CF; width: 25%;
        color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
        <br/><br/>
    </div>

    <div class="buttonHolder">
      <input type='button' value = "Sign up" style="color: black; font-weight: bold;" @click="submitForm">
    </div>
    <br>
    </div>
  
</template>


<!-- <script>
export default {
  name: 'RegistrationPage',
}
</script> -->

<script>
export default {
  name: 'RegistrationPage',
  data() {
    return {
      username: "",
      password: "",
      confirm_password: "",
      email: "",
      dob: "",
      gender: "",
      contact: "",
      alertMsg: "",
      alertShown: false,
      alertVariant: "success"
    }
  },
  methods: {
    async submitForm() {
      console.log(this.username);
      console.log(this.password);
      console.log(this.confirm_password);
      console.log(this.email);
      console.log(this.gender);
      console.log(this.dob);
      console.log(this.contact);
      const result = await this.$axios.$post("http://localhost:5000/register", {
        username: this.username,
        password: this.password,
        confirm_password: this.confirm_password,
        email: this.email,
        gender: this.gender,
        dob: this.dob,
        contact: this.contact
      })
      if (result.login_result) {
        this.alertShown = true
        this.alertMsg = "Login successful"
        this.alertVariant = "success"
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
  .loginDetails{
      text-align: center;
    }
  .buttonHolder{
      color: #386641;
      text-align: center;
    }
</style>