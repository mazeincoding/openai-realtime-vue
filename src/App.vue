<script setup lang="ts">
import { onMounted } from 'vue';

onMounted(() => {
  // This runs after the component is mounted
  if (typeof document !== "undefined") {
    document.documentElement.classList.add("light");
  }
});
</script>

<template>
  <router-view />
</template>
