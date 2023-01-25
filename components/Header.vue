<template>
  <div class="header">
    <NuxtLink
      to="/"
      class="text-2xl"
    >
      Nuxt 3
    </NuxtLink>
  </div>
</template>

<script>
export default {
  name: 'BaseHeader'
}
</script>

<style lang="sass">
.header
  @apply bg-aquamarine mb-4 p-8 rounded-lg shadow-lg font-extrabold text-white tracking-wide flex flex-wrap justify-between items-center
</style>
