<script>
export default {};
</script>
<template>
  <div class="bg-darkblue">
    <header class="container rounded-bottom-3">
      <h1 class="text-white fs-2 text-center p-5">
        Advent Calendar <br />
        2024
      </h1>
      <img src="../assets/header-bg.png" alt="" class="header-img" />
    </header>
  </div>
</template>
<style lang="scss">
.bg-darkblue {
  background-color: #100b45;
  header {
    height: 30vh;
    background-color: #2b35f1;
    position: relative;
    .header-img {
      width: 100%;
      position: absolute;
      top: 40%;
      right: 0vw;
      z-index: 1;
    }
  }
}
</style>
