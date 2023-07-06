<template>
  <div class="popup">
    <div class="card mt-2" style="width: 27rem">
      <img :src="item.img" class="card-img-top card--img" :alt="item.title" />
      <div class="card-body p-3">
        <div class="d-flex align-items-center justify-content-between flex-row">
          <p class="card-title fw-bold fs-2">{{ item.title }}</p>
          <div class="card-text fw-bold d-flex fs-5">
            <span class="text-warning">$</span>
            <p>{{ item.price }}</p>
          </div>
        </div>
        <p>
          Lorem Ipsum is simply dummy text of the printing and typesetting
          industry. Lorem Ipsum has been the industry's standard dummy text ever
          since the 1500s, when an unknown printer took a galley of type and
          scrambled
        </p>
        <div class="d-flex align-items-center justify-content-between">
          <button @click="incremeant(item)" class="btn btn-warning">+</button>
          <span>{{ item.count }}</span>
          <button
            :disabled="item.count <= 0"
            @click="dicrement(item)"
            class="btn btn-warning"
          >
            -
          </button>
        </div>
      </div>
      <button class="close-btn rounded" @click="closeDescription">Close</button>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";
const props = defineProps({
  item: Object,
});
const emit = defineEmits(["pushItem", "closeDescription"]);
const incremeant = (item) => {
  emit("pushItem", item);
  item.count++;
};
const dicrement = (item) => {
  emit("pushItem", item);
  item.count--;
};

const closeDescription = () => {
  emit("closeDescription");
};
</script>

<style scoped>
.card--img {
  width: 400px;
  height: 350px;
  padding: 18px;
}
.popup {
  position: fixed;
  left: 50%;
  transform: translateX(-50%);
  top: 10%;
  opacity: 1;
  transition: all 0.7s ease;
  z-index: 9999;
}
.close-btn {
  border: none;
  background-color: #fa5252;
  padding: 10px 20px;
  color: white;
}
</style>
