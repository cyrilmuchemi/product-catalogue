<script setup>
import ProductCard from './components/ProductCard.vue'
import NavComponent from './components/NavComponent.vue'
import { ref } from 'vue'

const sneakerTotal = ref(0)

const cartTotal = ref([])

const addSneaker = () => {
  sneakerTotal.value += 1
}

const subtractSneaker = () => {
  if (sneakerTotal.value > 0) {
    sneakerTotal.value -= 1
  } else {
    sneakerTotal.value = 0
  }
}

const addToCart = () => {
  if (sneakerTotal.value > 0) {
    if (cartTotal.value.length == 0) {
      cartTotal.value.push(sneakerTotal.value)
    } else {
      cartTotal.value[0] = sneakerTotal.value
    }
  }
}

const clearCart = () => {
  cartTotal.value = []
}
</script>

<template>
  <main>
    <NavComponent :cart-total="cartTotal" @clear-cart="clearCart" />
    <ProductCard
      :sneaker-total="sneakerTotal"
      @increment="addSneaker"
      @decrement="subtractSneaker"
      @add-to-cart="addToCart"
    />
  </main>
</template>

<style scoped></style>
