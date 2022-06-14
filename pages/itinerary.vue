<template>
    <div>
    <Navbar />
    <h1 style="color: #BC4749; font-family: merriweather; font-size: 50px; 
    padding-top: 20px; padding-left: 175px; ">
        <strong>
        <i>
            Itinerary
        </i>
        </strong>
    </h1>

    <b-container>
        <div class="row-fluid scrollable" style="width:1000px; height:500px">
            <div class="locations" v-for="imgUrl in images" :key="imgUrl">
                <img class="square" :src="imgUrl">
                <i class="fa-solid fa-ellipsis-vertical fa-2x"></i>

            </div>
        </div>
    </b-container>


    </div>
    

</template>

<script>
    import Navbar from "@/components/Navbar.vue";

    export default {
    name: 'Itinerary',
    data() {
        return {
        images: [
            "https://images.unsplash.com/photo-1623156346149-d5cec8b29818?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1931&q=80", 
            "https://images.unsplash.com/photo-1635563121451-2f3cfbf26826?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=930&q=80",
            "https://static.mothership.sg/1/2021/07/mos-burger-closed.jpeg",
            "https://cdn.britannica.com/08/193908-050-66767D57/view-Subway-restaurant-Bangkok-Thailand.jpg",
            "https://images.unsplash.com/photo-1532876688342-a79b7fa5c473?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1113&q=80",
            "https://images.unsplash.com/photo-1635563121451-2f3cfbf26826?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=930&q=80",
            "https://images.unsplash.com/photo-1635563121451-2f3cfbf26826?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=930&q=80",
            "https://images.unsplash.com/photo-1621114957135-7f88c8447439?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1331&q=80",
            "https://images.unsplash.com/photo-1532876688342-a79b7fa5c473?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1113&q=80",
            "https://images.unsplash.com/photo-1635563121451-2f3cfbf26826?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=930&q=80",
            "https://images.unsplash.com/photo-1635563121451-2f3cfbf26826?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=930&q=80"
        ],
        texts: [
            "McDonald's",
            "Burger King",
            "Mos Burger",
            "Subway"
        ]
        }
    },
    components: { Navbar },
}


    
</script>

<style>
    body{
        background-color: #FCF6E7;
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

    .scrollable {
        overflow-y: auto;
        white-space: nowrap;
    }

    .square {
        width: 100px;
        height: 100px;
    }
</style>