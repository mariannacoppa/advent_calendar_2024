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
      days: daysItems,
      showModal: false,
      modalContent: {},
    };
  },
  methods: {
    openModal(item) {
      this.modalContent = item;
      this.showModal = true;
    },
    closeModal() {
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
          @click.native="openModal(dayItem)"
        />
      </div>
    </main>
    <Modal v-if="showModal" :content="modalContent" @close="closeModal" />
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
