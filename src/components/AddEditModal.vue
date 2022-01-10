<template>
  <div class="col-12">
    <!-- email -->
    <div class="form-floating">
        <input type="email" class="form-control" placeholder="name@example.com" id="email" v-model="newOutfit.submittedBy">
        <label for="email">Email address</label>
    </div>
    <div v-if="isEmailOk === false && hasSubmitted === true" class="red-font">
        * Please input email
    </div>

    <!-- types -->
    <div>
        <label>Type: </label>
        <div class="form-check form-check-inline ms-2 mt-3">
            <input class="form-check-input" type="radio" name="type" id="formal" value="formal" v-model="newOutfit.type">
            <label class="form-check-label" for="formal">Formal</label>
        </div>
        <div class="form-check form-check-inline ms-2 mt-3">
            <input class="form-check-input" type="radio" name="type" id="casual" value="casual" v-model="newOutfit.type">
            <label class="form-check-label" for="casual">Casual</label>
        </div>
        <div class="form-check form-check-inline ms-2 mt-3">
            <input class="form-check-input" type="radio" name="type" id="streetwear" value="streetwear" v-model="newOutfit.type">
            <label class="form-check-label" for="streetwear">Streetwear</label>
        </div>
    </div>
    <div v-if="isTypeOk === false && hasSubmitted === true" class="red-font">
        * Please choose type
    </div>

    <div>
        <label>Gender :</label>
        <!-- gender -->
        <div class="form-check form-check-inline ms-2 mt-3">
            <input class="form-check-input" type="radio" name="gender" id="male" value="male" v-model="newOutfit.gender">
            <label class="form-check-label" for="male">Male</label>
        </div>
        <div class="form-check form-check-inline ms-2 mt-3">
            <input class="form-check-input" type="radio" name="gender" id="female" value="female" v-model="newOutfit.gender">
            <label class="form-check-label" for="female">Female</label>
        </div>
    </div>
    <div v-if="isGenderOk === false && hasSubmitted === true" class="red-font">
        * Please choose gender
    </div>

    <!-- img url -->
    <div class="form-floating mt-3">
        <input type="text" class="form-control" placeholder="image url" id="img-url" v-model="newOutfit.img_url">
        <label for="img-url">Image URL</label>
    </div>
    <div v-if="isImgUrlOK === false && hasSubmitted === true" class="red-font">
        * Please input img url
    </div>

    <!-- description -->
    <div class="form-floating mt-3">
        <input type="text" class="form-control" placeholder="image url" id="description" v-model="newOutfit.description">
        <label for="description">Description</label>
    </div>
    <div v-if="isDescriptionOK === false && hasSubmitted === true" class="red-font">
        * Please input description
    </div>

    <b-button class="btn-sm mt-3" variant="success" block v-on:click="addEditOutfit">Submit</b-button>
  </div>
</template>

<script>
export default {
  name: "AddEditModal",
  props: ["initOutfit", "mode"],
  data: function () {
    return {
      newOutfit: {
        id: this.initOutfit._id,
        submittedBy: this.initOutfit.submittedBy,
        type: this.initOutfit.type,
        gender: this.initOutfit.gender,
        img_url: this.initOutfit.img_url,
        description: this.initOutfit.description,
      },
      hasSubmitted: false
    };
  },
  methods: {
    addEditOutfit: function () {
      // set boolean
      this.hasSubmitted = true;

      // validate form
      if(this.newOutfit.submittedBy.length > 0
       && this.newOutfit.type.length > 0
       && this.newOutfit.gender.length > 0
       && this.newOutfit.img_url.length > 0
       && this.newOutfit.description.length > 0)
        this.$emit("add-edit-outfit", { ...this.newOutfit }); //trigger event
      else {
        alert("Please fill up everything");
      }
    },
  },
  computed: {
    // a computed property is like a function
    // in the `methods`
    // however we refer to it as if it is a data
    // variable in the template
    isEmailOk: function () {
      return this.newOutfit.submittedBy.length > 0;
    },
    isTypeOk: function () {
      return this.newOutfit.type.length > 0;
    },
    isGenderOk: function () {
      return this.newOutfit.gender.length > 0;
    },
    isImgUrlOK: function () {
      return this.newOutfit.img_url.length > 0;
    },
    isDescriptionOK: function () {
      return this.newOutfit.description.length > 0;
    }
  },
};
</script>

<style>
.red-font{
    color:red;
}
</style>