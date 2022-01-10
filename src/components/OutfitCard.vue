<template>
  <div class="card col-2 m-2">
    <div class="card-header">
        {{ outfit.type.toUpperCase() }}
    </div>
    <div class="card-body">
        <h5 class="card-title">{{ outfit.gender.toUpperCase() }}</h5>
        <img class="mx-0" v-bind:src="outfit.img_url" alt="" />
    </div>
    <div class="d-flex flex-row justify-content-center align-items-center">
        <button class="btn-sm btn-warning mb-3 m-2 col-4">Edit</button>
        <button class="btn-sm btn-success mb-3 m-2 col-4">View</button>
    </div>
    <div class="card-footer text-muted">
        {{ outfit.dateCreated.split("T")[0] }}
    </div>
  </div>
</template>

<script>
export default {
  name: "OutfitCard",
  props: ["outfit"],
  data: function () {
    return {
      formattedDate: "",
    };
  },
//   computed: {
//     // a computed property is like a function
//     // in the `methods`
//     // however we refer to it as if it is a data
//     // variable in the template
//     formatDate: function () {
//         // 2022-01-08T12:45:19.822Z
//         return this.outfit.dateCreated.split("T")[0]
//     },
//   }
};
</script>

<style>
img {
    height: 270px;
    width: 100%;
}
</style>