<script setup></script>

<template>
  <section>
    <div class="container">
      <div class="even-columns">
        <div class="product">
          <div class="product-display">
            <img src="../images/image-product-1.jpg" alt="product image" />
          </div>
          <div class="product-carousel">
            <div><img src="../images/image-product-1-thumbnail.jpg" alt="shoe thumbnail" /></div>
            <div><img src="../images/image-product-2-thumbnail.jpg" alt="shoe thumbnail" /></div>
            <div><img src="../images/image-product-3-thumbnail.jpg" alt="shoe thumbnail" /></div>
            <div><img src="../images/image-product-4-thumbnail.jpg" alt="shoe thumbnail" /></div>
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
              <button id="minus"><img src="../images/icon-minus.svg" /></button>
              <span id="total">0</span>
              <button id="plus"><img src="../images/icon-plus.svg" /></button>
            </div>
            <button class="Btn fw-bold">
              <img class="cart" src="../images/icon-cart.svg" />
              <span>Add to Cart</span>
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.old-price {
  text-decoration: line-through;
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

.product-carousel > div :hover,
.product-carousel > div :focus-visible {
  border: 4px solid hsl(26, 100%, 55%);
  background-color: hsl(219, 9%, 45%) !important;
}

.content {
  margin-top: 4rem;
}

@media (max-width: 50em) {
  .product-carousel {
    display: none;
  }
}
</style>
