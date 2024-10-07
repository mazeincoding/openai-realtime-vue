<script setup lang="ts">
import { useDark, useToggle } from "@vueuse/core";
import Button from "@/components/ui/Button.vue";

const isDark = useDark({
    selector: 'body',
    attributeName: 'class',
    valueDark: 'dark',
    valueLight: 'light',
});
const toggleDark = useToggle(isDark);
</script>

<template>
    <div class="flex flex-col items-center justify-center h-screen bg-background text-foreground gap-4">
        <h1 class="text-4xl font-bold">Welcome to Our App</h1>
        <p class="text-xl">Current theme: {{ isDark ? 'Dark' : 'Light' }}</p>
        <Button 
            @click="toggleDark()" 
        >
            Toggle {{ isDark ? 'Light' : 'Dark' }} Mode
        </Button>
    </div>
</template>
