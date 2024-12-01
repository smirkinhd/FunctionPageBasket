<template>
  <div class="cart-item">
    <span>{{ item.name }} (x{{ item.quantity }})</span>
    <span>${{ item.price * item.quantity }}</span>
    <button @click="removeItem">Удалить</button>
  </div>
</template>

<script>
export default {
  name: "CartItem",
  props: {
    item: {
      type: Object,
      required: true,
    },
    onRemove: {
      type: Function,
      required: true,
    },
  },
  methods: {
    removeItem() {
      this.onRemove(this.item.id);
    },
  },
};
</script>

<style scoped>
.cart-item {
  display: flex;
  justify-content: space-between;
  padding: 10px;
  border-bottom: 1px solid #ccc;
}
</style>
