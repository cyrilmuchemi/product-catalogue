<script setup>
import { ref } from 'vue'

const isNavOpen = ref(false)

const toggleNav = () => {
  isNavOpen.value = !isNavOpen.value
}

const navList = ref([
  { id: 1, value: 'Collections' },
  { id: 2, value: 'Men' },
  { id: 3, value: 'Women' },
  { id: 4, value: 'About' },
  { id: 1, value: 'Contact' },
])
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
        <a href="#"><img src="../images/logo.svg" alt="sneaker logo" /></a>
        <nav class="primary-navigation" :class="{ opened: isNavOpen }">
          <ul role="list" class="nav-list" id="primary-navigation">
            <li v-for="list in navList" :key="list.id">
              <a href="#">{{ list.value }}</a>
            </li>
          </ul>
        </nav>
        <div class="cart-box">
          <div class="cart"><img src="../images/icon-cart.svg" alt="shopping cart" /></div>
          <div class="avatar">
            <img src="../images/image-avatar.png" alt="profile picture" style="width: 55px" />
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
}

.mobile-nav-toggle {
  display: none;
}

ul {
  display: flex;
  align-items: center;
  justify-content: flex-start;
}

a {
  text-decoration: none;
  color: hsl(219, 9%, 45%);
  padding: 0 30px;
  display: flex;
  align-items: center;
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

@media (max-width: 50em) {
  .primary-navigation {
    display: none;
  }

  .primary-navigation.opened {
    display: block;
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

  a {
    color: hsl(220, 13%, 13%);
  }
}
</style>
