<template>
  <div class="max-w-7xl mx-auto">
    <div class="flex flex-col w-60">
      <NuxtLink
        class="
          px-6
          py-3
          text-blue-100
          no-underline
          bg-blue-500
          rounded
          hover:bg-blue-600
          hover:underline
          hover:text-blue-200
          mb-4
          text-center
        "
        to="/facts/123"
        >Facts length 123</NuxtLink
      >
      <NuxtLink
        class="
          px-6
          py-3
          text-blue-100
          no-underline
          bg-blue-500
          rounded
          hover:bg-blue-600
          hover:underline
          hover:text-blue-200
          text-center
        "
        to="/facts/30"
        >Facts length 30</NuxtLink
      >
    </div>
    <CatFacts />
  </div>
</template>
