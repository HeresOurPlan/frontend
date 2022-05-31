<template>
  <html>
    <h1 style="color:#BC4749;font-family:merriweather"><strong><i>Here's<br>Our<br>Plan<br><br></i></strong></h1>
    <body style="background-color:#F2E8CF;">
    <h4 align='center'><strong>Welcome!</strong></h4>
    <form action="" method="post">
    <style> 
      input[type=button], input[type=submit], input[type=reset] {
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
    <div class="buttonHolder">
      <input type='submit' value = "Log In">
    </div>
    <br>
  
    <h6 align='center'>New User?</h6>
    <div class="buttonHolder">
      <input type='submit' value = "Register">
    </div>
    <style>.buttonHolder{ text-align: center; }</style>
    </form>
    </body>
  </html>
  
</template>

<script>
export default {
  name: 'IndexPage',
}
</script>
