<template>
  <div class="container">
    <CustomNavbar />
    <slot />
  </div>
</template>

<style scoped>
.container {
  position: relative;
  width: 100%;
  height: 100vh;
  overflow-x: hidden;
}

.container::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: url("../public/images/main-bg-image.jpg") center/cover no-repeat;
  filter: blur(30px);
  z-index: -1;
}
.container h1 {
  color: white;
}

.container::after {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.8);
  z-index: -1;
}
</style>
