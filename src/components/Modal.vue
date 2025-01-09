<template>
  <div class="modal-overlay" @click="$emit('close')">
    <div class="modal-content" @click.stop>
      <button class="close-btn text-white" @click="$emit('close')">
        Close
      </button>
      <div
        class="gif rounded-3 d-flex justify-content-center"
        v-if="content.type === 'image'"
      >
        <img :src="content.url" alt="Modal content" />
      </div>
      <div v-else>
        <p class="rounded-3 p-2 me-3">{{ content.text }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    content: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style lang="scss">
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.6);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal-content {
  padding: 20px;
  border-radius: 8px;
  position: relative;
  max-width: 65%;
  max-height: 100%;
  overflow: auto;
  p,
  .gif {
    color: white;
    background-color: #296150;
  }
}

.close-btn {
  position: absolute;
  top: 0px;
  right: 0px;
  background: brown;
  padding: 5px;
  border-radius: 15px;
  border: none;
  font-size: 15px;
  cursor: pointer;
}
</style>
