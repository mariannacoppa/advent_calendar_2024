<script>
import daysItems from "../../daysItems.json";
import DayItem from "./DayItem.vue";
import Modal from "./Modal.vue";

export default {
  components: {
    DayItem,
    Modal,
  },
  data() {
    return {
      days: daysItems.map((day, index) => ({
        ...day,
        covered:
          JSON.parse(localStorage.getItem(`day-${index}-covered`)) || false,
      })),
      showModal: false,
      currentDayIndex: null,
    };
  },
  methods: {
    openModal(index) {
      this.currentDayIndex = index;
      this.showModal = true;
    },
    closeModal() {
      if (this.currentDayIndex !== null) {
        this.days[this.currentDayIndex].covered = true;
        localStorage.setItem(`day-${this.currentDayIndex}-covered`, true);
      }
      this.showModal = false;
    },
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
          :key="index"
          :icon="dayItem.icon"
          :number="dayItem.number"
          :covered="dayItem.covered"
          @click.native="openModal(index)"
        />
      </div>
    </main>
    <Modal
      v-if="showModal"
      :content="days[currentDayIndex]"
      @close="closeModal"
    />
  </div>
</template>

<style lang="scss" scoped>
.bg-darkblue {
  background-color: #100b45;
  height: calc(100vh - 30vh);
  width: 100vw;
  position: absolute;
  z-index: 1;
}
.container {
  .col-3 {
    color: white;
    font-weight: bold;
  }
}
</style>
