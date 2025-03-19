<template>
  <nav class="navbar">
    <div class="navbar-brand">
      <span class="navbar-logo">
        <Icon :name="icon" />
        <NuxtLink class="text-white" to="/">Job Portal</NuxtLink>
      </span>
    </div>
    <div class="navbar-menu" :class="{ 'is-active': isMenuOpen }">
      <ul class="navbar-tabs">
        <li
          v-for="map_route in routes"
          :key="map_route.value"
          :class="{ active: activeTab === map_route.value }"
          @click="handleTabClick(map_route.value)"
        >
          <NuxtLink :to="map_route.value">{{ map_route.name }}</NuxtLink>
        </li>
      </ul>
    </div>
    <div class="navbar-end">
      <TextButton label="Login" />
      <PrimaryButton label="Register" />
      <button class="navbar-toggle" @click="toggleMenu">
        <span class="hamburger"></span>
      </button>
    </div>
  </nav>
</template>

<script setup>
import { ref, watch } from "vue";
import { useRoute, useRouter } from "#imports";

const icon = ref("mdi:briefcase-search");
const route = useRoute();
const router = useRouter();
const activeTab = ref(route.path || "/");
const isMenuOpen = ref(false);

const routes = ref([
  { name: "Home", value: "/" },
  { name: "Jobs", value: "/jobs" },
  { name: "About Us", value: "/about" },
  { name: "Contact Us", value: "/contact" },
]);

const handleTabClick = (tabValue) => {
  activeTab.value = tabValue;
  isMenuOpen.value = false;
};

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

watch(activeTab, (newTab) => {
  router.push(newTab);
});

watch(
  () => route.path,
  (newPath) => {
    activeTab.value = newPath;
  }
);
</script>

<style scoped>
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 4rem;
  color: white;
  height: 64px;
  background-color: transparent;
  position: relative;
}

.navbar-brand {
  display: flex;
  align-items: center;
}

.navbar-logo {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 24px;
}

.navbar-logo a {
  text-decoration: none;
}

.navbar-menu {
  display: flex;
}

.navbar-tabs {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
}

.navbar-tabs li {
  padding: 0 16px;
  cursor: pointer;
  height: 64px;
  display: flex;
  align-items: center;
  position: relative;
}

.navbar-tabs li.active::after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 16px;
  width: calc(100% - 32px);
  height: 2px;
  background-color: white;
}

.navbar-tabs a {
  color: white;
  text-decoration: none;
  cursor: pointer !important;
}

.navbar-end {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.navbar-toggle {
  display: none;
  background: none;
  border: none;
  cursor: pointer;
  padding: 10px;
}

.hamburger {
  display: block;
  width: 25px;
  height: 3px;
  background: white;
  position: relative;
}

.hamburger::before,
.hamburger::after {
  content: "";
  position: absolute;
  width: 25px;
  height: 3px;
  background: white;
  transition: all 0.3s ease;
}

.hamburger::before {
  top: -8px;
}

.hamburger::after {
  bottom: -8px;
}

@media (max-width: 1024px) {
  .navbar {
    padding: 0 2rem;
  }

  .navbar-menu {
    display: none;
    position: absolute;
    top: 64px;
    left: 0;
    width: 100%;
    background-color: #333;
    flex-direction: column;
    padding: 1rem 0;
    z-index: 1000;
  }

  .navbar-menu.is-active {
    display: flex;
  }

  .navbar-tabs {
    flex-direction: column;
    width: 100%;
  }

  .navbar-tabs li {
    padding: 12px 2rem;
    height: auto;
    justify-content: flex-start;
  }

  .navbar-tabs li.active::after {
    left: 2rem;
    width: calc(100% - 4rem);
  }

  .navbar-toggle {
    display: block;
  }

  .navbar-end {
    gap: 0.5rem;
  }
}

@media (max-width: 640px) {
  .navbar {
    padding: 0 1rem;
  }

  .navbar-logo {
    font-size: 20px;
  }

  .navbar-end {
    gap: 0.25rem;
  }
}
</style>
