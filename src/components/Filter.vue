<template>
  <div class="btn-group mt-5">
    <div class="filter-option" @click="toggleDropdown">
      {{ filter }}
      <i class="bi bi-chevron-down"></i>
    </div>
    <div v-if="isDropdownOpen" class="dropdown">
      <div class="dropdown-item" @click="applyFilter('All')">All </div>
      <div class="dropdown-item" @click="applyFilter('Increase')">Increase</div>
      <div class="dropdown-item" @click="applyFilter('Decrease')">Decrease</div>
    </div>
  </div>
</template>

<script setup>
import { ref, defineEmits } from 'vue';

const filter = ref('All');
const isDropdownOpen = ref(false);

const emit = defineEmits(['applyFilter']);

const applyFilter = (selectedFilter) => {
  filter.value = selectedFilter;
  emit('applyFilter', selectedFilter);
  toggleDropdown();
};

const toggleDropdown = () => {
  isDropdownOpen.value = !isDropdownOpen.value;
};
</script>

<style>
.btn-group {
  position: relative;
}

.filter-option {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0.5rem 1rem;
  background-color: #f8f9fa;
  border: 1px solid #ced4da;
  border-radius: 0.25rem;
  cursor: pointer;
  width: 120px;
}

.dropdown {
  position: absolute;
  top: 100%;
  left: 0;
  width: 100%;
  background-color: #fff;
  border: 1px solid #ced4da;
  border-top: none;
  border-radius: 0 0 0.25rem 0.25rem;
  overflow: hidden;
  z-index: 1;
}

.dropdown-item {
  padding: 0.5rem 1rem;
  cursor: pointer;
}


.dropdown-item:hover {
  background-color: #f8b602;
}
</style>
