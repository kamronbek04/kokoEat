<template>
  <div class="sidebar">
    <h2>Menu</h2>
    <div class="d-flex flex-column align-items-center">
      <template v-for="(item, i) in sidebarItem" :key="item.name">
        <a
          :href="`#${item.path}`"
          class="sidebar--item"
          @click="setSelected(i)"
          :class="{ selected: item.name === selected }"
        >
          <div class="d-flex align-items-center flex-row gap-2">
            <span>
              {{ item.name }}
            </span>
          </div>
        </a>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selected: "Dashboard",
      sidebarItem: [
        {
          path: "asosiy",
          name: "Dashboard",
        },
        {
          path: "aksiyalar",
          name: "Discount",
        },
        {
          path: "mahsulotlar",
          name: "Products",
        },
        {
          path: "ichimliklar",
          name: "Beverages",
        },
      ],
    };
  },
  methods: {
    setSelected(index) {
      this.selected = this.sidebarItem[index].name;
    },
  },
};
</script>

<style scoped>
.sidebar {
  position: fixed;
  top: 100px;
  bottom: 0;
  left: 0;
  overflow-y: auto;
  width: 280px;

  background-color: #fcfcfc;
  border-radius: 20px;
  padding: 20px;
}
.sidebar h2 {
  text-align: center;
  margin-bottom: 30px;
}
.sidebar--item {
  margin-bottom: 30px;
  padding: 10px;
  width: 200px;
  border-radius: 16px;

  color: #495057;
}
.sidebar--item div span {
  opacity: 1;
  margin-top: 7px;
  font-size: 20px;
  width: 100%;
  display: inline-block;
}
.selected {
  background-color: #f8b602;
  color: #fff;
}
</style>
