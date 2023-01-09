<template>
  <button type="button" class="rounded-full p-1 ml-3 text-gray-900 dark:text-gray-400 hover:bg-gray-700 hover:text-white focus:outline-none">
    <span class="sr-only">View notifications</span>
    <BellIcon class="h-6 w-6" aria-hidden="true" />
  </button>
</template>

<script setup lang="ts">
import { BellIcon } from '@heroicons/vue/24/outline'
</script>
