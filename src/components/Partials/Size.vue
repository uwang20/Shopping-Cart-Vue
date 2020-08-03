<template>
  <ul class="product-sizes">
    <li v-for="(size, index) in sizes" :key="index" class="available-size">
      {{ size }}
    </li>
  </ul>
</template>

<script>
export default {
  name: "Size",
  props: {
    sizes: {
      type: Array,
      required: true
    }
  }
};
</script>

<style scoped>
.product-sizes {
  margin-top: 15px;
  display: flex;
}

.available-size {
  border: 1px solid rgba(0, 0, 0, 0.6);
  border-radius: 3px;
  height: 20px;
  width: 20px;
  margin-right: 5px;

  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
