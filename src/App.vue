<template>
  <main id="main">
    <CountdownTimer />
  </main>
</template>

<script>
import CountdownTimer from './components/CountdownTimer.vue'

export default {
  name: 'App',
  components: {
    CountdownTimer
  }
}
</script>

<style lang="scss">
#app {
  font-family: $primary_font;
}
</style>
