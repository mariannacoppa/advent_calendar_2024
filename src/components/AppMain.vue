<script>
import daysItems from "../../daysItems.json";
import DayItem from "./DayItem.vue";

export default {
  components: {
    DayItem,
  },
  data() {
    return {
      days: daysItems.map((day, index) => ({
        ...day,
        // add "covered" cell state
        covered:
          JSON.parse(localStorage.getItem(`day-${index}-covered`)) || false,
      })),
    };
  },
  methods: {
    // when clicked, each cell change will be memorized in localStorage in order to be visible even after page refreshing
    toggleCover(index) {
      this.days[index].covered = !this.days[index].covered;
      localStorage.setItem(`day-${index}-covered`, this.days[index].covered);
    },
  },
};
</script>

<template>
  <div class="bg-darkblue">
    <main class="container">
      <div class="row">
        <!-- .native changer on dayItem click event spreads the event to the father component -->
        <DayItem
          class="col-3 col-md-2 d-flex justify-content-center"
          v-for="(dayItem, index) in days"
          :key="index"
          :icon="dayItem.icon"
          :number="dayItem.number"
          :covered="dayItem.covered"
          @click.native="toggleCover(index)"
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
