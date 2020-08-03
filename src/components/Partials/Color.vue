<template>
  <ul class="product-colors">
    <li
      v-for="(color, index) in colors"
      :key="index"
      :style="{ backgroundColor: color }"
      class="available-color"
      :title="color"
    ></li>
  </ul>
</template>

<script>
export default {
  name: "Color",
  props: {
    colors: {
      type: Array,
      required: true
    }
  }
};
</script>

<style scoped>
.product-colors {
  display: flex;
  margin-top: 10px;
}

.available-color {
  width: 20px;
  height: 20px;
  margin-right: 10px;
  border-radius: 50%;
  box-shadow: 1px 1px 5px rgba(0, 0, 0, 0.8);
}
</style>
