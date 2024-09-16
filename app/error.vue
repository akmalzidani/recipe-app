<script setup lang="ts">
import type { NuxtError } from "#app";

const props = defineProps({
  error: Object as () => NuxtError,
});
</script>

<template>
  <section class="flex flex-col items-center justify-center min-h-screen">
    <h1 class="mb-2 font-bold text-9xl">
      {{ error?.statusCode }}
    </h1>
    <p class="mb-10 text-xl sm:text-3xl">{{ error?.statusMessage }}</p>
    <NuxtLink
      to="/"
      class="px-4 py-2 text-lg text-white rounded-md cursor-pointer bg-dodgeroll-gold"
    >
      Go home
    </NuxtLink>
  </section>
</template>
