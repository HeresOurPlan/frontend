<template>
  <div>
    <div class="HOP">
        Here's<br>
        Our<br>
        Plan<br>
    </div>
  
    <div class="loginDetails">
        <input type="text" placeholder="Username" style = "background-color: #F2E8CF; width: 25%;
        color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
        <br/><br/>
        <input type="text" placeholder="Email" style = "background-color: #F2E8CF; width: 25%;
        color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
        <br/><br/>
    </div>

    <div class="buttonHolder">
        <router-link to="/login">
        <input type='button' style="color: #386641; font-weight: bold;" value = "Request New Password">
        </router-link>
    </div>
    <br>

  </div>
  
</template>


<script>
export default {
  name: 'LoginPage',
}
</script>


<style>
  body {
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

  .loginDetails {
    text-align: center;
    }

  .buttonHolder {
    text-align: center;
    }

  .HOP {
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