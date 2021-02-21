<template>
  <div>
    <b-container>
      <JokeNavBar />
      <Joke v-for="joke in jokes" :key="joke.id" :joke="joke" />
      <JokeNavigation :total-pages="totalPages" :current-page="currentPage" />
    </b-container>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Joke from '@/components/Joke.vue'
import JokeNavBar from '@/components/JokeNavBar.vue'
import JokeNavigation from '@/components/JokePagination.vue'

export default Vue.extend({
  components: {
    Joke,
    JokeNavBar,
    JokeNavigation,
  },
  data() {
    return {
      jokes: [],
      totalPages: 10,
      currentPage: Number(this.$route.query.page) || 1,
    }
  },
  head() {
    return {
      title: 'Dad Jokes',
    }
  },
  async created() {
    const config = {
      headers: { Accept: 'application/json' },
    }

    const result = await this.$axios.$get(
      `https://icanhazdadjoke.com/search?term=${
        this.$route.query.term || ''
      }&page=${this.$route.query.page || 1}`,
      config
    )

    this.jokes = result.results
    this.totalPages = result.total_pages
  },
})
</script>

<style></style>
