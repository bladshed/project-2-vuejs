<template>
  <div id="home-div">
    <div id="background" class="d-flex justify-content-center align-items-center">
      <div class="text-center title">
        <h1>UNLOCK YOUR STYLE</h1>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HomePage",
  components: {},
};
</script>

<style>
#home-div {
  height: 100vh;
  background-image: url("../images/fashion-background.jpg");
  background-size: cover;
}
#background {
  height: 100%;
  width: 100%;
  background-color: rgba(0, 0, 0, 0.5);
}
.title {
  font-family: "Roboto", sans-serif;
  color: white;
  background-color: rgba(0, 0, 0, 0.9);
  padding: 15px;
  width: 100%;
}
</style>