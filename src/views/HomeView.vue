<script setup>
import ProductCard from "@/components/ProductCard.vue";

// Props to receive filtered products
const { filteredProducts } = defineProps(["filteredProducts"]);

// Function to scroll to the products section
const scrollToProducts = () => {
  const productsSection = document.getElementById("products-section");
  if (productsSection) {
    productsSection.scrollIntoView({ behavior: "smooth" });
  }
};
</script>

<template>
  <div class="home-page">
    <!-- Horizontal Image Section -->
    <div class="hero-image">
      <img
        src="/products-img/header.svg"
        alt="Hero Image"
        class="img-fluid hero-image-img"
      />
      <div class="overlay">
        <div class="hero-overlay-content">
          <h1>E‑Bike Marketplace</h1>
          <p>Ride cleaner. Ride farther. Discover premium e-bikes.</p>
          <button class="shop-now-btn" @click="scrollToProducts">
            Shop Now
          </button>
        </div>
      </div>
    </div>

    <!-- Highlight Strip -->
    <div class="highlights container">
      <div class="highlight-card">
        <i class="bi bi-truck"></i>
        <div>
          <h5>Fast Delivery</h5>
          <p>Doorstep delivery in 2–5 days.</p>
        </div>
      </div>
      <div class="highlight-card">
        <i class="bi bi-shield-check"></i>
        <div>
          <h5>2‑Year Warranty</h5>
          <p>Ride with confidence and support.</p>
        </div>
      </div>
      <div class="highlight-card">
        <i class="bi bi-headset"></i>
        <div>
          <h5>Expert Support</h5>
          <p>Our team is here 7 days a week.</p>
        </div>
      </div>
    </div>

    <!-- Products Section -->
    <div id="products-section" class="container my-5">
      <!-- Centered text -->
      <div class="products-title">
        <h2>Products</h2>
      </div>
      <div
        class="row row-cols-xl-4 row-cols-lg-4 row-cols-md-2 row-cols-sm-1 g-4"
      >
        <ProductCard
          v-for="product in filteredProducts"
          :key="product.id"
          :product="product"
        />
      </div>
    </div>
  </div>
</template>

<style scoped>
.home-page {
  padding-top: 50px;
  background: linear-gradient(180deg, #f8fafc 0%, #ffffff 60%, #f1f5f9 100%);
}

/* Hero image styling */
.hero-image {
  position: relative;
  width: 100%;
  overflow: hidden;
}

.hero-image-img {
  width: 100%; /* Make the image width 100% of its container */
  height: auto; /* Maintain the aspect ratio */
  object-fit: cover; /* Ensure the image covers the area while maintaining its aspect ratio */
}

/* Position the buttons container */
.hero-image .overlay {
  position: absolute;
  top: 22%;
  right: 8%;
  display: flex;
  align-items: flex-start;
}

.hero-overlay-content {
  color: #fff;
  max-width: 420px;
  text-align: left;
  background: rgba(15, 23, 42, 0.35);
  padding: 18px 20px;
  border-radius: 14px;
  backdrop-filter: blur(6px);
}

.hero-overlay-content h1 {
  font-size: 48px;
  margin: 0 0 8px 0;
  font-weight: 700;
  text-shadow: 0 2px 6px rgba(0, 0, 0, 0.4);
}

.hero-overlay-content p {
  margin: 0 0 16px 0;
  font-size: 18px;
  color: #e6fffa;
}

.shop-now-btn {
  display: inline-block;
  padding: 12px 20px;
  background: linear-gradient(90deg, #0369a1, #0ea5a0);
  color: #ffffff;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-weight: 600;
}

.shop-now-btn:hover {
  background: linear-gradient(90deg, #075985, #0f766e);
}

.highlights {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 16px;
  margin: 24px auto 8px;
}

.highlight-card {
  display: flex;
  gap: 12px;
  align-items: center;
  background: #ffffff;
  border-radius: 14px;
  padding: 16px 18px;
  box-shadow: 0 10px 24px rgba(2, 6, 23, 0.08);
}

.highlight-card i {
  font-size: 26px;
  color: #0ea5a0;
}

.highlight-card h5 {
  margin: 0 0 4px 0;
  font-weight: 700;
}

.highlight-card p {
  margin: 0;
  color: #475569;
  font-size: 14px;
}

@media (max-width: 992px) {
  .highlights {
    grid-template-columns: 1fr;
  }
}

/* Centering the 'Products' text */
.products-title {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100px; /* Adjust height as needed */
  margin-bottom: 30px; /* Space between the title and the products */
}

.products-title h2 {
  font-size: 36px; /* Adjust the font size */
  font-weight: bold;
  color: #333; /* Adjust the color */
}
</style>
