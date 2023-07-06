<template>
  <div class="orderside">
    <div class="d-flex align-items-center gap-1 order-menu">
      <i class="bi bi-cart4"></i>
      <h2 @click="chsol">Order list</h2>
    </div>
    <OrderCard v-for="item in orderList" :key="item" :item="item" />

    <Totalcost :items="orderList" />
  </div>
</template>

<script setup>
import OrderCard from "./OrderCard.vue";
import Totalcost from "./Totalcost.vue";
const props = defineProps({
  orderList: Array,
});
</script>

<style scoped>
.orderside {
  position: fixed;
  top: 100px;
  bottom: 0;
  right: 18px;
  overflow-y: auto;
  width: 280px;

  background-color: #fcfcfc;
  border-radius: 20px;
  padding: 20px;
}

.order-menu i {
  font-size: 30px;
}

.orderside h2 {
  text-align: center;
  margin-bottom: 0;
}
</style>
