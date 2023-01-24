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
// import { ref } from 'vue';
// import { useRoute } from 'vue-router';
const route = useRoute();

const maxLength = ref(Number(route.params.maxLength) || null);
</script>
