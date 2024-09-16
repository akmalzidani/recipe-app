<script setup lang="ts">
import RecipeCard from "~/components/RecipeCard.vue";
import { type RecipeResponse } from "~/types/types";
const limit = 12;

const { data, error } = await useFetch<RecipeResponse>(
  `https://dummyjson.com/recipes?limit=${limit}`
);

useSeoMeta({
  title: "Nuxtcipes",
  description: "Recipes for you to cook!",
  ogTitle: "Nuxtcipes",
  ogDescription: "Recipes for you to cook!",
  ogImage: "/nuxt-course-hero.png",
  ogUrl: `http:localhost:3000`,
  twitterTitle: "Nuxtcipes",
  twitterDescription: "Recipes for you to cook!",
  twitterImage: "/nuxt-course-hero.png",
  twitterCard: "summary",
});

useHead({
  htmlAttrs: {
    lang: "en",
  },
  link: [
    {
      rel: "icon",
      type: "image/png",
      href: "/favicon.png",
    },
  ],
});
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
        <RecipeCard v-for="recipe in data?.recipes" :recipe="recipe" />
      </div>
      <p v-else class="text-xl">
        {{ error }}
        Oops, Something went wrong. Please try again later
      </p>
    </section>
  </main>
</template>
