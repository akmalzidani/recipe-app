<script setup lang="ts">
import type { Recipe } from "~/types/types";
import type BaseButton from "./BaseButton.vue";

defineProps<{
  recipe: Recipe;
}>();
</script>

<template>
  <div class="flex flex-col rounded-md shadow">
    <NuxtImg
      :src="recipe.image"
      sizes="xs:100vw sm:50vw lg:400px"
      format="webp"
      densities="x1"
      alt=""
      class="rounded-t-md"
    />
    <div class="flex flex-col flex-1 px-4 py-6">
      <p class="mb-2 text-xl font-semibold lg:text-2xl">
        {{ recipe.name }}
      </p>
      <div
        class="flex w-full gap-8 mt-auto mb-4 text-lg font-normal bg-white/80 lg:text-xl"
      >
        <div class="flex items-center gap-1">
          <Icon name="mdi:clock-time-eight-outline" style="color: #f79f1a" />
          <span>{{ recipe.cookTimeMinutes }}</span>
        </div>
        <div class="flex items-center gap-1">
          <Icon name="mdi:fire" style="color: #f79f1a" />
          <span>{{ recipe.caloriesPerServing }}</span>
        </div>
        <div class="flex items-center gap-1">
          <Icon name="mdi:star" style="color: #f79f1a" />
          <span>{{ recipe.rating }} ({{ recipe.reviewCount }})</span>
        </div>
      </div>
      <BaseButton :to="`/recipes/${recipe.id}`">View</BaseButton>
    </div>
  </div>
</template>
