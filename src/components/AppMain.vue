<script>
import daysItems from "../../daysItems.json";
import DayItem from "./DayItem.vue";
export default {
  components: {
    DayItem,
  },
  data() {
    return {
      days: daysItems,
    };
  },
};
</script>
<template>
  <div class="bg-darkblue">
    <main class="container">
      <div class="row">
        <DayItem
          class="col-3 col-md-2 d-flex justify-content-center"
          v-for="(dayItem, index) in days"
          :icon="dayItem.icon"
          :number="dayItem.number"
        />
      </div>
    </main>
  </div>
</template>
<style lang="scss" scoped>
.bg-darkblue {
  background-color: #100b45;
}
.container {
  .col-3 {
    color: white;
    font-weight: bold;
  }
}
</style>
