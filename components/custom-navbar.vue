<template>
  <nav class="navbar">
    <div class="navbar-brand">
      <span class="navbar-logo">
        <Icon :name="icon" />
        <NuxtLink class="text-white" to="/">Job Portal</NuxtLink>
      </span>
    </div>
    <div class="navbar-menu">
      <ul class="navbar-tabs">
        <li
          v-for="map_route in routes"
          :key="map_route.value"
          :class="{ active: activeTab === map_route.value }"
          @click="activeTab = map_route.value"
        >
          <NuxtLink :to="map_route.value">{{ map_route.name }}</NuxtLink>
        </li>
      </ul>
    </div>
    <div class="navbar-end">
      <TextButton label="Login" />
      <PrimaryButton label="Register" />
    </div>
  </nav>
</template>

<script setup>
import { ref, watch } from "vue";
import { useRoute, useRouter } from "#imports";
import TextButton from "./text-button.vue";

const icon = ref("mdi:briefcase-search");
const route = useRoute();
const router = useRouter();
const activeTab = ref(route.query.tab || "");
const routes = ref([
  {
    name: "Home",
    value: "/",
  },
  {
    name: "Jobs",
    value: "/jobs",
  },
  {
    name: "About Us",
    value: "/",
  },
  {
    name: "Contact Us",
    value: "/jobs",
  },
]);

watch(activeTab, (newTab) => {
  router.push(newTab);
});

watch(
  () => route.query.tab,
  (newTab) => {
    if (newTab) {
      activeTab.value = newTab;
    }
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

.navbar-tabs a {
  color: white;
  cursor: pointer !important;
  text-decoration: none;
}

@media (max-width: 1024px) {
  .navbar {
    padding: 0 2rem;
  }

  .navbar-menu {
    display: none;
  }

  .navbar-end {
    display: flex;
    gap: 1rem;
  }
}
</style>
