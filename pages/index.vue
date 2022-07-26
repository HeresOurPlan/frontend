<template>
  <div>

    <div class="HOP">
        Here's<br>
        Our<br>
        Plan<br>
    </div>
 
    
    <h4 align='center'><strong>Welcome!</strong></h4>
    <form action="" method="post">

    <div class="buttonHolder">
      <router-link to ="/login">
      <input type='button' value = "  Log In  ">
    </router-link>
    </div>
    <br>
  
    <h6 align='center'>New User?</h6>
    <div class="buttonHolder">
      <router-link to ="/registrationpage">
      <input type='submit' value = "Register">
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
    color: #386641;
    font-weight: bold;
    }

  input[type=submit] {
    background-color: #F2E8CF;
    border: none;
    color: white;
    padding: 5px 100px;
    text-decoration: none;
    margin: 2px 1px;
    cursor: pointer;
    border-radius: 15px;
    font-style: italic;
    color: #BC4749;
    font-weight: bold;
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
