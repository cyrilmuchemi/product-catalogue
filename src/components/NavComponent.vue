<script setup>
import CartTotal from './slots/CartTotal.vue'
import { ref } from 'vue'
import { defineEmits } from 'vue'

const emit = defineEmits(['clear-cart'])

const clearCart = () => {
  emit('clear-cart')
}

const isNavOpen = ref(false)
const isCartVisible = ref(false)

const toggleNav = () => {
  isNavOpen.value = !isNavOpen.value
}

const props = defineProps({
  cartTotal: Array,
})

const navList = ref([
  { id: 1, value: 'Collections' },
  { id: 2, value: 'Men' },
  { id: 3, value: 'Women' },
  { id: 4, value: 'About' },
  { id: 1, value: 'Contact' },
])

const toggleCart = () => {
  isCartVisible.value = !isCartVisible.value
}
</script>

<template>
  <div class="primary-header">
    <div class="container">
      <div class="nav-wrapper">
        <button
          class="mobile-nav-toggle"
          :aria-expanded="isNavOpen"
          @click="toggleNav"
          aria-controls="primary-navigation"
        >
          <span class="sr-only">Menu</span>
          <img
            class="icon-humburger"
            src="../images/icon-menu.svg"
            alt="open-menu"
            aria-hidden="true"
            :class="{ hidden: isNavOpen }"
          />
          <img
            class="icon-close"
            src="../images/icon-close.svg"
            alt="close-menu"
            aria-hidden="true"
            :class="{ hidden: !isNavOpen }"
          />
        </button>
        <a href="#"><img src="../images/logo.svg" alt="sneakers logo" /></a>
        <nav class="primary-navigation" :class="{ opened: isNavOpen }">
          <ul role="list" class="nav-list" id="primary-navigation">
            <li v-for="list in navList" :key="list.id">
              <a href="#" class="nav-link">{{ list.value }}</a>
            </li>
          </ul>
        </nav>
        <div class="cart-box">
          <div class="cart">
            <img src="../images/icon-cart.svg" alt="shopping cart" @click="toggleCart" width="25" />
            <div v-if="props.cartTotal.length > 0" class="cart-total">{{ props.cartTotal[0] }}</div>
            <div v-else class="cart-total">0</div>
            <CartTotal v-if="isCartVisible">
              <p class="cart-title text-dark">Cart</p>
              <div v-if="props.cartTotal[0] && props.cartTotal[0] > 0">
                <div class="cart-display-total">
                  <div class="cart-thumbnail">
                    <img src="../images/image-product-1-thumbnail.jpg" alt="product thumbnail" />
                  </div>
                  <div class="cart-details">
                    <p>Fall Limited Edition Sneakers</p>
                    <p>
                      $125.00 x <span class="cart-quantity"> {{ props.cartTotal[0] }}</span
                      ><span> ${{ props.cartTotal[0] * 125 }}</span>
                    </p>
                  </div>
                  <button class="cart-delete" @click="clearCart">
                    <img src="../images/icon-delete.svg" alt="delete icon" />
                  </button>
                </div>
                <button class="btn checkout-btn fw-bold">Checkout</button>
              </div>
              <p class="class-empty" v-else>Your Cart is Empty</p>
            </CartTotal>
          </div>
          <div class="avatar">
            <img src="../images/image-avatar.png" alt="avatar" style="width: 45px" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.nav-wrapper {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-top: 1.5rem;
  padding-bottom: 1.5rem;
  border-bottom: 0.5px solid hsl(219, 9%, 45%);
}
.mobile-nav-toggle {
  display: none;
}

ul {
  display: flex;
  align-items: center;
  justify-content: flex-start;
}

.nav-link {
  text-decoration: none;
  color: hsl(219, 9%, 45%);
  padding: 0 30px;
  display: flex;
  align-items: center;
  position: relative;
}

.nav-link:hover {
  color: hsl(0, 0%, 0%);
}

.nav-link:focus {
  color: hsl(0, 0%, 0%);
}

.nav-link::after {
  content: '';
  height: 3px;
  width: 50%;
  background-color: hsl(26, 100%, 55%);
  position: absolute;
  bottom: -40px;
  opacity: 0;
  transition: all 0.3s;
}

.nav-link:hover::after,
.nav-link:focus::after {
  opacity: 1;
}

.cart-box {
  display: flex;
  align-items: center;
  gap: 30px;
}

.cart-box > div,
.cart-box > img {
  cursor: pointer;
}

.avatar {
  width: 55px;
  height: 55px;
  border-radius: 50%;
}

.avatar :hover {
  border: 3px solid hsl(26, 100%, 55%);
}

.cart {
  position: relative;
}

.cart-total {
  position: absolute;
  background-color: hsl(26, 100%, 55%);
  color: #fff;
  border-radius: 60%;
  text-align: center;
  top: 0;
  height: 22px;
  width: 30px;
  margin-top: -15px;
  margin-left: 5px;
}

/* Cart Title */
.cart-title {
  font-weight: bold;
  border-bottom: 1px solid #ddd;
  padding-bottom: 10px;
  margin-bottom: 10px;
}

/* Grid Layout */
.cart-display-total {
  display: grid;
  grid-template-columns: 50px 1fr auto;
  align-items: center;
  gap: 10px;
}

/* Styling Individual Elements */
.cart-thumbnail img {
  width: 50px;
  border-radius: 5px;
}

.cart-quantity {
  font-weight: bold;
}

.cart-display-total {
  font-weight: bold;
  margin-left: 8px;
}

/* Delete Button */
.cart-delete {
  background: none;
  border: none;
  cursor: pointer;
}

.cart-delete img {
  width: 16px;
}

/* Checkout Button */
.checkout-btn {
  width: 100%;
  background: #ff6600;
  color: white;
  padding: 10px;
  border-radius: 5px;
  font-size: 16px;
  cursor: pointer;
  margin-top: 10px;
  border: none;
}

.checkout-btn:hover {
  background: #e65c00;
}

.class-empty {
  text-align: center;
  padding-block: 2rem;
}

@media (max-width: 50em) {
  .primary-navigation {
    display: none;
  }

  .nav-link::after {
    display: none;
  }

  .primary-navigation.opened {
    display: block;
    position: absolute;
    inset: 50px 20px;
    background-color: #fff;
    width: 60%;
    min-height: 1000px;
  }

  .mobile-nav-toggle {
    display: block;
    cursor: pointer;
    background: transparent;
    border: 0;
    padding: 0.5em;
  }

  .icon-humburger.hidden {
    display: none;
  }

  .icon-close.hidden {
    display: none;
  }

  .nav-list {
    display: grid;
    gap: 1.5rem;
    padding: 2rem 1rem;
  }

  a {
    color: hsl(220, 13%, 13%);
    font-weight: 700;
  }

  .cart-display {
    position: absolute;
    top: 0;
    right: 0;
    background: white;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    padding: 1rem;
    border-radius: 8px;
    width: 300px;
  }
}
</style>
