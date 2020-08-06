/* eslint-disable prettier/prettier */
<template>
  <div id="app">
    <Nav @openCart="openCart" :cartCount="cart.length" />
    <Products
      v-if="!isCartOpen"
      :products="products"
      @addToCart="addToCart"
      @removeFromCart="removeFromCart"
    />
    <Cart
      v-else
      :cart="cart"
      :total="totalProducts"
      @addToCart="addToCart"
      @removeFromCart="removeFromCart"
    />
    <Footer />
  </div>
</template>

<script>
import Nav from "./components/Nav.vue";
import Products from "./components/Products.vue";
import Cart from "./components/Cart.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "App",
  components: {
    Nav,
    Products,
    Footer,
    Cart
  },
  mounted() {
    console.log(this.totalProducts);
  },
  data() {
    return {
      products: [
        {
          id: 0,
          name: "T-shirt",
          price: 350,
          isAvailable: false,
          quantity: 0,
          thumbnailPath: require("../public/shirt.jpg")
        },
        {
          id: 1,
          name: "Shoe",
          price: 899,
          isAvailable: true,
          quantity: 4,
          thumbnailPath: require("../public/shoes.jpg")
        },
        {
          id: 2,
          name: "Headphone",
          price: 500,
          isAvailable: true,
          quantity: 5,
          thumbnailPath: require("../public/headphone.jpg")
        }
      ],
      isCartOpen: false,
      cart: [
        {
          id: 2,
          productName: "Headphone",
          price: 500,
          count: 1,
          thumbnailPath: require("../public/headphone.jpg")
        },
        {
          id: 0,
          productName: "T-shirt",
          price: 700,
          count: 2,
          thumbnailPath: require("../public/shirt.jpg")
        }
      ]
    };
  },
  methods: {
    openCart() {
      this.isCartOpen = !this.isCartOpen;
    },
    addToCart(productId) {
      let addedProduct = null;

      this.products.forEach(product => {
        if (product.id === productId) {
          if (product.quantity === 0) return;

          product.quantity--;
          if (product.quantity === 0) {
            product.isAvailable = false;
          }

          addedProduct = this.products.find(product => {
            return product.id === productId;
          });

          if (this.cart.some(prod => prod.id === productId)) {
            this.cart.forEach(cartProduct => {
              if (cartProduct.id === productId) {
                cartProduct.count++;
                cartProduct.price += addedProduct.price;
              }
            });
            return;
          }

          this.cart.push({
            id: addedProduct.id,
            productName: addedProduct.name,
            price: addedProduct.price,
            count: 1,
            thumbnailPath: addedProduct.thumbnailPath
          });
        }
      });
    },
    removeFromCart(productId) {
      let newCart = null;

      let removeProduct = this.cart.find(prod => {
        return prod.id === productId;
      });

      if (typeof removeProduct === "undefined") {
        return;
      } else {
        if (removeProduct.count === 1) {
          newCart = this.cart.filter(prod => {
            return prod.id !== productId;
          });

          this.products.forEach(prod => {
            if (prod.id === productId) {
              prod.quantity++;
            }
          });

          this.cart = newCart;
        } else {
          this.products.forEach(prod => {
            if (prod.id === productId) {
              prod.quantity++;
              if (prod.quantity > 0) {
                prod.isAvailable = true;
              }
            }
          });

          this.cart.forEach(prod => {
            let choosenProduct = this.products.find(prod => {
              return prod.id === productId;
            });

            if (prod.id === productId) {
              prod.count--;
              prod.price -= choosenProduct.price;
            }
          });
        }
      }
    }
  },
  computed: {
    totalProducts() {
      let total = 0;
      this.cart.forEach(product => {
        total += product.price;
      });

      return total;
    }
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
