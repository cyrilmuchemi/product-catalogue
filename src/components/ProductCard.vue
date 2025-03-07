<script setup>
import { ref } from 'vue'
import { defineEmits } from 'vue'
import product1 from '@/images/image-product-1.jpg'
import product2 from '@/images/image-product-2.jpg'
import product3 from '@/images/image-product-3.jpg'
import product4 from '@/images/image-product-4.jpg'

import thumb1 from '@/images/image-product-1-thumbnail.jpg'
import thumb2 from '@/images/image-product-2-thumbnail.jpg'
import thumb3 from '@/images/image-product-3-thumbnail.jpg'
import thumb4 from '@/images/image-product-4-thumbnail.jpg'

const selectedImage = ref(product1)
const selectedIndex = ref(0)
defineProps({
  sneakerTotal: Number,
})

const emit = defineEmits(['increment', 'decrement', 'add-to-cart'])

const handleIncrese = () => {
  emit('increment')
}

const handleDecrese = () => {
  emit('decrement')
}

const addToCartHandler = () => {
  emit('add-to-cart')
}

const thumbnails = [
  { thumb: thumb1, full: product1 },
  { thumb: thumb2, full: product2 },
  { thumb: thumb3, full: product3 },
  { thumb: thumb4, full: product4 },
]

const changeImage = (image, index) => {
  selectedImage.value = image
  selectedIndex.value = index
}
</script>

<template>
  <section>
    <div class="container">
      <div class="even-columns">
        <div class="product">
          <div class="product-display">
            <img :src="selectedImage" alt="product image" />
            <div class="swipe-btns">
              <button class="swipeBtn">
                <img src="../images/icon-previous.svg" alt="swipe previous" />
              </button>
              <button class="swipeBtn">
                <img src="../images/icon-next.svg" alt="swipe next" />
              </button>
            </div>
          </div>
          <div class="product-carousel">
            <div
              v-for="(image, index) in thumbnails"
              :key="index"
              @click="changeImage(image.full, index)"
              :class="{ active: selectedIndex === index }"
            >
              <img :src="image.thumb" alt="shoe thumbnail" />
            </div>
          </div>
        </div>
        <div class="content">
          <h1 class="upperCase fw-bold">Sneaker Company</h1>
          <h2 class="fs-heading fw-bold text-dark">Fall Limited Edition Sneakers</h2>
          <p class="pb-10">
            These low profile sneakers are your perfect casual wear companion. Featuring a durable
            rubber outer sole, they'll withstand everything the weather can offer.
          </p>
          <div class="price pb-10">
            <div class="new-price d-flex">
              <p class="fs-semi-heading text-dark fw-bold">$125.00</p>
              <span class="percentage-off text-white bg-dark">50%</span>
            </div>
            <span class="old-price fw-bold">$250</span>
          </div>
          <div class="d-flex cart-logic pt-10">
            <div class="cart-btns fw-bold">
              <button id="minus" @click="handleDecrese">
                <img src="../images/icon-minus.svg" />
              </button>
              <span id="total">{{ sneakerTotal }}</span>
              <button id="plus" @click="handleIncrese">
                <img src="../images/icon-plus.svg" />
              </button>
            </div>
            <div class="cart">
              <button class="Btn fw-bold" @click="addToCartHandler">
                <img class="cart" src="../images/icon-cart.svg" />
                <span>Add to Cart</span>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.product-display img {
  width: 100%;
  display: block;
}

.old-price {
  text-decoration: line-through;
}

.swipe-btns {
  display: none;
}

.even-columns {
  margin-top: 3.8rem;
}

.pb-10 {
  padding-bottom: 1.2rem;
}

.pt-10 {
  padding-top: 1.2rem;
}

.d-flex {
  display: flex;
  align-items: center;
  gap: 1.5rem;
}

.percentage-off {
  border-radius: 10px;
  padding-block: 4px;
  padding-inline: 1rem;
}

.cart-logic {
  align-items: center;
}

#total {
  color: black;
}

#plus {
  outline: none;
  border: none;
}

#minus {
  outline: none;
  border: none;
}

.product-carousel {
  display: grid;
  gap: 1.5rem;
  grid-template-columns: auto auto auto auto;
  margin-top: 1.5rem;
  margin-bottom: 1.5rem;
}

.product-carousel > div > img {
  border-radius: 12px;
  cursor: pointer;
}

.product-carousel > div :hover {
  border: 4px solid hsl(26, 100%, 55%);
}

.product-carousel > div.active {
  border: 4px solid hsl(26, 100%, 55%);
  background-color: hsl(219, 9%, 45%) !important;
  opacity: 0.6;
}

.content {
  margin-top: 4rem;
}

.cart-btns > button {
  cursor: pointer;
}

@media (max-width: 50em) {
  .product-carousel {
    display: none;
  }

  .content {
    margin-top: 0;
  }

  .swipe-btns {
    display: flex;
    justify-content: space-between;
    margin-top: -11rem;
    margin-bottom: 11rem;
    margin-inline: 10px;
  }

  .swipeBtn {
    border-radius: 50%;
    width: 50px;
    height: 50px;
    border: none;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
  }

  #plus {
    outline: none;
    border: none;
    width: 30px;
  }

  #minus {
    outline: none;
    border: none;
    width: 30px;
  }
}
</style>
