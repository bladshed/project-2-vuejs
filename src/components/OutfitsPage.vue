<template>
  <div id="outfits-div">
    <div id="background">
      <main class="d-flex py-3">
        <!-- search column start -->
        <div class="col-2" id="search-div">
          <div class="p-3">
            <button class="btn-sm btn-primary m-3 col-10" id="add-new-btn">
              ADD NEW OUTFIT
            </button>
            <hr />
            <hr />

            <input id="search-input" class="form-control" type="text" placeholder="search input"/>
            <hr />
            <label>Types</label>
            <div class="form-check">
              <input class="form-check-input" type="checkbox" value="formal" />
              <label class="form-check-label" for="flexCheckDefault">
                Formal
              </label>
            </div>
            <div class="form-check">
              <input class="form-check-input" type="checkbox" value="casual" />
              <label class="form-check-label" for="flexCheckDefault">
                Casual
              </label>
            </div>
            <div class="form-check">
              <input
                class="form-check-input"
                type="checkbox"
                value="streetwear"
              />
              <label class="form-check-label" for="flexCheckDefault">
                Streetwear
              </label>
            </div>

            <hr />
            <label>Genders</label>
            <div class="form-check">
              <input class="form-check-input" type="checkbox" value="male" />
              <label class="form-check-label" for="flexCheckDefault">
                Male
              </label>
            </div>
            <div class="form-check">
              <input class="form-check-input" type="checkbox" value="female" />
              <label class="form-check-label" for="flexCheckDefault">
                Female
              </label>
            </div>
            <button class="btn-sm btn-success m-3 col-10" id="search-btn">
              SEARCH
            </button>
          </div>
        </div>
        <!-- search column end -->

        <!-- outfit records start -->
        <div id="map-section" class="col-10 d-flex flex-row align-items-center">
          <OutfitCard
            v-for="outfit in outfits"
            v-bind:key="outfit._id"
            v-bind:outfit="outfit"
          />
        </div>
        <!-- outfit records end -->
      </main>
    </div>
  </div>
</template>

<script>
import OutfitCard from "./OutfitCard";
import axios from "axios";

const BASE_API_URL = "http://localhost:7070/";

export default {
  name: "OutfitsPage",
  created: async function () {
    let response = await axios.get(BASE_API_URL + "outfits");
    this.outfits = response.data;
  },
  components: {
    OutfitCard,
  },
  data: function () {
    return {
      outfits: [],
    };
  },
};
</script>

<style>
#outfits-div {
  height: 100vh;
  background-image: url("../images/fashion-background.jpg");
  background-size: cover;
}
#background {
  height: 100%;
  width: 100%;
  background-color: rgba(0, 0, 0, 0.5);
}
#search-div {
  background-color: rgb(241, 241, 241);
}
</style>