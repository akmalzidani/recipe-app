<script setup lang="ts">
import { type RecipeResponse } from "~/types/types";
const limit = 12;

const { data, error } = await useFetch<RecipeResponse>(
  `https://dummyjson.com/recipes?limit=${limit}`
);
</script>

<template>
  <main>
    <section class="bg-[#f1f1f1]">
      <div
        class="container flex flex-col items-center gap-10 py-20 lg:flex-row"
      >
        <div class="flex-1 order-2 text-center lg:text-left lg:order-1">
          <h1 class="mb-6 text-4xl font-extrabold lg:text-6xl text-balance">
            Master the Kitchen with Ease: Unlash Your Inner Chef Today!
          </h1>
          <p class="mb-8 text-xl lg:text-2xl text-balance">
            Discover recipes helping you to find the easiest way to cook.
          </p>
          <button
            class="self-start px-4 py-2 text-lg text-white rounded-md cursor-pointer bg-dodgeroll-gold"
          >
            Browse Recipes
          </button>
        </div>
        <div class="flex-1 order-1 lg:order-2">
          <NuxtImg
            src="/nuxt-course-hero.png"
            alt=""
            densities="x1"
            sizes="xs:100vw sm:667px"
            format="webp"
          />
        </div>
      </div>
    </section>
    <section class="container py-20">
      <h2 class="mb-2 text-3xl lg:text-5xl">Discover, Create, Share</h2>
      <p class="mb-8 text-lg lg:text-xl">Check out our most popular recipes!</p>
      <div
        v-if="!error"
        class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-x-4 gap-y-8"
      >
        <div
          v-for="recipe in data?.recipes"
          class="flex flex-col rounded-md shadow"
        >
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
                <Icon
                  name="mdi:clock-time-eight-outline"
                  style="color: #f79f1a"
                />
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
            <NuxtLink
              :to="`/recipes/${recipe.id}`"
              class="self-start px-4 py-2 text-base text-white rounded-md cursor-pointer bg-dodgeroll-gold lg:text-lg"
              >View</NuxtLink
            >
          </div>
        </div>
      </div>
      <p v-else class="text-xl">
        {{ error }}
        Oops, Something went wrong. Please try again later
      </p>
    </section>
  </main>
</template>
