<script setup lang="ts">
import { computed } from 'vue';

interface ButtonProps {
  variant?: 'primary' | 'secondary' | 'outline' | 'ghost';
  disabled?: boolean;
}

const props = withDefaults(defineProps<ButtonProps>(), {
  variant: 'primary',
  disabled: false,
});

const buttonClasses = computed(() => {
  const baseClasses = 'px-5 py-2 rounded font-medium transition-colors focus:outline-none text-sm';
  
  const variantClasses = {
    primary: 'bg-primary text-primary-foreground hover:bg-primary/90',
    secondary: 'bg-secondary text-secondary-foreground hover:bg-secondary/80',
    outline: 'border border-input bg-background hover:bg-accent hover:text-accent-foreground',
    ghost: 'hover:bg-accent hover:text-accent-foreground',
  };

  const disabledClasses = 'opacity-50 cursor-not-allowed pointer-events-none';

  return `${baseClasses} ${variantClasses[props.variant]} ${props.disabled ? disabledClasses : ''}`;
});
</script>

<template>
  <button :class="buttonClasses" :disabled="disabled">
    <slot></slot>
  </button>
</template>
