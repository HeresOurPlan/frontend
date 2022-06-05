<template>
    <div>
    <h1 style="color:#BC4749; font-family:merriweather; font-size: 30px; 
    padding-top: 50px; padding-left: 50px;">
      <strong>
      <i>
        Last Viewed Activities
      </i>
      </strong>
    </h1>

    <div class="circle">
    </div>
    <div class="profileCircle"> 
    </div>

    <div class="centerImage">
    </div>
    <div class="leftImage">
    </div>
    
    </div>
</template>


<script>
export default {
  name: 'MainPage',
}
</script>


<style>
    body{
        background-color: #FCF6E7;
    }
    .profileCircle{
        position: relative;
        top: 100%;
        left: 100%;
        margin-top:-50px;
        margin-left:-110px;
        width: 50px;
        height: 50px;
        -webkit-border-radius: 25px;
        -moz-border-radius: 25px;
        border-radius: 25px;
        background: black;
    }
    .circle {
        position: relative;
        top: 100%;
        left: 100%;
        margin-top:-10px;
        margin-left:-100px;
        width: 50px;
        height: 50px;
        -webkit-border-radius: 25px;
        -moz-border-radius: 25px;
        border-radius: 25px;
        background: red;
    }
    .leftImage {
        width:100px;
        height:100px;
        background-image: url(https://images.unsplash.com/photo-1621114957135-7f88c8447439?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1331&q=80);
        background-size:cover;
        background-position:center;
        padding-left: 100px;
        display: block;
        text-align: left;
    }
    .centerImage {
        width:100px;
        height:100px;
        background-image: url(https://images.unsplash.com/photo-1532876688342-a79b7fa5c473?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1113&q=80);
        background-size:cover;
        background-position:center;
        padding-left: 100px;
        display: block;
        margin-left: auto;
        margin-right: auto;
    }
</style>
