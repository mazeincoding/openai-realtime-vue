<script lang="ts">
import { createApp } from "vue";

createApp({
  setup() {
    // This runs before the component is mounted
    if (typeof document !== "undefined") {
      document.documentElement.classList.add("light");
    }
  },
}).mount("#app");
</script>

<template>
  <router-view />
</template>
