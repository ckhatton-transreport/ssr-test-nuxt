<template>
  <div class="mb-4 p-4">
    <h2 class="text-2xl">
      Cat Facts 🐈
    </h2>
    <p class="my-4">
      This grabs cat facts from an API (<a
        href="https://catfact.ninja/#/Facts/getFacts"
        target="_blank"
      >https://catfact.ninja/#/Facts/getFacts</a>) via fetch.
    </p>
    <div class="flex justify-center">
      <button
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
        @click="loadPreviousPage"
      >
        Previous
      </button>
      <button
        class="
          bg-gray-300
          hover:bg-gray-400
          text-gray-800
          font-bold
          py-2
          px-4
          rounded-r
        "
        @click="loadNextPage"
      >
        Next
      </button>
    </div>
    <section class="flex flex-wrap relative">
      <div
        v-if="loading"
        class="absolute"
      >
        <div class="flex items-center justify-center w-full">
          Loading
        </div>
      </div>
      <div
        v-for="catFact in facts"
        v-else
        :key="catFact.fact.split(' ')[0]"
        :key="catFact.fact.split(' ')[0]"
        class="w-full sm:w-1/2 md:w-1/3 xl:w-1/4"
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

  mounted() {
    this.getFacts(2);
  },

  mounted() {
    this.getFacts(this.currentPage);
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
};
</script>
