<template>
  <div>
    <div class="HOP">
        Here's<br>
        Our<br>
        Plan<br>
    </div>

    <div class="loginDetails">
      <input
        v-model="email"
        type="email"
        placeholder="Email"
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
        v-model="name"
        type="text"
        placeholder="Name"
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
        v-model="username"
        type="text"
        placeholder="Username"
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
        v-model="gender"
        style="
          background-color: #f2e8cf;
          width: 25%;
          color: black;
          border: 5px solid #f2e8cf;
          border-radius: 10px;
          box-sizing: border-box;
        "
      >
        <option value="" disabled hidden>Select Gender</option>
        <option value="F">Female</option>
        <option value="M">Male</option>
        <option value="O">Others</option>
      </select>
      <br /><br />
      <input
        v-model="dob"
        type="date"
        placeholder="Date of Birth"
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
        v-model="contact"
        type="tel"
        placeholder="Contact Number"
        pattern="[0-9]{8}"
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
        v-model="password"
        type="password"
        placeholder="Password"
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
        v-model="confirm_password"
        type="password"
        placeholder="Re-type Password"
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
    </div>
    <b-alert :show="alertShown" :variant="alertVariant">
      {{ alertMsg }}
    </b-alert>
    <div class="buttonHolder">
      <input
        type="button"
        value="Sign up"
        style="color: white; font-weight: bold"
        @click="submitForm"
      />
    </div>
    <br /><br>
        <h6 align='center' style="color:#bc4749">Already a user?</h6>
    <router-link to ="/login">
        <p align='center' style="color: black;"><i><u>Log in here</u></i></p><br><br>
    </router-link>
  </div>
</template>

<script>
export default {
  name: "RegistrationPage",
  data() {
    return {
      username: "",
      name: "",
      password: "",
      confirm_password: "",
      email: "",
      dob: "",
      gender: "",
      contact: "",
      alertMsg: "",
      alertShown: false,
      alertVariant: "success",
    };
  },
  methods: {
    async submitForm() {
      console.log(this.username);
      console.log(this.name);
      console.log(this.password);
      console.log(this.confirm_password);
      console.log(this.email);
      console.log(this.gender);
      console.log(this.dob);
      console.log(this.contact);
      const result = await this.$axios.$post("http://localhost:8080/register", {
        username: this.username,
        name: this.name,
        password: this.password,
        confirm_password: this.confirm_password,
        email: this.email,
        gender: this.gender,
        dob: this.dob,
        contact: this.contact,
      });

      if (result.registration_result == "wrongpassword") {
        this.alertShown = true;
        this.alertMsg = "Your passwords do not match";
        this.alertVariant = "danger";
        console.log("wrong pass");
      } else if (result.registration_result == "invalidemail") {
        this.alertShown = true;
        this.alertMsg = "Please enter a valid email";
        this.alertVariant = "danger";
      } else if (result.registration_result == "usernametaken") {
        this.alertShown = true;
        this.alertMsg = "Your username has been taken";
        this.alertVariant = "danger";
      } else if (result.registration_result == "emailtaken") {
        this.alertShown = true;
        this.alertMsg = "Your email has been taken";
        this.alertVariant = "danger";
      } else if (result.registration_result) {
        this.alertShown = true;
        this.alertMsg = "Registration successful";
        this.alertVariant = "success";
        window.location.href = "/main";
      } else {
        this.alertShown = true;
        this.alertMsg = "Login unsuccessful";
        this.alertVariant = "danger";
      }
    },
  },
};
</script>


<style>
body {
  background-color: #fcf6e7;
}
input[type="button"] {
  background-color: #a7c957;
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
.loginDetails {
  text-align: center;
}
.buttonHolder {
  color: #386641;
  text-align: center;
}
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