<script setup>
import { RouterLink, useRouter } from "vue-router";
import { computed, ref, defineEmits, onMounted } from "vue";
import { useCartList, useFavoritesList } from "@/data/store.js";

const storeCart = useCartList();
const storeFavorites = useFavoritesList();

const { cartProducts } = defineProps(["cartProducts"]);
const emits = defineEmits(["search", "resetFilter"]);

const burgerMenu = ref(false);
const search = ref("");
const toggleBurgerMenu = () => {
  burgerMenu.value = !burgerMenu.value;
};

const router = useRouter();
const accountName = ref(JSON.parse(localStorage.getItem("account")) || "");
const isSignedIn = computed(() => !!accountName.value);
const showProfileMenu = ref(false);

const toggleProfileMenu = () => {
  if (!isSignedIn.value) {
    router.push({ path: "/account" });
    return;
  }
  showProfileMenu.value = !showProfileMenu.value;
};

const logout = () => {
  localStorage.removeItem("account");
  localStorage.setItem("showSignupForm", JSON.stringify(true));
  localStorage.setItem("showSignedupCard", JSON.stringify(false));
  accountName.value = "";
  showProfileMenu.value = false;
  window.dispatchEvent(new Event("auth-changed"));
  router.push({ path: "/account" });
};

const totalProductsQuantity = computed(() => {
  return storeCart.items.reduce((acc, product) => acc + product.quantity, 0);
});

const searchProduct = () => {
  emits("search", search.value);
};

const resetFilter = () => {
  search.value = "";
  emits("resetFilter");
};

onMounted(() => {
  window.addEventListener("auth-changed", () => {
    accountName.value = JSON.parse(localStorage.getItem("account")) || "";
  });
});
</script>

<template>
  <nav class="navbar navbar-expand-lg app-navbar fixed-top">
    <div class="container-fluid d-flex justify-content-between">
      <div>
        <RouterLink to="/">
          <img
            src="/logo.png"
            alt="logo"
            class="img-fluid rounded-4 logo-image"
            @click="resetFilter"
          />
        </RouterLink>
      </div>
      <div class="w-50">
        <div class="d-flex" role="search">
          <input
            v-model="search"
            @keyup.enter="searchProduct"
            class="search-input form-control me-2"
            type="search"
            placeholder="Search"
            aria-label="Search"
          />
          <button
            @click="searchProduct"
            class="search-btn btn bg-light text-dark"
          >
            <i class="bi bi-search"></i>
          </button>
        </div>
      </div>
      <div class="right-header">
        <ul class="navbar-nav d-flex align-items-center gap-4">
          <li class="nav-item text-light position-relative">
            <button
              @click="toggleProfileMenu"
              class="btn btn-link text-light p-0 profile-icon"
              title="Profile"
            >
              <i class="bi bi-person fs-2"></i>
            </button>
            <div
              v-if="showProfileMenu"
              class="profile-menu dropdown-menu show position-absolute"
            >
              <p class="dropdown-item mb-0">
                Signed in as <strong>{{ accountName }}</strong>
              </p>
              <button @click="logout" class="dropdown-item">Log out</button>
            </div>
          </li>
          <li class="nav-item">
            <RouterLink
              to="/favorites"
              class="text-light pt-2 position-relative"
              active-class="active"
            >
              <i class="bi-heart fs-2"></i>
              <span
                class="position-absolute top-0 start-100 translate-middle badge rounded-pill bg-light text-dark shadow pt-1 fw-semibold"
              >
                {{ storeFavorites.favoriteItems.length }}
              </span>
            </RouterLink>
          </li>
          <li class="nav-item">
            <RouterLink
              to="/cart"
              class="text-light pt-2 position-relative"
              active-class="active"
            >
              <i class="bi bi-bag fs-2"></i>
              <span
                class="cart-quantity position-absolute top-0 start-100 translate-middle badge rounded-pill bg-light text-dark shadow pt-1 fw-semibold"
              >
                {{ totalProductsQuantity }}
              </span>
            </RouterLink>
          </li>
        </ul>
      </div>
      <div @click="toggleBurgerMenu" class="burger-menu d-none">
        <i v-if="burgerMenu" class="bi bi-x-lg text-light fs-2"></i>
        <i v-else class="bi bi-list text-light fs-2"></i>
      </div>
    </div>
  </nav>

  <div
    v-if="burgerMenu"
    class="menu-items bg-dark fixed-top end-0 d-flex justify-content-center ms-auto rounded-2"
  >
    <ul class="list-inline">
      <li class="text-light position-relative">
        <button
          @click="toggleProfileMenu"
          class="btn btn-link text-light p-0 profile-icon"
          title="Profile"
        >
          <i class="bi bi-person fs-2"></i>
        </button>
        <div v-if="showProfileMenu" class="profile-menu dropdown-menu show">
          <p class="dropdown-item mb-0">
            Signed in as <strong>{{ accountName }}</strong>
          </p>
          <button @click="logout" class="dropdown-item">Log out</button>
        </div>
      </li>
      <li class="nav-item">
        <RouterLink
          to="/favorites"
          class="text-light pt-2 position-relative"
          active-class="active"
        >
          <i class="bi-heart fs-2"></i>
          <span
            class="position-absolute top-0 start-100 translate-middle badge rounded-pill bg-light text-dark shadow pt-1 fw-semibold"
          >
            {{ storeFavorites.favoriteItems.length }}
          </span>
        </RouterLink>
      </li>
      <li class="nav-item">
        <RouterLink
          to="/cart"
          class="text-light pt-2 position-relative"
          active-class="active"
        >
          <i class="bi bi-bag fs-2"></i>
          <span
            class="cart-quantity position-absolute top-0 start-100 translate-middle badge rounded-pill bg-light text-dark shadow pt-1 fw-semibold"
          >
            {{ totalProductsQuantity }}
          </span>
        </RouterLink>
      </li>
    </ul>
  </div>
</template>

<style scoped>
nav.app-navbar {
  background: rgba(8, 10, 20, 0.66);
  backdrop-filter: blur(8px) saturate(120%);
  -webkit-backdrop-filter: blur(8px) saturate(120%);
  box-shadow: 0 6px 24px rgba(2, 6, 23, 0.45);
  padding: 0.45rem 0;
  z-index: 1050;
}

.logo-image {
  width: 64px;
  transition: transform 0.2s ease;
}

.logo-image:hover {
  transform: scale(1.03);
}

.search-input {
  border-radius: 999px;
  padding-left: 14px;
  padding-right: 12px;
  box-shadow: 0 6px 18px rgba(3, 7, 18, 0.12);
}

.search-btn {
  border-radius: 999px;
  margin-left: 6px;
}

.search-btn:hover {
  color: white !important;
  background-color: #1e3a5f !important;
  box-shadow: 2px 2px 20px rgba(0, 0, 0, 0.4);
}

.profile-icon {
  text-decoration: none;
}

.profile-menu {
  min-width: 200px;
  background: rgba(10, 12, 20, 0.96);
  color: #fff;
  border-radius: 10px;
  padding: 6px 0;
  box-shadow: 0 12px 30px rgba(2, 6, 23, 0.45);
  border: 1px solid rgba(255, 255, 255, 0.08);
  right: 0;
  top: 48px;
}

.profile-menu .dropdown-item {
  color: #e6eef8;
  background: transparent;
  border: none;
  width: 100%;
  text-align: left;
}

.profile-menu .dropdown-item:hover {
  background: rgba(255, 255, 255, 0.06);
}

.active:before {
  content: "";
  position: absolute;
  top: 35px;
  width: 100%;
  height: 7%;
  background-color: white;
}

@media (max-width: 995px) {
  .right-header {
    display: none;
  }

  .burger-menu {
    display: block !important;
    cursor: pointer;
  }

  .menu-items {
    margin-top: 64px !important;
    width: 50px;
  }

  .active:before {
    content: "";
    position: absolute;
    top: 35px;
    width: 30px;
    height: 2px;
    background-color: white;
  }
}

@media (max-width: 600px) {
  .active:before {
    content: "";
    position: absolute;
    top: 35px;
    width: 26px;
    height: 2px;
    background-color: white;
  }
}
</style>
