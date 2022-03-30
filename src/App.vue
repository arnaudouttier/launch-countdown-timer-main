<template>
  <main id="main">
    <section class="main-header">
      <CountdownTimer />
    </section>
    <section class="main-footer">
      <CounterSocialNavigation />
    </section>
  </main>
</template>

<script>
import CountdownTimer from './components/CountdownTimer.vue'
import CounterSocialNavigation from './components/CounterSocialNavigation.vue'

export default {
  name: 'App',
  components: {
    CountdownTimer,
    CounterSocialNavigation
  }
}
</script>

<style lang="scss">
main {
  font-family: $primary_font;
  height: 100vh;
  width: 100%;
   background: linear-gradient(180deg, #1e1f29 80%, #2f2439 20%);
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: 3fr 1fr;
}

.main-header,
.main-footer {
  display: flex;
  justify-content: center;
  align-items: center;
}

.main-header {
  background-image: url("~@/assets/images/bg-stars.svg");
  background-repeat: no-repeat;
}

.main-footer {
  background-image: url("~@/assets/images/pattern-hills.svg");
  background-position: 28% top;
  background-repeat: no-repeat;
}
</style>
