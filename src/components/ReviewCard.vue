<template>
  <div class="card col-12 custom-card">
    <div class="card-header">
      <div v-if="!this.review.isNew">
        {{this.review.submittedBy}}
      </div>
      <div v-else>
        <input type="email" class="form-control" placeholder="email name@example.com" id="reviewEmail" v-model="review.submittedBy">
      </div>
    </div>
    <div class="card-body">
      <div v-if="!review.isNew">
        <p class="card-title"><b>{{review.comment}}</b></p>
      </div>
      <div v-else>
        <input type="text" class="form-control" placeholder="comment" id="comment" v-model="review.comment">
      </div>

      <!-- rating -->
      <div>
        <label>Rating :</label>
        <div class="form-check form-check-inline ms-3 my-1">
            <input v-if="!review.isNew" class="form-check-input disable" type="radio" v-bind:name="review.id" v-bind:id="review.id + '_1'" value="1" v-model="review.rating" disabled>
            <input v-else class="form-check-input disable" type="radio" v-bind:name="review.id" v-bind:id="review.id + '_1'" value="1" v-model="review.rating">
            <label class="form-check-label" v-bind:for="review.id + '_1'">1</label>
        </div>
        <div class="form-check form-check-inline my-1">
            <input v-if="!review.isNew" class="form-check-input disable" type="radio" v-bind:name="review.id" v-bind:id="review.id + '_2'" value="2" v-model="review.rating" disabled>
            <input v-else class="form-check-input disable" type="radio" v-bind:name="review.id" v-bind:id="review.id + '_2'" value="2" v-model="review.rating">
            <label class="form-check-label" v-bind:for="review.id + '_2'">2</label>
        </div>
        <div class="form-check form-check-inline my-1">
            <input v-if="!review.isNew" class="form-check-input disable" type="radio" v-bind:name="review.id" v-bind:id="review.id + '_3'" value="3" v-model="review.rating" disabled>
            <input v-else class="form-check-input disable" type="radio" v-bind:name="review.id" v-bind:id="review.id + '_3'" value="3" v-model="review.rating">
            <label class="form-check-label" v-bind:for="review.id + '_3'">3</label>
        </div>
        <div class="form-check form-check-inline my-1">
            <input v-if="!review.isNew" class="form-check-input disable" type="radio" v-bind:name="review.id" v-bind:id="review.id + '_4'" value="4" v-model="review.rating" disabled>
            <input v-else class="form-check-input disable" type="radio" v-bind:name="review.id" v-bind:id="review.id + '_4'" value="4" v-model="review.rating">
            <label class="form-check-label" v-bind:for="review.id + '_4'">4</label>
        </div>
        <div class="form-check form-check-inline my-1">
            <input v-if="!review.isNew" class="form-check-input disable" type="radio" v-bind:name="review.id" v-bind:id="review.id + '_5'" value="5" v-model="review.rating" disabled>
            <input v-else class="form-check-input disable" type="radio" v-bind:name="review.id" v-bind:id="review.id + '_5'" value="5" v-model="review.rating">
            <label class="form-check-label" v-bind:for="review.id + '_5'">5</label>
        </div>
      </div>
    </div>
    <div class="d-flex flex-row align-items-start">
        <button class="badge bg-success ms-1 mb-1" v-if="!review.isNew" v-on:click="editReview">Edit</button>
        <button class="badge bg-danger ms-1 mb-1" v-if="!review.isNew" v-on:click="deleteReview">Delete</button>
        <button class="badge bg-success ms-1 mb-1" v-else v-on:click="saveReview">Save</button>
    </div>
    <div class="card-footer text-muted">
      <div v-if="!review.isNew">
        {{ review.dateModified ? review.dateModified.split("T")[0] : review.dateCreated.split("T")[0] }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ReviewCard",
  props: ["forReview"],
  data: function () {
    return {
      review:{
        id: this.forReview._id,
        submittedBy: this.forReview.submittedBy,
        rating: this.forReview.rating,
        comment: this.forReview.comment,
        dateCreated: this.forReview.dateCreated,
        dateModified: this.forReview.dateModified,
        isNew: this.forReview.isNew
      }
    };
  },
  methods: {
    editReview: function () {
      this.review.isNew = true;
    },
    saveReview: async function () {
      if(this.review.submittedBy.length > 0
       && this.review.comment.length > 0
       && this.review.rating){
        if(this.review.id){
          this.review.isNew = false;
          this.$emit("edit-review", this.review);
        } else {
          await this.$emit("save-review", this.review);
          this.review = {
            id: '',
            submittedBy: '',
            rating: '',
            comment: '',
            dateCreated: '',
            dateModified: '',
            isNew: true
          }
        }
      } else {
         alert("Please fill up everything");
      }
    },
    deleteReview: function () {
      this.$emit("delete-review", this.review.id);
    }
  }
};
</script>

<style>
img {
  height: 270px;
  width: 100%;
}
.badge{
  font-size: 0.5em !important;
}
.custom-card>.card-header,.card-footer{
  font-size: 10px;
}
.custom-card>.card-body{
  font-size: 12px;
  padding: 4px;
}
.card-header>div>.form-control{
  font-size: 12px;
}
.card-body>div>.form-control{
  font-size: 12px;
}
</style>