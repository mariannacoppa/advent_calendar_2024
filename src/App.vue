<script>
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";

export default {
  components: {
    AppHeader,
    AppMain,
  },
};
// document.querySelectorAll(".icon").forEach((icon) => {
//   const id = icon.getAttribute("data-id");
//   const isActive = localStorage.getItem(id) === "true";
//   if (isActive) icon.classList.add("active");

//   icon.addEventListener("click", () => {
//     icon.classList.toggle("active");
//     const activeState = icon.classList.contains("active");
//     localStorage.setItem(id, activeState);
//   });
// });
</script>
<template>
  <div>
    <AppHeader />
    <AppMain />
  </div>
</template>
<style lang="scss">
@use "./styles/generals.scss";
</style>
