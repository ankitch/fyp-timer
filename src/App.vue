<template>
  <div id="app">
      <Timer v-bind:date=date></Timer>
  </div>
</template>

<script>
import Timer from '@/components/Timer.vue'
export default {
  name: 'app',
  data () {
    return {
      date: 'May 10, 2018'
    }
  },
  components: {
    Timer
  }
}
</script>

<style>
body {
  margin: 0;
}

#app {
height: 100vh;
background-color: #0fb9b1;
}
</style>
