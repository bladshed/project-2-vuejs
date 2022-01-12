<template>
  <div id="content-div" class="d-flex">
    <main class="d-flex py-3 w-100">
      <!-- search column start -->
      <div class="col-2 p-3 justify-content-center align-items-center" id="search-div">
        <div class="text-center">
          <b-button v-b-modal.modal-outfit variant="success" class="btn-sm m-1 col-10 text-center" v-on:click="newModal">Add Outfit</b-button>
        </div>
        <hr />

        <input id="search-input" class="form-control" type="text" placeholder="search input" v-model="searchInput"/>
        <hr />
        <label>Types</label>
        <div class="form-check">
          <input class="form-check-input" type="checkbox" id="search-formal" name="search-formal" value="formal" v-model="searchType"/>
          <label class="form-check-label" for="search-formal">
            Formal
          </label>
        </div>
        <div class="form-check">
          <input class="form-check-input" type="checkbox" id="search-casual" name="search-casual" value="casual" v-model="searchType"/>
          <label class="form-check-label" for="search-casual">
            Casual
          </label>
        </div>
        <div class="form-check">
          <input class="form-check-input" type="checkbox" id="search-streetwear" name="search-streetwear" value="streetwear" v-model="searchType"/>
          <label class="form-check-label" for="search-streetwear">
            Streetwear
          </label>
        </div>

        <hr />
        <label>Genders</label>
        <div class="form-check">
          <input class="form-check-input" type="checkbox" id="search-male" name="search-male" value="male" v-model="searchGender"/>
          <label class="form-check-label" for="search-male">
            Male
          </label>
        </div>
        <div class="form-check">
          <input class="form-check-input" type="checkbox" id="search-female" name="search-female" value="female" v-model="searchGender"/>
          <label class="form-check-label" for="search-female">
            Female
          </label>
        </div>
        <div class="text-center">
          <button class="btn-sm btn-success m-1 col-10" id="search-btn" v-on:click="searchQuery">
            SEARCH
          </button>
        </div>
      </div>
      <!-- search column end -->

      <!-- outfit records start -->
      <div id="records-div" class="col-10 d-flex justify-content-center align-items-center flex-wrap">
        <OutfitCard
          v-on:edit-outfit="editOutfit"
          v-on:view-outfit="viewOutfit"
          v-on:delete-outfit="deleteOutfit"
          v-for="outfit in outfits"
          v-bind:key="outfit._id"
          v-bind:outfit="outfit"
        />
        <b-button v-b-modal.modal-outfit id="edit-modal" class="d-none">Add Outfit</b-button>
        <b-button v-b-modal.view-modal id="view-modal" class="d-none">Add Outfit</b-button>
      </div>
      <!-- outfit records end -->
    </main>

    <!-- add/edit modal start -->
    <b-modal id="modal-outfit" title="Outfit Form" hide-footer>
      <AddEditModal v-if="isNewOutfit"
        v-on:add-edit-outfit="addEditOutfit"
        v-bind:initOutfit="{
          submittedBy: '',
          type: '',
          gender: '',
          img_url: '',
          description : ''
        }"
      />
      <AddEditModal v-else
        v-on:add-edit-outfit="addEditOutfit"
        v-bind:initOutfit="forEditData"
      />
    </b-modal>
    <!-- add/edit modal end -->

    <!-- view modal start -->
    <b-modal id="view-modal" size="lg" scrollable title="View Outfit" hide-footer>
      <ViewModal 
        v-bind:initOutfitData="forEditData"
      />
    </b-modal>
    <!-- view modal end -->

  </div>
</template>

<script>
import OutfitCard from "./OutfitCard";
import AddEditModal from "./AddEditModal"
import ViewModal from "./ViewModal"
import axios from "axios";
import qs from 'qs'

const BASE_API_URL = "https://fms-project-2-apis.herokuapp.com/";

export default {
  name: "OutfitsPage",
  created: async function () {
    // initialize data
    let response = await axios.get(BASE_API_URL + "outfits");
    this.outfits = response.data;
  },
  components: {
    OutfitCard, AddEditModal, ViewModal
  },
  props: ["forEditData"],
  data: function () {
    return {
      outfits: [],
      isModalClicked: false,
      isNewOutfit: false,
      searchInput: '',
      searchType: [],
      searchGender: []
    };
  },
  methods:{
    refreshData: async function (){
      // call get all outfits api
      let response = await axios.get(BASE_API_URL + "outfits");
      this.outfits = response.data;
    },
    newModal: function() {
      // set boolean
      this.isNewOutfit = true;
    },
    addEditOutfit: async function(outfitData) {
      if(outfitData.id){
        // call edit api
        await axios.put(BASE_API_URL + "outfits/" +outfitData.id, outfitData);
        alert("Edit Outfit Successful!")
      } else {
        // call add new api
        await axios.post(BASE_API_URL + "outfits",outfitData);
        alert("New Outfit Added!")
      }
      // close modal
      document.querySelector('.close').click();
      // refresh data list
      this.refreshData();
    },
    editOutfit: async function(outfitId) {
      // set boolean
      this.isNewOutfit = false;
      // get outfit data
      let response = await axios.get(BASE_API_URL + "outfits/" + outfitId);
      // set data
      this.forEditData = response.data.outfit;
      document.getElementById("edit-modal").click();
    },
    viewOutfit: async function(outfitId) {
      // get outfit data
      let response = await axios.get(BASE_API_URL + "outfits/" + outfitId);
      // set data
      this.forEditData = response.data.outfit;
      // click button to open modal
      document.getElementById("view-modal").click();
    },
    deleteOutfit: async function(outfitId) {
      if (confirm("Are you sure you want to delete this outfit? Press OK to confirm")) {
        // call delete api
        await axios.delete(BASE_API_URL + "outfits/" + outfitId);
        // refresh data list
        this.refreshData();
        alert("Delete Outfit Successful!")
      }
    },
    searchQuery: async function() {
      // call search api
      let results = await axios.get(BASE_API_URL + 'outfit-search', {
        params: {
          description: this.searchInput,
          types: this.searchType,
          genders: this.searchGender
        },
        paramsSerializer: params => {
          return qs.stringify(params)
        }
      });

      // set query list
      this.outfits = results.data;
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