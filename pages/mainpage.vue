<template>
    <div>
    <h1 style="color: #BC4749; font-family: merriweather; font-size: 45px; 
    padding-top: 50px; padding-left: 200px;">
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

    <div class="leftImage">
        <div class="centerImage">
            <div class="rightImage">
            </div>
        </div>  
    </div>
    
    <br/><br/><br/><br/>

    <div class = "icons">
        <script src="https://kit.fontawesome.com/e0ba381a85.js" crossorigin="anonymous"></script>
            <a href ="/map"><i class="fa-solid fa-location-dot fa-3x" style="color:black;"></i></a>
            <br/><br/><br/><br/><br/><br/> 
            <a href ="/additinerary"><i class="fa-regular fa-square-plus fa-3x" style="color:black;"></i></a>
    </div>

    </div>
</template>


<script>
export default {
  name: 'MainPage',
}
</script>


<style>
    .icons{
        text-align: center;
    }
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
        margin-top: -10px;
        margin-left: -100px;
        width: 50px;
        height: 50px;
        -webkit-border-radius: 25px;
        -moz-border-radius: 25px;
        border-radius: 25px;
        background: red;
    }
    .leftImage {
        width: 200px;
        height: 200px;
        background-image: url(https://images.unsplash.com/photo-1621114957135-7f88c8447439?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1331&q=80);
        background-size: cover;
        background-position: center;
        padding-left: 100px;
        display: block;
        margin-left: 200px;
        margin-right: auto;
    }
    .centerImage {
        width: 200px;
        height: 200px;
        background-image: url(https://images.unsplash.com/photo-1532876688342-a79b7fa5c473?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1113&q=80);
        background-size: cover;
        background-position: center;
        padding-left: 100px;
        display: block;
        margin-left: 325px;
        margin-right: auto;

    }
    .rightImage{
        width: 200px;
        height: 200px;
        background-image: url(https://images.unsplash.com/photo-1635563121451-2f3cfbf26826?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=930&q=80);
        background-size: cover;
        background-position: center;
        padding-left: 100px;
        display: block;
        margin-left: 300px;
        margin-right: auto;

    }
</style>
