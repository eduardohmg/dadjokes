<template>
  <div>
    <b-card>
      {{ joke.joke }}
    </b-card>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'Joke',
  props: { joke: Object },
})
</script>

<style></style>
