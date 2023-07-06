<template>
  <div class="main">
    <Dashboard />
    <!-- <Discount /> -->
    <Product @orderListChange="$emit('orderListChange', $event)" />
    <Beverages @orderListChange="$emit('orderListChange', $event)" />
  </div>
</template>
<script setup>
import Product from "./Product.vue";
import Dashboard from "./Dashboard.vue";
import Beverages from "./Beverages.vue";
// import Discount from "./Discount.vue";
</script>

<style scoped>
.main {
  flex-grow: 1;
  overflow-y: auto;
  margin-top: 85px;
  margin-left: 280px;
  background-color: #e9ecef;

  transition: all 0.3s ease-in-out;
}
</style>
