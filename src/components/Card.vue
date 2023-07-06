<template>
  <div class="card mt-4" style="width: 13rem">
    <img
      :src="item.img"
      class="card-img-top card--img"
      :alt="item.title"
      @click="selectItem"
    />
    <div class="card-body p-3">
      <div class="d-flex align-items-center justify-content-center flex-column">
        <p class="card-title">{{ item.title }}</p>
        <div class="card-text fw-bold d-flex fs-5">
          <span class="text-warning">$</span>
          <p>{{ item.price }}</p>
        </div>
      </div>

      <div class="d-flex align-items-center justify-content-between">
        <button @click="incremeant(item)" class="btn btn-warning">+</button>
        <span>{{ props.item.count }}</span>
        <button
          :disabled="item.count <= 0"
          @click="dicrement(item)"
          class="btn btn-warning"
        >
          -
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, defineProps, defineEmits } from "vue";
const props = defineProps({
  item: Object,
});
const emit = defineEmits(["pushItem", "selectItem"]);

const isSelected = ref(false);

const selectItem = () => {
  isSelected.value = true;
  emit("selectItem", props.item);
  // console.log(props.item);
};

const incremeant = (item) => {
  emit("pushItem", item);
  item.count++;
};
const dicrement = (item) => {
  emit("pushItem", item);
  item.count--;
};
</script>
<style scoped>
.card--img {
  width: 200px;
  height: 180px;
  padding: 18px;
  cursor: pointer;
}
</style>
