<template>
  <!-- This block will show after the delay -->
  <div class="block" v-if="showBlock">click me!</div>
</template>

<script>
export default {
  props: ['delay'],
  data() {
    return {
      showBlock: false,
    }
  },
  /*
   Used to run code after the component has finished the initial rendering and created the DOM nodes
   Mounting which sets a delay timer - the delay prop is the variable
  */
  mounted() {
    console.log('component mounted')
    setTimeout(() => {
      this.showBlock = true
      console.log(this.delay)
    }, this.delay)
  },
  /*
   Fires this after the component has updated
  */
  updated() {
    console.log('component updated')
  },
  /*
   Fires this when the component unmounts - especially when changing pages
  */
  unmounted() {
    console.log('component unmounted')
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
