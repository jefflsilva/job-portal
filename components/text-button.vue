<template>
  <button class="button-default text-button text-white">{{ label }}</button>
</template>
<script lang="ts" setup>
interface Props {
  label: string;
}
const { label } = defineProps<Props>();
</script>
<style scoped>
.text-button {
  background-color: transparent;
}
</style>
