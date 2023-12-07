<script setup>
import { computed } from 'vue'

const props = defineProps({
  variant: { type: String, default: 'default' },
  size: { type: String, default: 'default' }
})

const variantClass = computed(() => {
  return {
    default:
      'bg-transparent text-white hover:text-primary focus:ring-transparent',
    primary: 'bg-primary/80 text-white hover:bg-primary focus:ring-primary/50',
    negative:
      'bg-negative/80 text-white hover:bg-negative focus:ring-negative/50',
    positive:
      'bg-positive/80 text-white hover:bg-positive focus:ring-positive/50'
  }[props.variant]
})

const sizeClass = computed(() => {
  return {
    default: 'h-10 px-6 text-sm',
    sm: 'h-8 px-4 text-sm',
    icon: 'h-10 w-10'
  }[props.size]
})
</script>
<template>
  <button
    class="inline-flex items-center justify-center rounded-md shadow transition-colors duration-200 focus:ring"
    :class="[variantClass, sizeClass]"
  >
    <slot />
  </button>
</template>
