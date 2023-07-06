<template>
  <div :class="{ 'blurred-background': showDescriptionValue }">
    <div
      class="d-flex align-items-center justify-content-between product--header"
    >
      <h2 class="p-2 mt-5" id="mahsulotlar">Products</h2>
      <Filter @applyFilter="applyFilter" />
    </div>
    <RangeFilter @filter="emitFilter" />

    <div class="card-wrapper">
      <template v-if="filteredAndSortedItems.length">
        <div v-for="item in filteredAndSortedItems" :key="item.id">
          <Card @pushItem="takeItems" @selectItem="selectItem" :item="item" />
        </div>
      </template>

      <template v-else>
        <p class="validation">
          There are no products that match the filter price.
        </p>
      </template>
    </div>
  </div>
  <Description
    @pushItem="takeItems"
    :item="selectedItem"
    v-if="showDescriptionValue"
    @closeDescription="closeDescription"
  />
</template>

<script setup>
import { ref, defineEmits, computed } from "vue";
import Card from "./Card.vue";
import Filter from "./Filter.vue";
import RangeFilter from "./RangeFilter.vue";
import Description from "./Description.vue";
const items = ref([
  {
    title: "Fish burger",
    price: 20.9,
    img: "https://media.istockphoto.com/id/840902892/photo/burger-isolated-on-white.jpg?s=612x612&w=0&k=20&c=QhBjklDI7l_Q2kvRmUuF5SoVaUHHjIMxioIvSegKV4o=",
    id: 1,
    count: 0,
  },
  {
    title: "Lavash",
    price: 40.9,
    img: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT_Z14pNsWvJUK1je1GEPwljwjqTAa_Vsg5p5UxaWs-e-o692gB1vGipLDA1Y0w_s4SOA4&usqp=CAU",
    id: 2,
    count: 0,
  },
  {
    title: "Sandwich",
    price: 19.9,
    img: "https://rare-gallery.com/uploads/posts/861558-Fast-food-Sandwich-Bread-Closeup-White-background.jpg",
    id: 3,
    count: 0,
  },
  {
    title: "Pizza",
    price: 29.9,
    img: "https://png.pngtree.com/png-vector/20230331/ourmid/pngtree-gourmet-pizza-cartoon-png-image_6656160.png",
    id: 4,
    count: 0,
  },
  {
    title: "Hot dog",
    price: 27.9,
    img: "https://media.istockphoto.com/id/1131775824/photo/hot-dog-on-white.jpg?s=612x612&w=0&k=20&c=Mxa7_X-V0jnDaYV1cf2qD4XvZ2A2LWWKHpnAI2C86BM=",
    id: 5,
    count: 0,
  },
  {
    title: "Shaurma",
    price: 24.9,
    img: "https://eda.yandex/images/3682162/6c8bd555785e0fbd07dd412011345f92-216x188.jpg",
    id: 6,
    count: 0,
  },
]);
//For showing the description
const selectedItem = ref(null);
const showDescriptionValue = ref(false);

const emit = defineEmits(["orderListChange"]);

const takeItems = (item) => {
  emit("orderListChange", item);
};

const filter = ref("All");
const minPrice = ref(0);
const maxPrice = ref(60);

//Range Filter
const emitFilter = ({ minRange, maxRange }) => {
  minPrice.value = minRange;
  maxPrice.value = maxRange;
};

const filteredAndSortedItems = computed(() => {
  let filteredItems = items.value.filter(
    (item) => item.price >= minPrice.value && item.price <= maxPrice.value
  );

  switch (filter.value) {
    case "Increase":
      return filteredItems.sort((a, b) => a.price - b.price);
    case "Decrease":
      return filteredItems.sort((a, b) => b.price - a.price);
    default:
      return filteredItems;
  }
});

const applyFilter = (selectedFilter) => {
  filter.value = selectedFilter;
};
//Description
const selectItem = (item) => {
  selectedItem.value = item;
  showDescriptionValue.value = true;
  console.log(selectedItem.value);
};

const closeDescription = () => {
  showDescriptionValue.value = false;
};
</script>

<style scoped>
.card-wrapper {
  width: 900px;
  margin-left: 40px;
  display: grid;

  grid-template-rows: 1fr 1fr;
  grid-template-columns: 1fr 1fr 1fr;

  row-gap: 70px;
  height: 100%;
  align-items: center;
}
.product--header {
  width: 850px;
}
.validation {
  font-size: 25px;
  font-weight: bold;
  width: 780px;
  text-align: center;
  margin-top: 30px;
}

.blurred-background {
  filter: blur(8px);
  -webkit-filter: blur(8px);
}
</style>
