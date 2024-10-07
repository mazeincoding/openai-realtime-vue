<script setup lang="ts">
import Button from "@/components/ui/Button.vue";
import Input from "@/components/ui/Input.vue";
</script>

<template>
  <div
    class="flex flex-col items-center justify-center h-screen gap-6 max-w-sm mx-auto w-full"
  >
    <h1 class="text-4xl font-bold">Talk with ChatGPT</h1>
    <div class="space-y-4 w-full">
      <Input placeholder="Your API key" />
      <Button class="w-full">Start session</Button>
    </div>
  </div>
</template>
