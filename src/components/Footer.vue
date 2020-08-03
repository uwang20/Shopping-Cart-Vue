<template>
  <div class="root-container">
    THIS IS THE ROOT
  </div>
</template>

<script>
export default {
  name: "Footer"
};
</script>

<style scoped>
.root-container {
  width: 100%;
  min-height: 15vh;
  background-color: #1b65f2;
  display: flex;
  align-items: center;
  justify-content: center;
}

@media (min-width: 576px) {
  .root-container {
    height: 15vh;
  }
}
@media (min-width: 768px) {
  .root-container {
    height: 15vh;
  }
}
@media (min-width: 992px) {
  .root-container {
    height: 15vh;
  }
}
@media (min-width: 1200px) {
  .root-container {
    height: 15vh;
  }
}
</style>
