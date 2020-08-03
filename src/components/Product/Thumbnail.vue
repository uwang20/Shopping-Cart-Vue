<template>
  <div class="image-wrapper">
    <img :src="thumbnailPath" alt="" class="product-image" />
    <p class="product-price">{{ `$ ${price.toFixed(2)}` }}</p>
  </div>
</template>

<script>
export default {
  name: "Thumbnail",
  props: {
    price: {
      type: Number,
      required: true
    },
    thumbnailPath: {
      type: String,
      required: true
    }
  }
};
</script>

<style scoped>
.image-wrapper {
  height: 200px;
  width: 100%;
  background-color: orange;

  position: relative;
  border-radius: 8px 8px 0 0;
}

.product-price {
  position: absolute;
  bottom: 3px;
  right: 3px;
  z-index: 5;

  background-color: #f24a65;
  color: white;
  padding: 2px 6px;
  border-radius: 6px 0 0 0;
}

.product-image {
  height: 100%;
  width: 100%;
  border-radius: 8px 8px 0 0;
}
</style>
