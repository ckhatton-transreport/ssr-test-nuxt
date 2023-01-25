<template>
  <div class="max-w-7xl mx-auto">
    <BaseCatFacts />
  </div>
</template>

<script>
export default {
  name: 'PagesFactsMaxLength'
}
</script>

<script setup>
// import { useRoute } from 'vue-router';
// import { CatFactsStore } from '@/composables/CatFactsStore';

CatFactsStore.maxLength = Number(useRoute().params.maxLength) || -1;
</script>
