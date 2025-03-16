<template>
  <section class="hero-section">
    <div class="main-section">
      <div class="text-white">
        <h1>Find Your Dream Job Today!</h1>
        <p class="text-center">
          Connecting Talent with Opportunity: Your Gateway to Career Success
        </p>
      </div>
    </div>
    <div class="footer-section">logos</div>
  </section>
</template>
<style scoped>
.hero-section {
  min-height: calc(100vh - 64px);
  display: flex;
  flex-direction: column;
}

.hero-section h1 {
  font-size: 64px;
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
</style>
