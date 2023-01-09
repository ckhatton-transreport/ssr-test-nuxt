<template>
  <div class="mb-4 p-4">
    <h2 class="text-2xl">Cat Facts 🐈</h2>
    <p class="my-4">
      This grabs cat facts from an API (<a
        href="https://catfact.ninja/#/Facts/getFacts"
        target="_blank"
        >https://catfact.ninja/#/Facts/getFacts</a
      >) via fetch.
    </p>
    <div class="flex justify-center">
      <button
        @click="loadPreviousPage"
        class="
          bg-gray-300
          hover:bg-gray-400
          text-gray-800
          font-bold
          py-2
          px-4
          rounded-l
        "
        :disabled="isDisabled"
      >
        Previous
      </button>
      <button
        @click="loadNextPage"
        class="
          bg-gray-300
          hover:bg-gray-400
          text-gray-800
          font-bold
          py-2
          px-4
          rounded-r
        "
      >
        Next
      </button>
    </div>
    <section class="flex flex-wrap relative">
      <div class="absolute" v-if="loading">
        <div class="flex items-center justify-center w-full">Loading</div>
      </div>
      <div
        v-for="(catFact, index) in facts"
        class="w-full sm:w-1/2 md:w-1/3 xl:w-1/4"
        :key="catFact.fact.split(' ')[0] + index"
      >
        <div class="bg-white rounded-lg shadow-lg m-4 p-4">
          <h3>{{ catFact.fact }}</h3>
        </div>
      </div>
    </section>
  </div>
</template>
<script>
export default {
  name: "CatFacts",
  data() {
    return {
      facts: {},
      currentPage: 1,
      loading: false,
    };
  },
  computed: {
    isDisabled() {
      if (this.currentPage === 1) {
        return true;
      } else return false;
    },
  },

  methods: {
    async getFacts(event) {
      try {
        this.loading = true;
        const response = await $fetch(
          `https://catfact.ninja/facts?page=${this.currentPage}`,
          {
            method: "GET",
          }
        );
        this.facts = [];
        this.facts = response.data;
        this.loading = false;
      } catch (error) {
        this.loading = false;
        console.log(error);
      }
    },

    loadNextPage() {
      this.currentPage++;
      this.getFacts();
    },

    loadPreviousPage() {
      this.currentPage--;
      this.getFacts();
    },
  },

  mounted() {
    this.getFacts(this.currentPage);
  },
};
</script>
