<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header class="py-8">
    <nav class="flex gap-2">
      <RouterLink to="/" class="px-4 py-2 rounded text-gray-700 bg-gray-200">Home</RouterLink>
      <RouterLink to="/about" class="px-4 py-2 rounded text-gray-700 bg-gray-200">About</RouterLink>
    </nav>
  </header>

  <main>
    <RouterView />
  </main>
</template>
