<template>
  <div class="cost">
    <div class="card-text fw-bold d-flex">
      <p @click="calculateTotalPrice">Total cost:</p>
      <span class="text-warning">$</span>
      <p>{{ calculateTotalPrice() }}</p>
    </div>
  </div>
</template>
<script setup>
const props = defineProps({
  items: Array,
});
const calculateTotalPrice = () => {
  let totalPrice = 0;
  for (const item of props.items) {
    totalPrice += item.count * item.price;
  }
  return totalPrice.toFixed(1);
};
</script>
<style scoped>
.cost {
  position: absolute;
  bottom: 30px;
  font-size: 25px;
}
</style>
