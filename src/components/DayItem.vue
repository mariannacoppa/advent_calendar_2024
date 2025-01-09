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
        <img :src="icon" alt="" class="icon h-25 mt-2" />
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

.icon {
  width: 40%;
  height: 40%;
}

/*layout dayItem 25*/
.special-day .day-item {
  background-color: white;
  width: 95%;
  .icon {
    width: 5% !important;
  }
  .number {
    color: #296150;
    font-weight: bolder;
  }
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: #100b458b; /* Overlay blu */
  border-radius: 8px;
  z-index: 1;
}
</style>
