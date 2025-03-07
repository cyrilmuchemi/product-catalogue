<template>
  <div class="cart-display">
    <slot></slot>
  </div>
</template>

<style scoped>
.cart-display {
  position: absolute;
  top: 100%;
  right: 0;
  width: 300px;
  background: white;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
  border-radius: 10px;
  padding: 15px;
  z-index: 10;
}
</style>
