<script setup lang="ts">
import { computed } from 'vue';

interface ButtonProps {
  variant?: 'primary' | 'secondary' | 'outline' | 'ghost';
}

const props = withDefaults(defineProps<ButtonProps>(), {
  variant: 'primary',
});

const buttonClasses = computed(() => {
  const baseClasses = 'px-5 py-2 rounded font-medium transition-colors focus:outline-none text-sm';
  
  const variantClasses = {
    primary: 'bg-primary text-primary-foreground hover:bg-primary/90',
    secondary: 'bg-secondary text-secondary-foreground hover:bg-secondary/80',
    outline: 'border border-input bg-background hover:bg-accent hover:text-accent-foreground',
    ghost: 'hover:bg-accent hover:text-accent-foreground',
  };

  return `${baseClasses} ${variantClasses[props.variant]}`;
});
</script>

<template>
  <button :class="buttonClasses">
    <slot></slot>
  </button>
</template>
