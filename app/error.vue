<script setup lang="ts">
import type { NuxtError } from "#app";
import type BaseButton from "./components/BaseButton.vue";

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
    <div>
      <BaseButton to="/" label="Go Home" />
    </div>
  </section>
</template>
