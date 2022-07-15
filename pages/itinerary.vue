<template>
    <div>
    <Navbar />
    <h1 style="color: #BC4749; font-family: merriweather; font-size: 50px; 
    padding-top: 20px; padding-left: 2%; text-align: center">
        <strong>
        <i>
            Itinerary
        </i>
        </strong>
    </h1>

    <b-container-fluid>
        <div class="row-fluid scrollable" style="width:100%; height:100%" @click="test">
            <details class="locations" v-for="shop in shops" :key="shop">
                <summary>&emsp;<img class="square" :src="shop.image">&ensp;
                <!-- <i class="fa-solid fa-ellipsis-vertical fa-2x"></i> -->
                {{ shop.text }}
                </summary>
                <div class='information'>
                if click alr show this</div>
            </details>
        </div>
    </b-container-fluid>


    <br/><br/><br/><br/>

    <div class = "icons">
        <a href ="/additinerary"><i class="fa-regular fa-square-plus fa-3x" style="color:black;"></i></a>
    </div>


    </div>
    

</template>

<script>
    import Navbar from "@/components/Navbar.vue";

    export default {
        
    name: 'Itinerary',
    data() {
        return {
        shops: [
            {
                "image": "https://images.unsplash.com/photo-1623156346149-d5cec8b29818?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1931&q=80",
                "text":  "McDonald's",
            },
            {
                "image": "https://static.mothership.sg/1/2021/07/mos-burger-closed.jpeg",
                "text":  "Mos Burger",
            },
            {
                "image": "https://cdn.britannica.com/08/193908-050-66767D57/view-Subway-restaurant-Bangkok-Thailand.jpg",
                "text":  "Subway",
            },
            {
                "image": "https://images.unsplash.com/photo-1532876688342-a79b7fa5c473?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1113&q=80",
                "text":  "McDonald's",
            },
            {
                "image": "https://images.unsplash.com/photo-1511882150382-421056c89033?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1742&q=80",
                "text":  "Arcade",
            },
        ],
        fetched: false,
        indivactivity: []
        }
    },

    fetchOnServer: false,
    async fetch() {
        this.indivactivity = await this.$axios.$get("http://localhost:8080/activities");
        console.log(this.indivactivity)
    },

    components: { Navbar },
    methods: {
    async test() {
      const result = await this.$axios.$post("http://localhost:8080/activities")
      console.log(result['Test']['category'])

    }
  }
}


    
</script>

<style>
    body{
        background-color: #FCF6E7;
    }

    .icons{
        text-align: center;
    }

    .locations {
        background-color: maroon;
        color: white;
        border: none;
        margin: 15px;
        padding: 20px 50px;
        cursor: pointer;
        font-style: italic;
        border-radius: 15px;
    }

    .information {
        background-color:#BC4749;
        color:white;
        font-style:normal;
        padding-top:10px;
        padding-bottom:10px;
        padding-left:30px;
        padding-right:30px;
        margin-top:20px;
        margin-left:27.5px;
        margin-right:40px;
        border-radius:5px;
        overflow:scroll;
    }

    .scrollable {
        overflow-y: auto;
        white-space: nowrap;
    }

    .square {
        width: 100px;
        height: 100px;
    }
</style>