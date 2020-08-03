<template>
  <div class="root-container">
    <ul class="products">
      <li
        v-for="product in products"
        :key="product.id"
        class="product"
        :class="{ 'no-stock': !product.isAvailable }"
      >
        <Thumbnail
          :price="product.price"
          :thumbnailPath="product.thumbnailPath"
        />

        <Details :name="product.name" />

        <Availability
          :isAvailable="product.isAvailable"
          :quantity="product.quantity"
        />

        <AddToCartBtn
          :isAvailable="product.isAvailable"
          :productId="product.id"
          @addToCart="addToCart"
          @removeFromCart="removeFromCart"
        />
      </li>
    </ul>
  </div>
</template>

<script>
import Thumbnail from "./Product/Thumbnail.vue";
import Details from "./Product/Details.vue";
import Availability from "./Product/Availability.vue";
import AddToCartBtn from "./Product/AddToCartBtn.vue";

export default {
  name: "Products",
  components: {
    Thumbnail,
    Details,
    Availability,
    AddToCartBtn
  },
  props: {
    products: {
      type: Array,
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

<style>
.root-container * {
  list-style: none;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.root-container {
  width: 100%;
  min-height: 100vh;
  background-color: #eee;
}

.products {
  border-radius: 8px;
  padding: 15px 20px;

  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: auto;
  grid-gap: 15px;
}

.product {
  background-color: #eee;
  border-radius: 8px;
  box-shadow: 4px 4px 7px rgba(0, 0, 0, 0.7), -4px -4px 6px white;

  display: flex;
  flex-direction: column;
  justify-content: space-between;

  margin-bottom: 20px;
}

@media (min-width: 576px) {
  .products {
    width: 90%;
    margin: auto;

    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: auto;
    grid-gap: 25px;

    padding-top: 30px;
  }
}
@media (min-width: 768px) {
  .products {
    width: 90%;
    margin: auto;

    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: auto;
    grid-gap: 25px;

    padding-top: 30px;
  }
}
@media (min-width: 992px) {
  .products {
    width: 90%;
    margin: auto;

    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: auto;
    grid-gap: 25px;

    padding-top: 30px;
  }
}
@media (min-width: 1200px) {
  .products {
    width: 90%;
    margin: auto;

    display: grid;
    grid-template-columns: repeat(5, 1fr);
    grid-template-rows: auto;
    grid-gap: 25px;

    padding-top: 50px;
  }
}
</style>
