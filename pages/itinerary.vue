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
            <details class="locations" v-for="(shop,index) in shops" :key="shop">
                <summary>&emsp;<img class="square" :src="shop.image">&ensp;
                <span style="height:100px"><b>{{index+1}}. {{ shop.text }}</b> @
                <i>{{shop.location}}, S({{shop.postal}})</i></span>
                </summary>
                <div class='information'>
                    <!--<b>Location:</b> {{shop.location}}, S({{shop.postal}})-->
                    <b>Opening/Closing Hours:</b> {{shop.opening_hours}}-{{shop.closing_hours}}<br>
                </div>
            </details>

            <!--
            <details class="locations" v-for="(shop,index) in shops" :key="shop">
            <summary>
                <b-container fluid>
                    <b-row>
                        <b-col cols="2">
                            &emsp;<img class="square" :src="shop.image">
                        </b-col>

                        <b-col cols="8">
                            <b>{{index+1}}. {{ shop.text }}</b> @
                            <i>{{shop.location}}, S({{shop.postal}})</i>
                            
                        </b-col>
                    </b-row>
                </b-container>
            </summary>
                            
            <div class='information'>
                <b>Opening/Closing Hours:</b> {{shop.opening_hours}}-{{shop.closing_hours}}<br>
            </div>
                
            </details>

            THIS ACTUALLY looks weirder than the initial one dskfjhsdkjf now everything is completely out of whack... 
            still struggling to make the words adjustible....

            if just wna make it less ugly then ig can just get rid of the location in the title Ahaha...

            -->


        </div>
    </b-container-fluid>


    <br/><br/><br/><br/>

    <div class = "icons">
        <a href ="/additinerary"><i class="fa-regular fa-square-plus fa-3x" style="color:black;"></i></a>
    </div>

    <br/><br/><br/><br/>    <br/>
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
                "location": "100 Charming Avenue",
                "postal":'888888',
                "opening_hours":'10am',
                "closing_hours":'5pm',
                "category":'F&B'
            },
            {
                "image": "https://static.mothership.sg/1/2021/07/mos-burger-closed.jpeg",
                "text":  "Mos Burger",
                "location": "100 Charming Avenue",
                "postal":'888888',
                "opening_hours":'10am',
                "closing_hours":'5pm',
                "category":'F&B'
            },
            {
                "image": "https://cdn.britannica.com/08/193908-050-66767D57/view-Subway-restaurant-Bangkok-Thailand.jpg",
                "text":  "Subway",
                "location": "100 Charming Avenue",
                "postal":'888888',
                "opening_hours":'10am',
                "closing_hours":'5pm',
                "category":'F&B'
            },
            {
                "image": "https://images.unsplash.com/photo-1532876688342-a79b7fa5c473?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1113&q=80",
                "text":  "McDonald's",
                "location": "100 Charming Avenue",
                "postal":'888888',
                "opening_hours":'10am',
                "closing_hours":'5pm',
                "category":'F&B'
            },
            {
                "image": "https://images.unsplash.com/photo-1511882150382-421056c89033?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1742&q=80",
                "text":  "Arcade",
                "location": "100 Charming Avenue",
                "postal":'888888',
                "opening_hours":'10am',
                "closing_hours":'5pm',
                "category":'F&B'
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
        border-radius: 15px;
        white-space:initial;
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
        white-space: initial;
        cursor:auto;
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