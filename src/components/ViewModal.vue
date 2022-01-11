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
    </div>
  </div>
</template>

<script>

// const BASE_API_URL = "http://localhost:7070/";

export default {
  name: "ViewModal",
  props: ["initOutfitData", "mode"],
  data: function () {
    return {
      viewOutfit: {
        id: this.initOutfitData._id,
        submittedBy: this.initOutfitData.submittedBy,
        type: this.initOutfitData.type,
        gender: this.initOutfitData.gender,
        img_url: this.initOutfitData.img_url,
        description: this.initOutfitData.description,
      },
    };
  },
  methods: {
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