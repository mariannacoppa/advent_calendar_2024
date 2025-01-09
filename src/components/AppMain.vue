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
    // modal behaviour functions
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
    // removing overlays function
    resetAllCovers() {
      this.days.forEach((day, index) => {
        day.covered = false;
        localStorage.setItem(`day-${index}-covered`, false);
      });
    },
  },
};
</script>

<template>
  <div class="bg-darkblue">
    <main class="container">
      <div class="row">
        <!-- Dynamic binding to class property -->
        <DayItem
          v-for="(dayItem, index) in days"
          :key="index"
          :icon="dayItem.icon"
          :number="dayItem.number"
          :covered="dayItem.covered"
          @click.native="openModal(index)"
          :class="{
            'col-3 col-md-2 d-flex justify-content-center':
              dayItem.number !== '25',
            'col-12 d-flex justify-content-center special-day':
              dayItem.number === '25',
          }"
        />
      </div>
      <!-- removing overlays button -->
      <div class="row">
        <div class="col-12">
          <div class="d-flex justify-content-center">
            <div class="btn btn-danger mt-3" @click="resetAllCovers">Reset</div>
          </div>
        </div>
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
  height: 100vh;
  width: 100%;
  position: absolute;
  z-index: 1;
  .container {
    .col-3 {
      color: white;
      font-weight: bold;
    }
  }
}
</style>
