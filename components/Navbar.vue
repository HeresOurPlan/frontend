<template>
    <b-navbar toggleable="lg" type="dark" variant="dark">
      
    <b-navbar-brand href="#">Here's Our Plan</b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav>
        <b-nav-item href="/main">Home</b-nav-item>
      </b-navbar-nav>

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">
        <b-nav-form>
          <b-form-input size="sm" class="mr-sm-2" placeholder="Search Locations"></b-form-input>
          <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
        </b-nav-form>

        <b-nav-item-dropdown text="Where to?" class="ml-2">
          <b-dropdown-item href="/itinerary">Itinerary</b-dropdown-item>
          <b-dropdown-item href="#">Add Activity</b-dropdown-item>
          <b-dropdown-item href="#">Map</b-dropdown-item>
        </b-nav-item-dropdown>

        <!-- <b-nav-item-dropdown right> 
          <template #button-content>
            <em><div class = "circle"></div><div class="profileCircle"></div></em>
          </template>
          <b-dropdown-item href="#">Profile</b-dropdown-item>
          <b-dropdown-item href="#">Sign Out</b-dropdown-item>
        </b-nav-item-dropdown> -->

          <!-- <b-navbar-nav> -->
            <b-nav-item class = "circle"></b-nav-item>
            <b-nav-item href="#" class = "profileCircle"></b-nav-item>
          <!-- </b-navbar-nav> -->
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</template>

<script>
export default {
    name: 'Navbar',
}
</script>

<style scoped>
.navbar.navbar-dark.bg-dark{
    background-color: #b6ad90!important;
}

.profileCircle{
        position: relative;
        /* top: 100%;
        left: 100%; */
        /* margin-top:-40px;
        margin-left:-60px; */
        width: 40px;
        height: 40px;
        -webkit-border-radius: 20px;
        -moz-border-radius: 20px;
        border-radius: 20px;
        background: black;
        transform: translateX(-20px);
}
.circle {
        position: relative;
        /* top: 100%;
        left: 100%; */
        /* margin-top: -40px;
        margin-left: -10px; */
        width: 40px;
        height: 40px;
        -webkit-border-radius: 20px;
        -moz-border-radius: 20px;
        border-radius: 20px;
        background: red;
        transform: translateX(30px);
}
</style>