<script>
import Target from './components/Target.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Target, Results },
  data() {
    return {
      ongoing: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start() {
      console.log("Hello there")
      this.delay = 2000 + Math.random() * 5000
      this.ongoing = true
      this.showResults = false
    },
    finish(event) {
      this.score = event.reactionTime
      this.ongoing = false
      this.showResults = true
    }
  }
}
</script>

<template>
  <h1>Reaction timer</h1>
  <div class="ui primary button" @click="start" :disabled="ongoing">play</div>

  <Target v-if="ongoing" :delay="delay" @fired="finish"/>

  <Results v-if="showResults" :score="score"/>

</template>

<style>
</style>
