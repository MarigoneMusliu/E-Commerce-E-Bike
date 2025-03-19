<script setup>
import { useFavoritesList } from "@/data/store.js";
import FavoriteProductCard from "@/components/FavoriteProductCard.vue";

const storeFavorites = useFavoritesList();

const removeAllFavorites = () => {
  storeFavorites.removeAllFavorites();
};
</script>

<template>
  <div class="favorites-container container my-5">
    <div v-if="storeFavorites.favoriteItems.length > 0" class="row">
      <div class="col-12">
        <button
          @click="removeAllFavorites"
          class="btn btn-danger w-100 fw-semibold py-3 shadow-sm remove-all-btn"
        >
          <i class="bi bi-trash3"></i> Remove All Favorite Products
        </button>
      </div>
    </div>

    <!-- No Favorites Message -->
    <div
      v-if="storeFavorites.favoriteItems.length === 0"
      class="no-favorite-msg d-flex justify-content-center align-items-center col-12 p-4 bg-light rounded-3 shadow-sm"
    >
      <h1 class="text-muted text-center">
        No favorite products found here <i class="bi bi-search-heart"></i>
      </h1>
    </div>

    <!-- Favorite Products -->
    <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4 g-4">
      <FavoriteProductCard
        v-for="favoriteProduct in storeFavorites.favoriteItems"
        :key="favoriteProduct.id"
        :favoriteProduct="favoriteProduct"
      />
    </div>
  </div>
</template>

<style scoped>
.favorites-container {
  padding-top: 60px;
  min-height: 60vh;
  max-width: 1200px;
  margin: 0 auto;
}

/* Button Styling */
.remove-all-btn {
  background-color: #ff4d4d;
  color: white;
  transition: all 0.3s ease;
}

.remove-all-btn:hover {
  background-color: #e60000;
  transform: scale(1.05);
}

.remove-all-btn i {
  margin-right: 10px;
}

/* No Favorite Message Styling */
.no-favorite-msg {
  height: 50vh;
  background-color: #f8f9fa;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.no-favorite-msg h1 {
  font-size: 24px;
  color: #6c757d;
}

.no-favorite-msg i {
  margin-left: 10px;
}

/* Product Grid Styling */
.row-cols-1 {
  margin-top: 20px;
}

.row-cols-1 .col {
  display: flex;
  justify-content: center;
  align-items: center;
}

@media (min-width: 576px) {
  .row-cols-sm-2 {
    margin-top: 20px;
  }
}

@media (min-width: 768px) {
  .row-cols-md-3 {
    margin-top: 20px;
  }
}

@media (min-width: 992px) {
  .row-cols-lg-4 {
    margin-top: 20px;
  }
}
</style>
