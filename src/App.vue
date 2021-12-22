<template>
  <div id="app">
    <header>
      <img src="https://www.pngall.com/wp-content/uploads/9/Spotify-Logo.png" alt="">
    </header>

    <main>
      <Disks />
    </main>
  </div>
</template>

<script>
import Disks from "./components/Disks.vue";

export default {
  name: "App",
  components: {
    Disks,
  },
};
</script>

<style lang="scss">
@import './style/general.scss';


header{
  height: 80px;
  background-color: #2e3a46;
  line-height: 80px;
  img{
    height: 70px;
    width: auto;
  }
}

main{
  background-color: #1e2d3b;
  padding: 50px 0;
  color: white;
}
</style>
