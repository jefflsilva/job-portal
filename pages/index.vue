<template>
  <section class="hero-section">
    <div class="main-section">
      <div class="text-white">
        <h1>Find Your Dream Job Today!</h1>
        <p class="text-center">
          Connecting Talent with Opportunity: Your Gateway to Career Success
        </p>
        <div class="inputs-wrapper">
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
            <option disabled value="">Select Category</option>
            <option>A</option>
            <option>B</option>
            <option>C</option>
          </select>
          <span class="button-search">
            <Icon name="mdi:magnify" />Search Job
          </span>
        </div>
      </div>
    </div>
    <div class="footer-section">
      <NuxtImg src="/images/logo_spotify.png" />
      <NuxtImg src="/images/logo_slack.png" />
      <NuxtImg src="/images/logo_adobe.png" />
      <NuxtImg src="/images/logo_asana.png" />
      <NuxtImg src="/images/logo_linear.png" />
    </div>
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
  text-align: center;
  text-wrap: balance;
}

.main-section {
  flex-grow: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

.text-white {
  color: white;
}

.inputs-wrapper {
  margin: 0 auto;
  padding: 0;
  width: 80%;
  height: 80px;
  background-color: var(--white);
  border-radius: 16px 0 0 16px;
  margin-top: 54px;
  font-size: 1.2rem;
  display: flex;
  flex-direction: row;
}

.button-search {
  background-color: var(--primary);
  min-width: 200px;
  border-radius: 0 16px 16px 0;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
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

.footer-section {
  background: black;
  height: 128px;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  flex-wrap: wrap;
  padding: 10px;
}

.footer-section img {
  width: 140px;
  height: auto;
}

@media (max-width: 1024px) {
  .hero-section h1 {
    font-size: 40px;
  }

  .inputs-wrapper {
    flex-direction: column;
    height: auto;
    border-radius: 16px;
    padding: 36px;
    width: 90%;
  }

  .custom-input:first-child {
    border-radius: 0;
  }

  .custom-input:not(:first-child) {
    margin-right: 0;
    margin-bottom: 16px;
  }

  .button-search {
    border-radius: 16px;
    margin-top: 24px;
    padding: 18px 30px;
  }

  .footer-section {
    height: auto;
    justify-content: space-around;
  }

  .footer-section img {
    width: 100px;
    margin: 5px;
  }
}

@media (max-width: 640px) {
  .footer-section img {
    width: 80px;
  }
}
</style>
