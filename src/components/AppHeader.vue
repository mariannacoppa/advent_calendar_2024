<script>
export default {};
</script>
<template>
  <div class="bg-darkblue pt-2">
    <header class="container rounded-3">
      <div class="row">
        <div class="col-12">
          <h1 class="text-white fs-3 text-center pt-2">
            Advent<br />
            Calendar <br />
            2024
          </h1>
          <img src="../assets/header-bg.png" alt="" class="header-img" />
        </div>
      </div>
    </header>
  </div>
</template>
<style lang="scss">
.bg-darkblue {
  background-color: #100b45;
  height: 20vh;
  width: 100%;
  header {
    height: 30vh;
    width: 90%;
    background-color: #2b35f1;
    position: relative;
    .header-img {
      width: 100%;
      position: absolute;
      top: 5%;
      right: 0vw;
      z-index: 1;
    }
  }
  header:hover {
    background-color: rgb(38, 20, 120);
    opacity: 0.5;
    transition: 1s;
    cursor: url(../assets/icons/ico-stella.png), auto;
    h1 {
      font-weight: bold;
      transition: 0.5s;
    }
  }
}
</style>
