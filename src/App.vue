<template>
  <div>
    <Navbar />
    <div class="body-wrapper">
      <Sidebar />
      <Main @orderListChange="orderListChange" />
      <Order :orderList="orderList" />
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import Navbar from "./components/Navbar.vue";
import Sidebar from "./components/Sidebar.vue";
import Order from "./components/Order.vue";
// import Product from "./components/Product.vue";
import Main from "./components/Main.vue";

const orderList = ref([]);
const orderListChange = (item) => {
  const index = orderList.value.findIndex(
    (obj) => obj.id === item.id && obj.name === item.name
  );

  if (index !== -1) {
    orderList.value[index] = item;
  } else {
    orderList.value.push(item);
  }
};
</script>
<style scoped>
.body-wrapper {
  display: flex;
  justify-content: space-between;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  height: 100vh;
}
</style>
