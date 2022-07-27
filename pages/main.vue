<template>
    <div>
    <Navbar />
    <br>
    <h1 style="color: #BC4749; font-family: Bookman Old Style; font-size: 31px; 
    padding-top: 1%; padding-left: 12%; ">
      <strong>
      <i>
        Last Viewed Activities
      </i>
      </strong>
    </h1>

    <b-container>
        <div class="row-fluid scrollable" style="height:250px">
            <div style="display:inline" v-for="imgUrl in images" :key="imgUrl">
                <a href='' onclick="document.getElementById('modal1').style.display='block'" target="iframe_modal" ><img class="square" :src="imgUrl"></a>  
                
            </div>
        </div>

        <div id="modal1" class="modal">
            <span onclick="document.getElementById('modal1').style.display='none'; document.getElementById('iframe1').src =''" class="">&times;</span>
            <iframe id="iframe1" height="300px" width="100%" src="" name="iframe_modal"></iframe>
        </div>

    </b-container>
    
    <br/><br/>

    <div class = "icons">
        <a href ="/map"><i class="fa-solid fa-location-dot fa-3x" style="color:black;"></i></a>
        <br/><br/><br/><br/><br/>
        <a href ="/new_loc_map"><i class="fa-regular fa-square-plus fa-3x" style="color:black;"></i></a>
    </div>
    <br/><br/><br/><br/><br/>
    </div>
</template>


<script>
import Navbar from "@/components/Navbar.vue";

export default {
    name: 'MainPage',
    data() {
        return {
        images: [
            "https://images.unsplash.com/photo-1621114957135-7f88c8447439?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1331&q=80",
            "https://images.unsplash.com/photo-1532876688342-a79b7fa5c473?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1113&q=80",
            "https://images.unsplash.com/photo-1635563121451-2f3cfbf26826?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=930&q=80",
            "https://images.unsplash.com/photo-1635563121451-2f3cfbf26826?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=930&q=80",
            "https://images.unsplash.com/photo-1635563121451-2f3cfbf26826?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=930&q=80",
            "https://images.unsplash.com/photo-1635563121451-2f3cfbf26826?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=930&q=80",
            "https://images.unsplash.com/photo-1635563121451-2f3cfbf26826?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=930&q=80"
        ]
        }
    },
    components: { Navbar }
}
</script>


<style>
    .icons{
        text-align: center;
    }
    body{
        background-color: #FCF6E7;
    }

    .scrollable {
        overflow-x: auto;
        white-space: nowrap;
    }

    .square {
        width: 200px;
        height: 200px;
    }

    .modal {
        padding-top: 20%;
        padding-bottom: 30%;
        padding-left: 20%;
        padding-right: 20%;
        position:fixed;
        width:80%;
        height:50%;
        overflow:scroll;
        white-space: nowrap;
        background-color:rgb(0,0,0);
        background-color:rgba(0,0,0,0.4)
    }

</style>
