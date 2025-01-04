<script>
export default {
  props: {
    icon: String,
    number: String,
    covered: Boolean,
  },
};
</script>

<template>
  <div class="day-item-container">
    <div
      class="day-item align-content-center mt-2 rounded-3"
      :class="{ covered }"
    >
      <div class="d-flex justify-content-center">
        <img :src="icon" alt="" class="h-25 mt-2" />
      </div>
      <div class="number text-center fs-1">{{ number }}</div>
    </div>
    <div v-if="covered" class="overlay"></div>
  </div>
</template>

<style lang="scss">
.day-item-container {
  position: relative;
}

.day-item {
  background-color: #296150;
  width: 75%;
}

.day-item:hover {
  cursor: pointer;
}

.day-item:active {
  background-color: #100b45;
}

img {
  width: 40%;
  height: 40%;
}
/*add clicked cell overlay*/
.overlay {
  position: absolute; /*covers the cell*/
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.7);
  border-radius: 8px;
}
</style>
