<template>
  <div id="content-div" class="d-flex">
    <main class="d-flex py-3">
      <!-- search column start -->
      <div class="col-2 p-1 justify-content-center align-items-center" id="search-div">
        <br />
        <div class="text-center">
          <b-button v-b-modal.add-outfit variant="primary" class="btn-sm m-1 col-10 text-center">Add Outfit</b-button>
        </div>
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
        <div class="text-center">
          <button class="btn-sm btn-success m-1 col-10" id="search-btn">
            SEARCH
          </button>
        </div>
      </div>
      <!-- search column end -->

      <!-- outfit records start -->
      <div id="records-div" class="col-10 d-flex justify-content-center align-items-center flex-wrap">
        <OutfitCard
          v-for="outfit in outfits"
          v-bind:key="outfit._id"
          v-bind:outfit="outfit"
        />
      </div>
      <!-- outfit records end -->
    </main>

    <!-- modal -->
    <b-modal id="add-outfit" title="BootstrapVue" hide-footer>
      <AddOutfitModal 
        v-on:new-outfit-added="addOutfit"
        v-bind:initOutfit="{
          submittedBy: '',
          type: '',
          gender: '',
          img_url: '',
          description : ''
        }" 
      />
    </b-modal>
    <!-- add/edit modal start -->

    <!-- <Modal /> -->
  </div>
</template>

<script>
import OutfitCard from "./OutfitCard";
import AddOutfitModal from "./AddOutfitModal"
import axios from "axios";

const BASE_API_URL = "http://localhost:7070/";

export default {
  name: "OutfitsPage",
  created: async function () {
    let response = await axios.get(BASE_API_URL + "outfits");
    this.outfits = response.data;
  },
  components: {
    OutfitCard, AddOutfitModal,
  },
  data: function () {
    return {
      outfits: [],
      isModalClicked: false
    };
  },
  methods:{
    refreshData: async function (){
      let response = await axios.get(BASE_API_URL + "outfits");
      this.outfits = response.data;
    },
    clickModal: function() {
      if(this.isModalClicked){
        this.isModalClicked = false;
      } else {
        this.isModalClicked = true;
      }
    },
    addOutfit: async function(newOutfit) {
      console.log(newOutfit);
      await axios.post(BASE_API_URL + "outfits",newOutfit);
      alert("New Outfit Added!")
      document.querySelector('.close').click();
      this.refreshData();
    }
  }
};
</script>

<style>
#content-div{
  height: 100vh;
}
#search-div {
  background-color: rgb(241, 241, 241);
  height: 80vh;
  overflow-y: auto;
}
.btn-custom {
  color: #fff;
  background-color: #0d6efd;
  border-color: #0d6efd;
}
#records-div{
  height: 80vh;
  overflow-y: auto;
}
</style>