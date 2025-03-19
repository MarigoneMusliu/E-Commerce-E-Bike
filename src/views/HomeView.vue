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
        src="/products-img/header.jpg"
        alt="Hero Image"
        class="img-fluid hero-image-img"
      />
      <div class="overlay">
        <button class="shop-now-btn" @click="scrollToProducts"></button>
        <button class="second-btn" @click="scrollToProducts"></button> <!-- New second button -->
      </div>
    </div>

    <!-- Products Section -->
    <div id="products-section" class="container my-5">
      <!-- Centered text -->
      <div class="products-title">
        <h2>Products</h2>
      </div>
      <div class="row row-cols-xl-4 row-cols-lg-4 row-cols-md-2 row-cols-sm-1 g-4">
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
  bottom: 212px; /* Adjust position as needed */
  left: 145px; /* Move the buttons further to the left */
  display: flex;
  gap: 30px; /* 3 cm (30px) distance between buttons */
}

/* Transparent "SHOP NOW" button */
.shop-now-btn,
.second-btn {
  width: 180px;  /* Increased width */
  height: 50px;  /* Increased height */
  background-color: transparent;
  border: none;  /* No border */
  cursor: pointer;
}

/* Hover effect for both buttons */
.shop-now-btn:hover,
.second-btn:hover {
  background-color: rgba(255, 255, 255, 0.2); /* Light white background when hovered */
}

/* Centering the 'Products' text */
.products-title {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100px;  /* Adjust height as needed */
  margin-bottom: 30px;  /* Space between the title and the products */
}

.products-title h2 {
  font-size: 36px; /* Adjust the font size */
  font-weight: bold;
  color: #333; /* Adjust the color */
}
</style>
