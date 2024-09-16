<script setup lang="ts">
import type { Recipe } from "~/types/types";

const route = useRoute();
const { id } = route.params;

const { data, error } = await useFetch<Recipe>(
  `https://dummyjson.com/recipes/${id}`
);
</script>

<template>
  <div class="container flex flex-col max-w-screen-lg py-20">
    <!-- Header -->
    <div class="flex flex-col mb-6">
      <h2 class="mb-4 text-5xl font-semibold">{{ data?.name }}</h2>
      <div class="flex gap-4 mb-6 text-xl">
        <div class="flex items-center gap-1">
          <Icon name="mdi:clock-time-eight-outline" style="color: #f79f1a" />
          <span>{{ data?.cookTimeMinutes }}</span>
        </div>
        <div class="flex items-center gap-1">
          <Icon name="mdi:fire" style="color: #f79f1a" />
          <span>{{ data?.caloriesPerServing }}</span>
        </div>
        <div class="flex items-center gap-1">
          <Icon name="mdi:star" style="color: #f79f1a" />
          <span>{{ data?.rating }} ({{ data?.reviewCount }})</span>
        </div>
      </div>
      <hr />
    </div>

    <!-- Image -->
    <NuxtImg
      :src="data?.image"
      alt=""
      sizes="xs:100vw sm:100vw lg:100vw xl:100vw"
      format="webp"
      densities="x1"
      class="w-full max-h-[500px] object-cover rounded-md shadow-sm mb-12"
    />

    <!-- Ingredients -->
    <div class="mb-8">
      <h2 class="mb-4 text-3xl font-semibold">Ingredients</h2>
      <ul class="grid grid-cols-1 gap-2 text-lg md:grid-cols-2">
        <li v-for="ingredient in data?.ingredients">
          <label class="flex items-center gap-2">
            <input type="checkbox" class="hidden peer" />
            <div
              class="relative flex items-center justify-center w-6 h-6 border-2 rounded-full border-dodgeroll-gold peer-checked:after:absolute peer-checked:after:w-4 peer-checked:after:h-4 peer-checked:after:rounded-full peer-checked:after:bg-dodgeroll-gold"
            ></div>
            <span class="peer-checked:line-through">
              {{ ingredient }}
            </span>
          </label>
        </li>
      </ul>
    </div>

    <!-- Instructions -->
    <div>
      <h2 class="mb-4 text-3xl font-medium">Instructions</h2>
      <ul class="flex flex-col gap-4 text-lg">
        <li
          v-for="(intruction, index) in data?.instructions"
          class="flex gap-2"
        >
          <span
            class="flex items-center justify-center text-sm text-white rounded-full bg-dodgeroll-gold w-7 h-7"
            >{{ index + 1 }}</span
          >
          <span class="flex-1">{{ intruction }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>
