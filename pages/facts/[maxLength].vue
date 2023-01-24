<template>
  <div class="max-w-7xl mx-auto">
    <CatFacts :max-length="maxLength" />
  </div>
</template>

<script>
export default {
  name: 'PagesFactsMaxLength'
}
</script>

<script setup>
// import { useRoute } from 'vue-router';

const maxLength = Number(useRoute().params.maxLength) || null;
</script>
