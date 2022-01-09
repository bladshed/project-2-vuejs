<template>
  <div id="app">
    <!-- navbar start -->
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <div class="container-fluid">
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse show" id="navbarNavAltMarkup">
          <div class="navbar-nav">
            <a v-on:click="goHomePage" class="nav-link active" aria-current="page" id="home" href="#">Home</a>
            <a v-on:click="goOutfitsPage" class="nav-link" href="#">Outfits</a>
          </div>
        </div>
      </div>
    </nav>
    <!-- navbar end -->

    <!-- page content start -->
    <div>
      <HomePage v-if="page==='home'"/>
      <OutfitsPage v-if="page==='outfits'"/>
    </div>
    <!-- page content end -->
  </div>
</template>

<script>
import HomePage from "@/components/HomePage"
import OutfitsPage from "@/components/OutfitsPage"

export default {
  name: "App",
  components: {
    HomePage, OutfitsPage
  },
  data: function() {
    return {
      page: "home"
    }
  },
  methods:{
    goHomePage: function() {
      this.page = "home"
    },
    goOutfitsPage: function() {
      this.page = "outfits"
    }
  }

}
</script>

<style>

</style>
