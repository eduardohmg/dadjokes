<template>
  <b-pagination-nav
    v-model="page"
    align="center"
    :link-gen="linkGen"
    :number-of-pages="totalPages"
    limit="10"
  ></b-pagination-nav>
</template>

<script>
import Vue from 'vue'

export default Vue.extend({
  props: {
    currentPage: { type: Number, default: 1 },
    totalPages: { type: Number, default: 10 },
  },
  data() {
    return {
      page: this.currentPage,
    }
  },
  methods: {
    linkGen(pageNum) {
      const term = this.$route.query.term
      const termQuery = !term ? '' : `term=${this.$route.query.term}&`
      return `?${termQuery}page=${pageNum}`
    },
  },
})
</script>

<style></style>
