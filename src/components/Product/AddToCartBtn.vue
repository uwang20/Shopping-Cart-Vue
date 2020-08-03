<template>
  <div
    class="add-to-cart-btn"
    ref="addToCart"
    :class="{ 'justify-between': showBtn }"
  >
    <div
      v-show="showBtn"
      class="remove-product"
      @click="removeFromCart(productId)"
      ref="minus"
    >
      -
    </div>
    <div
      v-if="isAvailable"
      class="add-to-cart-class"
      @click="showCart(isAvailable)"
    >
      ADD TO CART
    </div>
    <div v-else>--</div>
    <div
      v-show="showBtn"
      class="add-product"
      @click="addToCart(productId)"
      ref="plus"
    >
      +
    </div>
  </div>
</template>

<script>
export default {
  name: "AddToCartBtn",
  props: {
    isAvailable: {
      type: Boolean,
      required: true
    },
    productId: {
      type: Number,
      required: true
    }
  },
  data() {
    return {
      showBtn: false
    };
  },
  methods: {
    addToCart(productId) {
      return this.$emit("addToCart", productId);
    },
    removeFromCart(productId) {
      return this.$emit("removeFromCart", productId);
    },
    showCart(isAvailable) {
      // if(this.$refs) return ;
      if (!isAvailable) return;
      this.showBtn = !this.showBtn;
    }
  }
};
</script>

<style scoped>
.add-to-cart-btn {
  background-image: linear-gradient(to right, #1b65f2, #33a6fe);
  color: white;
  border-radius: 0 0 8px 8px;

  display: flex;
  justify-content: center;
  align-items: center;

  padding: 10px;
  cursor: pointer;
}

.justify-between {
  justify-content: space-between;
}
</style>
