<template>
  <section class="hero-section">
    <div class="main-section">
      <div class="text-white">
        <h1>Find Your Dream Job Today!</h1>
        <p class="text-center">
          Connecting Talent with Opportunity: Your Gateway to Career Success
        </p>
        <div class="d-flex justify-content-center inputs-wrapper">
          <input
            v-model="inputValue"
            placeholder="Job Title or Company"
            type="text"
            class="input-default border-none custom-input"
          />
          <CustomDivider />

          <select
            v-model="selectedLocation"
            class="input-default border-none custom-input"
          >
            <option disabled value="">Select Location</option>
            <option>A</option>
            <option>B</option>
            <option>C</option>
          </select>
          <CustomDivider />
          <select
            v-model="selectedCategory"
            class="input-default border-none custom-input"
          >
            <option disabled value="">Select Location</option>
            <option>A</option>
            <option>B</option>
            <option>C</option>
          </select>
          <span
            class="d-flex align-items-center justify-content-center button-search"
          >
            <Icon name="mdi-search" />Search Job
          </span>
        </div>
      </div>
    </div>
    <div class="footer-section">logos</div>
  </section>
</template>
<script lang="ts" setup>
const selectedLocation = ref("");
const selectedCategory = ref("");
const inputValue = ref("");
</script>
<style scoped>
.hero-section {
  min-height: calc(100vh - 64px);
  display: flex;
  flex-direction: column;
}

.hero-section h1 {
  font-size: 80px;
  margin-bottom: 16px;
}

.main-section {
  flex-grow: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

.footer-section {
  background: black;
  height: 128px;
}

.inputs-wrapper {
  margin: 0 auto;
  padding: 0;
  width: 100%;
  height: 80px;
  background-color: var(--white);
  width: 80%;
  border-radius: 16px 0 0 16px;
  margin-top: 54px;
  font-size: 1.2rem;
}

.button-search {
  background-color: var(--primary);
  min-width: 200px;
  border-radius: 0 16px 16px 0;
  cursor: pointer;
}

.custom-input {
  padding: 18px 30px;
  font-size: 1rem;
  color: var(--grey);
}
.custom-input::placeholder {
  color: var(--grey);
}
.custom-input:not(:first-child) {
  margin-right: 16px;
}
.custom-input:first-child {
  border-radius: 16px 0 0 16px;
}
</style>
