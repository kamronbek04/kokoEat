<template>
  <div>
    <div
      class="d-flex align-items-center justify-content-between beverage--header"
    >
      <h2 class="p-2 mt-5" id="ichimliklar">Beverages</h2>
      <Filter @applyFilter="applyFilter" />
    </div>
    <RangeFilter @filter="emitFilter" />

    <div class="card-wrapper">
      <template v-if="filteredAndSortedItems.length">
        <div v-for="item in filteredAndSortedItems" :key="item.id">
          <Card @pushItem="takeItems(item)" :item="item" />
        </div>
      </template>

      <template v-else>
        <p class="validation">
          There are no beverages that match the filter price.
        </p>
      </template>
    </div>
  </div>
</template>

<script setup>
import { ref, defineEmits, computed } from "vue";
import Card from "./Card.vue";
import Filter from "./Filter.vue";
import RangeFilter from "./RangeFilter.vue";

const items = ref([
  {
    title: "Coca-cola(0.5litr)",
    price: 2.5,
    img: "https://pizzapich.com/wp-content/uploads/2022/09/tovar-2.jpg",
    id: 7,
    count: 0,
  },
  {
    title: "Fuse tea(0.5litr)",
    price: 1.9,
    img: "https://www.psassets.ch/thumbs/bd/22/059754ef02fca59502f09bb23d39-70929_Image0.jpg",
    id: 8,
    count: 0,
  },
  {
    title: "Coca-cola(1litr)",
    price: 3.9,
    img: "https://www.casillowine.com/5100-large_default/coca-cola-1-litro-pet.jpg",
    id: 9,
    count: 0,
  },
  {
    title: "Fanta(0.5litr)",
    price: 1.7,
    img: "https://www.coffeeshop.md/image/cache/catalog/produse/Fanta/fanta-500ml-orange-coffeeshop-md--800x800.jpg",
    id: 10,
    count: 0,
  },
  {
    title: "Sprite(1litr)",
    price: 3.6,
    img: "https://kellysdistributors.com.au/wp-content/uploads/2023/05/1084-1-1.jpg",
    id: 11,
    count: 0,
  },
  {
    title: "Fanta(1litr)",
    price: 3.8,
    img: "https://www.valfresco.com/media/cache/496x496/coca-cola-hbc-hrvatska-doo-fanta-1-l-180014-1.jpg",
    id: 12,
    count: 0,
  },
]);
const emit = defineEmits(["orderListChange"]);

const takeItems = (item) => {
  emit("orderListChange", item);
};

const filter = ref("All");
const minPrice = ref(0);
const maxPrice = ref(60);

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
.beverage--header {
  width: 850px;
}
.validation {
  font-size: 25px;
  font-weight: bold;
  width: 780px;
  text-align: center;
  margin-top: 30px;
}
</style>
