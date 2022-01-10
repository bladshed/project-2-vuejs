<template>
  <div id="main-div">
    <div id="background" class="d-flex flex-column">
      <!-- navbar start -->
      <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="container-fluid">
          <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse show" id="navbarNavAltMarkup">
            <div class="navbar-nav">
              <a v-on:click="goToPage($event)" class="nav-link active" aria-current="page" id="home" href="#">Home</a>
              <a v-on:click="goToPage($event)" class="nav-link" id="outfits" href="#">Outfits</a>
            </div>
          </div>
        </div>
      </nav>
      <!-- navbar end -->

      <!-- page content start -->
      <HomePage v-if="page==='home'"/>
      <OutfitsPage v-if="page==='outfits'"/>
      <!-- page content end -->
    </div>
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
    goToPage: function(event) {
      let pageId = event.currentTarget.id;
      // set page value
      this.page = pageId;
      // remove and set active page
      document.querySelector(".active").classList.remove("active");
      document.querySelector(`#${pageId}`).classList.add("active");
    }
  }

}
</script>

<style>
#main-div {
  height: 100vh;
  background-image: url("./images/fashion-background.jpg");
  background-size: cover;
}
#background {
  height: 100%;
  width: 100%;
  background-color: rgba(0, 0, 0, 0.5);
}
.navbar-light .navbar-nav .show > .nav-link, .navbar-light .navbar-nav .nav-link.active {
    font-weight: bold;
}
</style>
