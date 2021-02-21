<template>
  <b-navbar type="dark" variant="primary">
    <b-navbar-brand href="/">Dad Jokes</b-navbar-brand>
    <b-navbar-nav class="ml-auto"
      ><b-nav-form>
        <b-form-input
          v-model="term"
          size="sm"
          class="mr-sm-2"
          placeholder="Search"
          name="term"
        ></b-form-input>
      </b-nav-form>
    </b-navbar-nav>
  </b-navbar>
</template>

<script>
import Vue from 'vue'
export default Vue.extend({
  data() {
    return {
      term: this.$route.query.term || '',
    }
  },
})
</script>

<style></style>
