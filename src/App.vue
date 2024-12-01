<template>
  <div id="app">
    <h1>Интернет-магазин</h1>
    <ShoppingCart />
  </div>
</template>

<script>
import ShoppingCart from "./components/Cart.vue";

export default {
  name: "App",
  components: {
    ShoppingCart,
  },
};
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  margin-top: 20px;
}
</style>
