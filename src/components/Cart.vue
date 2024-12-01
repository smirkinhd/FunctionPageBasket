<template>
  <div class="cart">
    <h2>Корзина</h2>
    <div v-if="cartItems.length > 0">
      <CartItem
        v-for="item in cartItems"
        :key="item.id"
        :item="item"
        :onRemove="removeFromCart"
      />
    </div>
    <p v-else>Корзина пуста</p>
    <h3>Итого: ${{ totalPrice }}</h3>
    <button @click="addExampleItem">Добавить пример товара</button>
  </div>
</template>

<script>
import CartItem from "./CartItem.vue";

export default {
  name: "ShoppingCart",
  components: {
    CartItem,
  },
  data() {
    return {
      cartItems: [],
    };
  },
  computed: {
    totalPrice() {
      return this.cartItems.reduce(
        (total, item) => total + item.price * item.quantity,
        0
      );
    },
  },
  methods: {
    addExampleItem() {
      const exampleItem = { id: 1, name: "Пример товара", price: 10 };
      const existingItem = this.cartItems.find((item) => item.id === exampleItem.id);
      if (existingItem) {
        existingItem.quantity += 1;
      } else {
        this.cartItems.push({ ...exampleItem, quantity: 1 });
      }
    },
    removeFromCart(itemId) {
      this.cartItems = this.cartItems.filter((item) => item.id !== itemId);
    },
  },
};
</script>

<style scoped>
.cart {
  width: 400px;
  margin: 20px auto;
  border: 1px solid #ccc;
  padding: 10px;
}
</style>
