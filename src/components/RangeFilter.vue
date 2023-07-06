<template>
  <div class="range-filter">
    <div class="wrapper">
      <header>
        <h2>Price Range</h2>
      </header>

      <div class="price-input">
        <div class="field">
          <span>Min</span>
          <input type="number" v-model="minPrice" class="input-min" />
        </div>
        <div class="separator">-</div>
        <div class="field">
          <span>Max</span>
          <input type="number" v-model="maxPrice" class="input-max" />
        </div>
      </div>

      <div class="slider">
        <div
          class="progress"
          :style="{ left: minRangeStyle, right: maxRangeStyle }"
        ></div>
      </div>
      <div class="range-input">
        <input
          type="range"
          v-model="minPrice"
          class="range-min"
          min="0"
          max="60"
          step="0.1"
        />
        <input
          type="range"
          v-model="maxPrice"
          class="range-max"
          min="0"
          max="60"
          step="0.1"
        />
      </div>
      <button @click="emitFilter" class="btn--filter">Filter</button>
    </div>
  </div>
</template>

<script setup>
import { ref, computed, defineEmits, watch } from "vue";

const minPrice = ref(0);
const maxPrice = ref(60.0);
const priceGap = 0.1;

const minRangeStyle = computed(
  () => `${((minPrice.value - 0.1) / (60 - 0.1)) * 100}%`
);
const maxRangeStyle = computed(
  () => `${100 - ((maxPrice.value - 0.1) / (60 - 0.1)) * 100}%`
);

const emit = defineEmits(["filter"]);

const emitFilter = () => {
  emit("filter", {
    minRange: minPrice.value,
    maxRange: maxPrice.value,
  });
  // console.log(minPrice.value);
};

watch([minPrice, maxPrice], ([newMin, newMax]) => {
  if (newMax - newMin >= priceGap && newMin >= 0 && newMax <= 60) {
    return;
  }
  if (newMin < 0) {
    minPrice.value = 0;
  }
  if (newMax > 60) {
    maxPrice.value = 60;
  }
});
</script>

<style scoped>
.range-filter {
  width: 700px;
  margin: 0 auto;
}
.wrapper {
  width: 400px;
  background: #fff;
  border-radius: 10px;
  padding: 20px;
  box-shadow: 0 12px 35px rgba(0, 0, 0, 0.1);
}
header h2 {
  font-size: 24px;
  font-weight: 600;
}
.price-input {
  width: 100%;
  display: flex;
  margin: 15px 0 15px;
}
.price-input .field {
  display: flex;
  width: 100%;
  height: 35px;
  align-items: center;
}
.field input {
  width: 100%;
  height: 100%;
  outline: none;
  font-size: 19px;
  margin-left: 12px;
  border-radius: 5px;
  text-align: center;
  border: 1px solid #999;
}
input[type="number"]::-webkit-outer-spin-button,
input[type="number"]::-webkit-inner-spin-button {
  -webkit-appearance: none;
}
.price-input .separator {
  width: 130px;
  display: flex;
  font-size: 19px;
  align-items: center;
  justify-content: center;
}
.slider {
  height: 5px;
  position: relative;
  background: #ddd;
  border-radius: 5px;
}
.slider .progress {
  height: 100%;
  left: 25%;
  right: 25%;
  position: absolute;
  border-radius: 5px;
  background: #ffd43b;
}
.range-input {
  position: relative;
}
.range-input input {
  position: absolute;
  width: 100%;
  height: 5px;
  top: -5px;
  background: none;
  pointer-events: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}
input[type="range"]::-webkit-slider-thumb {
  height: 17px;
  width: 17px;
  border-radius: 50%;
  background: #ffd43b;
  pointer-events: auto;
  -webkit-appearance: none;
  box-shadow: 0 0 6px rgba(0, 0, 0, 0.05);
}
input[type="range"]::-moz-range-thumb {
  height: 17px;
  width: 17px;
  border: none;
  border-radius: 50%;
  background: #ffd43b;
  pointer-events: auto;
  -moz-appearance: none;
  box-shadow: 0 0 6px rgba(0, 0, 0, 0.05);
}
.btn--filter {
  background-color: #ffd43b;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  margin-left: 280px;
  margin-top: 20px;
}
</style>
