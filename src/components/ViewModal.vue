<template>
  <div class="col-12">
    <div class="text-center">
      <img class="mx-0 view-img" v-bind:src="viewOutfit.img_url" alt="" />
    </div>
    <br />
    <div class="details">
      <h3>{{viewOutfit.description}}</h3>
      <p><b>Submitted By:</b> {{viewOutfit.submittedBy}}</p>
      <p><b>Type:</b> {{viewOutfit.type}}</p>
      <p><b>Gender:</b> {{viewOutfit.gender}}</p>
    </div>
    <br />
    <div>
      <h3>REVIEWS:</h3>
      <ReviewCard 
        v-for="review in viewOutfit.reviews"
        v-bind:key="review._id"
        v-bind:forReview="review"
        v-on:edit-review="addEditReview"
        v-on:delete-review="deleteReview"
      />
      <ReviewCard 
        v-bind:forReview="{
          submittedBy: '',
          comment : '',
          rating: '',
          isNew: true
        }"
        v-on:save-review="addEditReview"
      />
    </div>
  </div>
</template>

<script>
import ReviewCard from "./ReviewCard";
import axios from "axios";

const BASE_API_URL = "https://fms-project-2-apis.herokuapp.com/";

export default {
  name: "ViewModal",
  components: {
    ReviewCard
  },
  props: ["initOutfitData"],
  data: function () {
    return {
      viewOutfit: this.initOutfitData,
    };
  },
  methods: {
    refreshOutfitData: async function() {
      // call get all outfits api
      let response = await axios.get(BASE_API_URL + "outfits/" + this.viewOutfit._id);
      this.viewOutfit = response.data.outfit;
    },
    addEditReview: async function(review) {
      if(review.id){
        // call edit review api /reviews/:reviewId
        await axios.put(BASE_API_URL + "reviews/" + review.id, review);
        alert("Edit Review Successful!")
      } else {
        // call add new api /outfits/:id/reviews/add
        await axios.post(BASE_API_URL + "outfits/" + this.viewOutfit._id + "/reviews/add", review);
        alert("New Review Added!");
      }
      // refresh data
      this.refreshOutfitData();
    },
    deleteReview: async function(reviewId) {
      if (confirm("Are you sure you want to delete this review? Press OK to confirm")) {
        // call delete api
        await axios.delete(BASE_API_URL + "reviews/" + reviewId);
        // refresh data
        this.refreshOutfitData();
        alert("Delete Review Successful!")
      }
    }
  },
  computed: {
  },
};
</script>

<style>
.red-font{
    color:red;
}
.view-img {
  height: 470px;
  width: 350px;
}
.details>h3,p{
  margin: 0px !important;
}
</style>