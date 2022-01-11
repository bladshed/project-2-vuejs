<template>
  <div id="content-div" class="d-flex">
    <main class="d-flex py-3">
      <!-- search column start -->
      <div class="col-2 p-3 justify-content-center align-items-center" id="search-div">
        <div class="text-center">
          <b-button v-b-modal.modal-outfit variant="success" class="btn-sm m-1 col-10 text-center" v-on:click="newModal">Add Outfit</b-button>
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
          <input class="form-check-input" type="checkbox" value="streetwear"/>
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

const BASE_API_URL = "http://localhost:7070/";

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
      isNewOutfit: false
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