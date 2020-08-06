<template>
  <div class="root-container">
    <div class="total-wrapper">
      <h2>Total: {{ `$ ${total.toFixed(2)}` }}</h2>
    </div>
    <ul class="cart-products">
      <li v-for="product in cart" :key="product.id" class="cart-product">
        <div class="cart-image-wrapper">
          <img :src="product.thumbnailPath" alt="product" class="cart-image" />
        </div>
        <div class="cart-product-details">
          <div class="cart-product-name">
            <h2>{{ product.productName }}</h2>
          </div>
          <div>
            <div class="cart-product-price">
              <p>{{ `$ ${product.price.toFixed(2)}` }}</p>
            </div>
            <div class="cart-product-count">
              <div class="decrease-count" @click="removeFromCart(product.id)">
                -
              </div>
              <div class="cart-count">{{ product.count }}</div>
              <div class="increase-count" @click="addToCart(product.id)">+</div>
            </div>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Cart",
  props: {
    cart: {
      type: Array,
      required: true
    },
    total: {
      type: Number,
      required: true
    }
  },
  methods: {
    addToCart(productId) {
      return this.$emit("addToCart", productId);
    },
    removeFromCart(productId) {
      return this.$emit("removeFromCart", productId);
    }
  }
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.root-container {
  background-color: #eee;
  width: 100%;
  min-height: 100vh;
}

.total-wrapper {
  width: 80%;
  margin: auto;
  padding: 50px 15px 0 15px;
}

.cart-products {
  width: 80%;
  margin: auto;
  padding: 15px 15px 20px 15px;

  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: auto;
  grid-gap: 30px;
}

.cart-product {
  background-color: #eee;
  box-shadow: 3px 3px 6px rgba(0, 0, 0, 0.2), -3px -3px 6px #fff;
  border-radius: 6px;
  padding: 6px 10px;
  display: flex;
}

.cart-image-wrapper {
  height: 200px;
  flex: 1.5;
  background-color: red;
}

.cart-image {
  height: 100%;
  width: 100%;
}

.cart-product-details {
  flex: 2;
  padding: 5px 10px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.cart-product-name {
  color: #373737;
}

.cart-product-price {
  border-radius: 6px;
  background-color: #eee;
  box-shadow: 3px 3px 6px rgba(0, 0, 0, 0.2), -3px -3px 6px #fff;
  text-align: center;
  padding: 5px 0;
  margin-top: 10px;
}

.cart-product-count {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 10px;
  border: 2px solid #65e21e;
  border-radius: 5px;
  color: #65e21e;
  padding: 5px;
}

.decrease-count,
.increase-count {
  background-color: #65e21e;
  color: white;
  border-radius: 5px;
  height: 25px;
  width: 25px;
  border-radius: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  box-shadow: 3px 3px 6px rgba(0, 0, 0, 0.2), -3px -3px 6px #fff;
}

.cart-count {
  font-weight: 700;
  font-size: 1.1rem;
}

@media (min-width: 576px) {
  .cart-products {
    width: 80%;
    margin: auto;
    padding: 50px 15px 20px 15px;

    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: auto;
    grid-gap: 30px;
  }
}
@media (min-width: 768px) {
  .cart-products {
    width: 80%;
    margin: auto;
    padding: 50px 15px 20px 15px;

    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: auto;
    grid-gap: 30px;
  }
}
@media (min-width: 992px) {
  .cart-products {
    width: 80%;
    margin: auto;
    padding: 50px 15px 20px 15px;

    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: auto;
    grid-gap: 30px;
  }
}
@media (min-width: 1200px) {
  .cart-products {
    width: 80%;
    margin: auto;
    padding: 50px 15px 20px 15px;

    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: auto;
    grid-gap: 30px;
  }
}
</style>
