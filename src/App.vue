<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header class="py-8">
    <slot />
  </header>

  <main>
    <RouterView />
  </main>
</template>
