<template>
  <div :class="{ none: item.count === 0 }">
    <div class="d-flex">
      <img :src="item.img" class="order-card--img" />
      <div>
        <p>{{ item.title }}</p>
        <span class="text-secondary">x{{ item.count }}</span>
      </div>
      <div class="card-text fw-bold d-flex fs-5">
        <span class="text-warning">$</span>
        <p>{{ item.price }}</p>
      </div>
    </div>
  </div>
</template>
<script setup>
defineProps({
  item: Object,
});
</script>
<style scoped>
.order-card--img {
  width: 24px;
  height: 24px;
}
p {
  margin-bottom: 0;
}
.none {
  display: none;
}
</style>
