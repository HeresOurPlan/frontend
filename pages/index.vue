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
 
    
    <h4 align='center'><strong>Welcome!</strong></h4>
    <form action="" method="post">

    <div class="buttonHolder">
      <router-link to ="/loginpage">
      <input type='button' style="color: #386641; font-weight: bold;" value = "Log In">
    </router-link>
    </div>
    <br>
  
    <h6 align='center'>New User?</h6>
    <div class="buttonHolder">
      <router-link to ="/registrationpage">
      <input type='submit' style="color: #BC4749; font-weight: bold;" value = "Register">
      </router-link>
    </div>

    </form>
    </div>
  
</template>


<script>
export default {
  name: 'IndexPage',
}
</script>


<style>
  body{
    background-color: #FCF6E7;
  }
  input[type=button]{
  background-color: #A7C957;
  border: none;
  color: white;
  padding: 5px 100px;
  text-decoration: none;
  margin: 2px 1px;
  cursor: pointer;
  border-radius: 15px;
  font-style: italic;
}
  input[type=submit]{
  background-color: #F2E8CF;
  border: none;
  color: white;
  padding: 5px 100px;
  text-decoration: none;
  margin: 2px 1px;
  cursor: pointer;
  border-radius: 15px;
  font-style: italic;
}
  .buttonHolder{ text-align: center; }

</style>
