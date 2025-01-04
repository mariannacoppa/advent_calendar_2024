<template>
  <div class="day-item-container" @click="$emit('click')">
    <div class="day-item align-content-center mt-2 rounded-3">
      <div class="d-flex justify-content-center">
        <img :src="icon" alt="" class="h-25 mt-2" />
      </div>
      <div class="number text-center fs-1">{{ number }}</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    icon: String,
    number: String,
  },
};
</script>

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

img {
  width: 40%;
  height: 40%;
}
</style>
