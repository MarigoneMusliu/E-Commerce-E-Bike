<script setup>
const {
  products,
  totalProductsQuantity,
  productsTotal,
  totalWithShipping,
  tax,
  orderTotal,
} = defineProps([
  'products',
  'totalProductsQuantity',
  'productsTotal',
  'totalWithShipping',
  'tax',
  'orderTotal'
])
</script>

<template>
  <section class="col-lg-4 col-md-12 order-lg-2 order-1">
    <div class="payment-summary card shadow-lg mb-3 fw-semibold border-primary">
      <div class="card-header text-light bg-primary">
        Order Details
      </div>
      <div class="card-body">
        <div class="card-text">
          <div class="d-flex justify-content-between mb-2">
            <p>Products (<span class="text-primary">{{ totalProductsQuantity }}</span>):</p>
            <p>{{ productsTotal }} &euro;</p>
          </div>
          <div class="d-flex justify-content-between mb-2">
            <p>Shipping:</p>
            <p v-if="products.length === 0">0 &euro;</p>
            <p v-else>5 &euro;</p>
          </div>
          <div class="d-flex justify-content-between border-primary border-top py-2 mb-2">
            <p>Total without TAX:</p>
            <p v-if="products.length === 0">{{ totalWithShipping = 0 }} &euro;</p>
            <p v-else>{{ totalWithShipping }} &euro;</p>
          </div>
          <div class="d-flex justify-content-between mb-2">
            <p>TAX (8%):</p>
            <p v-if="products.length === 0">{{ tax = 0 }} &euro;</p>
            <p v-else>{{ tax }} &euro;</p>
          </div>
        </div>
      </div>
      <div class="card-footer border-top border-5 border-primary">
        <div class="d-flex justify-content-between text-primary">
          <h5 class="fw-semibold">Order Total</h5>
          <h5 v-if="products.length === 0">{{ orderTotal = 0 }} &euro;</h5>
          <h5 v-else class="fw-semibold">{{ orderTotal }} &euro;</h5>
        </div>
        <button class="btn btn-primary w-100 fs-5 fw-semibold my-3">
          Order Now
        </button>
      </div>
    </div>
  </section>
</template>

<style scoped>
.card-header {
  background-color: #003366; /* Navy blue */
  color: #fff;
}

.card-body {
  font-size: 1rem;
  color: #333;
}

.card-footer {
  background-color: #f8f9fa;
  border-top: 5px solid #003366; /* Navy blue */
}

.text-primary {
  color: #003366 !important; /* Navy blue text */
}

.btn-primary {
  background-color: #003366;
  border-color: #003366;
}

.card {
  border: 1px solid #003366; /* Navy blue border */
  border-radius: 10px;
}

.card-text p {
  font-weight: 500;
}

.card-footer h5 {
  font-weight: 600;
}

.card-footer button {
  font-weight: 600;
}
</style>
