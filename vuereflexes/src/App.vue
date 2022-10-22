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

  <div class="ui centered container">
    <div class="ui raised very padded text container segment">
      <div class="ui padded grid">

        <div class="sixteen wide column">
          <h2 class="ui header">Reaction timer</h2>
          <div class="ui primary button" @click="start" :disabled="ongoing">play</div>
        </div>

        <div class="sixteen wide column">
          <Target v-if="ongoing" :delay="delay" @fired="finish"/>
          <Results v-if="showResults" :score="score"/>
        </div>

      </div>
    </div>
  </div>

</template>

<style>
</style>
