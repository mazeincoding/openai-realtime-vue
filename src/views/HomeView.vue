<script setup lang="ts">
import { ref, computed, onMounted } from "vue";
import Button from "@/components/ui/Button.vue";
import Input from "@/components/ui/Input.vue";

const apiKey = ref("");
const storedApiKey = ref("");

const isKeyModified = computed(() => apiKey.value !== storedApiKey.value);
const isKeyEmpty = computed(() => apiKey.value.trim() === "");

const buttonText = computed(() =>
  isKeyModified.value ? "Set API key" : "Start session"
);

const isButtonDisabled = computed(() => isKeyEmpty.value);

const handleButtonClick = () => {
  if (isKeyModified.value) {
    localStorage.setItem("openai_api_key", apiKey.value);
    storedApiKey.value = apiKey.value;
  } else {
    // Logic for starting the session
    console.log("Starting session with API key:", apiKey.value);
  }
};

const fetchApiKey = () => {
  const storedKey = localStorage.getItem("openai_api_key");
  if (storedKey) {
    apiKey.value = storedKey;
    storedApiKey.value = storedKey;
  }
};

onMounted(fetchApiKey);
</script>

<template>
  <div
    class="flex flex-col items-center justify-center min-h-screen px-8 py-8 sm:px-6 lg:px-8"
  >
    <div class="w-full max-w-md space-y-8">
      <h1 class="text-3xl sm:text-4xl font-bold text-center">Talk with ChatGPT</h1>
      <div class="space-y-4">
        <Input v-model="apiKey" placeholder="Your API key" />
        <Button
          class="w-full"
          @click="handleButtonClick"
          :disabled="isButtonDisabled"
        >
          {{ buttonText }}
        </Button>
      </div>
    </div>
  </div>
</template>
