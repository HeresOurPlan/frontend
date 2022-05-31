<template>
  <html>
    <h1 style="color:#BC4749; font-family:merriweather; font-size: 70px; padding-left: 50px;">
      <strong>
      <i>
        Here's<br>
        Our<br>
        Plan<br>
      </i>
      </strong>
    </h1>
    
    <body style="background-color:#FCF6E7;">
    <form action="" method="post">
    <style> 
      input[type=button] {
      background-color: #A7C957;
      border: none;
      color: white;
      padding: 5px 100px;
      text-decoration: none;
      margin: 2px 1px;
      cursor: pointer;
      align: center;
      border-radius: 15px;
      font-style: italic;
      text-align: center; 
    }
    </style>
    <div class="loginDetails">
        <input type="text" placeholder="Username" style = "background-color: #F2E8CF; width: 17%;
        color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
        <br/><br/>
        <input type="text" placeholder="Password" style = "background-color: #F2E8CF; width: 17%;
        color: black; border: 5px solid #F2E8CF; border-radius: 10px; box-sizing: border-box;">
        <br/><br/>
    </div>

    <style>
    .loginDetails{ text-align: center; }
    </style>

    <div class="buttonHolder">
      <input type='button' style="color: #386641; font-weight: bold;" value = "Log In">
    </div>
    <br>
    <style>.buttonHolder{ text-align: center; }</style>

    <router-link to ="">
        <p align='center' style="color: black;"><i><u>Forgot your password?</u></i></p>
    </router-link>
    </form>
    </body>
  </html>
  
</template>

<script>
export default {
  name: 'IndexPage',
}
</script>