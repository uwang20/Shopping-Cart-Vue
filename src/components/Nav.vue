<template>
  <div class="nav">
    <div class="inner-wrapper">
      <h1 class="logo">Shopping Cart</h1>
      <h1 @click="openCart" class="cart">
        CART
        <div class="product-count">
          {{ cartCount }}
        </div>
      </h1>
    </div>
  </div>
</template>

<script>
export default {
  name: "Nav",
  props: {
    cartCount: {
      type: Number,
      required: true
    }
  },
  created() {
    console.log(this.cartCount);
  },
  methods: {
    openCart() {
      this.$emit("openCart");
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.nav {
  height: 10vh;
  width: 100%;
  background-color: #1b65f2;
  cursor: pointer;
}

.inner-wrapper {
  width: 90%;
  height: 100%;
  color: white;
  margin: auto;

  display: flex;
  justify-content: space-between;
  align-items: center;
}

.inner-wrapper .logo {
  font-size: 1.1rem;
  position: relative;
}

.inner-wrapper .cart {
  font-size: 1rem;
  position: relative;
}

.product-count {
  position: absolute;
  right: 0;
  bottom: 0;
  transform: translate(50%, 50%);
  background-color: #f24a65;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  color: white;
  font-size: 0.9rem;

  display: flex;
  justify-content: center;
  align-items: center;
}

@media (min-width: 576px) {
  .inner-wrapper {
    width: 80%;
  }

  .inner-wrapper .logo {
    font-size: 1.6rem;
  }

  .inner-wrapper .cart {
    font-size: 1.2rem;
    position: relative;
  }
}
@media (min-width: 768px) {
  .inner-wrapper {
    width: 80%;
  }

  .inner-wrapper .logo {
    font-size: 1.6rem;
  }

  .inner-wrapper .cart {
    font-size: 1.2rem;
    position: relative;
  }
}

@media (min-width: 992px) {
  .inner-wrapper {
    width: 80%;
  }

  .inner-wrapper .logo {
    font-size: 1.6rem;
  }

  .inner-wrapper .cart {
    font-size: 1.2rem;
    position: relative;
  }
}

@media (min-width: 1200px) {
  .inner-wrapper {
    width: 80%;
  }

  .inner-wrapper .logo {
    font-size: 1.6rem;
  }

  .inner-wrapper .cart {
    font-size: 1.2rem;
    position: relative;
  }
}
</style>
