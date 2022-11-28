<template>
  <!-- This block will show after the delay -->
  <div class="block" v-show="showBlock" @click="stopTimer">click me!</div>
</template>

<script>
export default {
  props: ['delay'], // prop obtained from App.js
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0
    }
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true
      this.startTimer()
    }, this.delay)
  },
  methods: {
    startTimer() {
      /*
      Start the timer, tick every 10ms - store interval
      */
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10)
    },
    stopTimer() {
      /**
       * Stop the timer - clear stored interval
       * Emits the "end-game" variable to the App.js
      */
      clearInterval(this.timer)
      this.$emit('end-game', this.reactionTime)
    }
  }
}
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
