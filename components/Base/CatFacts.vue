<template>
  <div class="mb-4 p-4">
    <h2 class="text-2xl">
      Cat Facts 🐈
    </h2>
    <p class="my-4">
      This grabs cat facts from an API <NuxtLink
        to="https://catfact.ninja/#/Facts/getFacts"
        target="_blank"
      >
        (https://catfact.ninja/#/Facts/getFacts)
      </NuxtLink> via fetch.
    </p>
    <p
      v-if="CatFactsStore.maxLength !== -1"
      class="my-4"
    >
      The facts have been limited to a fact length of {{ CatFactsStore.maxLength }}.
    </p>
    <ToolPagination />
    <ToolFacts />
  </div>
</template>

<script setup lang="ts">
// import { onBeforeMount } from 'vue';
// import { CatFactsStore } from '@/composables/CatFactsStore';

onBeforeMount((): void => {
  CatFactsStore.getFacts();
});
</script>
