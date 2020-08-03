<template>
  <div>
    <div v-if="isAvailable" class="product-availability">
      <p>{{ `${quantity} items left` }}</p>
    </div>
    <div v-else class="product-availability">
      <p class="out-of-stock">OUT OF STOCK</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Availability",
  props: {
    isAvailable: {
      type: Boolean,
      required: true
    },
    quantity: {
      type: Number,
      required: true
    }
  }
};
</script>

<style scoped>
.product-availability {
  padding: 10px;
  text-align: center;
}

.product-availability p {
  background-color: #65e21e;
  color: white;
  font-size: 1.1rem;
  padding: 5px;
  border-radius: 4px;
  font-weight: bold;
}

.product-availability .out-of-stock {
  background-color: #e93837;
}
</style>
