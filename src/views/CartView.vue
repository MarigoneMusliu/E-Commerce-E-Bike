<script setup>
import OrderSummary from "@/components/OrderSummary.vue";
import PaymentSummary from "@/components/PaymentSummary.vue";
import { computed, ref } from "vue";
import { useCartList } from "@/data/store.js";

const store = useCartList();
const removedFromCartMsg = ref(false);

const clearCart = () => {
  store.clearCart();
};
const removeFromCart = (pId) => {
  store.removeFromCart(pId);

  removedFromCartMsg.value = true;

  setTimeout(() => {
    removedFromCartMsg.value = false;
  }, 700);
};

const productsQtyTotalPrice = computed(() => {
  return store.items.reduce((acc, product) => {
    return acc + product.priceCents * product.quantity;
  }, 0);
});

const totalProductsQuantity = computed(() => {
  return store.items.reduce((acc, product) => acc + product.quantity, 0);
});

const shippingFee = ref(5);
const productsTotal = computed(() =>
  (Math.round(productsQtyTotalPrice.value) / 100).toFixed(2)
);
const totalWithShipping = computed(() =>
  (Math.round(productsQtyTotalPrice.value) / 100 + shippingFee.value).toFixed(2)
);
const tax = computed(() => (totalWithShipping.value * 0.08).toFixed(2));
const orderTotal = computed(() =>
  (parseFloat(totalWithShipping.value) + parseFloat(tax.value)).toFixed(2)
);
</script>

<template>
  <div class="container my-5">
    <div class="row">
      <div
        v-if="store.items.length > 0"
        class="col-xl-8 col-lg-8 col-md-12 col-xs-12 order-2 mb-2"
      >
        <button @click="clearCart" class="btn btn-dark w-100 fw-semibold">
          Remove all products from cart <i class="bi bi-trash3"></i>
        </button>
      </div>
      <div
        class="added-products col-xl-8 col-lg-8 d-flex flex-wrap p-0 order-2 position-relative"
      >
        <div
          v-if="removedFromCartMsg"
          class="removed-message z-1 p-4 position-absolute top-50 start-50 translate-middle border border-2 border-success bg-success-subtle rounded-2 text-success text-center"
        >
          <h2>Removed from cart</h2>
          <i class="bi bi-check2-circle fs-1"></i>
        </div>
        <div
          v-if="store.items.length === 0"
          class="col-xl-7 col-lg-10 col-md-12 col-xs-12 p-4 bg-dark-subtle bg-opacity-15 border border-dark rounded-5 m-auto shadow-lg"
        >
          <h1 class="text-dark text-center fs-4 fw-bold">
            Your cart is empty <i class="bi bi-bag-x"></i>
          </h1>
          <p class="text-dark text-center mt-3">
            Looks like you haven't added anything to your cart yet. Start
            shopping now!
          </p>
        </div>

        <OrderSummary
          v-for="product in store.items"
          :key="product.id"
          :product="product"
          @delete-from-cart="removeFromCart"
        />
      </div>
      <PaymentSummary
        :products="store.items"
        :totalProductsQuantity="totalProductsQuantity"
        :productsTotal="productsTotal"
        :totalWithShipping="totalWithShipping"
        :tax="tax"
        :orderTotal="orderTotal"
      />
    </div>
  </div>
</template>

<style scoped>
.container {
  padding-top: 60px;
}

@media (max-width: 769px) {
  .added-products {
    display: block !important;
  }
}

.bg-dark-subtle {
  background-color: #003366; /* Darker navy blue for empty cart background */
}

.text-dark {
  color: #003366 !important; /* Darker navy blue text */
}

.btn-dark {
  background-color: #003366; /* Darker navy blue button */
  border-color: #003366;
}

.border-dark {
  border-color: #003366 !important; /* Darker navy blue border */
}

.removed-message {
  background-color: #003366; /* Darker navy blue for removed message background */
  color: #fff;
  border-color: #003366;
}

.text-success {
  color: #fff; /* Keeping success text white for visibility */
}

.card-header,
.card-footer {
  background-color: #003366; /* Darker navy blue header/footer */
  color: #fff;
}
</style>
