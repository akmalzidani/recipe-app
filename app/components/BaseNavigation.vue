<script setup></script>

<template>
  <header class="py-4 border-b">
    <nav class="container flex items-center">
      <NuxtLink to="/" class="flex items-center gap-1">
        <NuxtImg
          src="/icon-green.png"
          width="56px"
          densities="x1"
          format="webp"
          alt=""
        />
        <span class="text-3xl font-bold">Nuxtcipes</span>
      </NuxtLink>
      <ul class="flex gap-6 ml-auto text-xl font-bold capitalize">
        <li>
          <NuxtLink to="/" active-class="border-b-4 border-green-500"
            >Home</NuxtLink
          >
        </li>
        <li>
          <NuxtLink to="/about" active-class="border-b-4 border-green-500"
            >About</NuxtLink
          >
        </li>
      </ul>
    </nav>
  </header>
</template>
