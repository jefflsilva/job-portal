<template>
  <button class="button-default button-primary text-white">{{ label }}</button>
</template>
<script lang="ts" setup>
interface Props {
  label: string;
}
const { label } = defineProps<Props>();
</script>
<style scoped>
.button-primary {
  background-color: var(--primary);
}
</style>
