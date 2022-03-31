<template>
  <main id="main">
    <section class="main-header">
      <CountdownTimer />
    </section>
    <section class="main-footer">
      <CountdownSocial />
    </section>
  </main>
</template>

<script>
import CountdownTimer from './components/CountdownTimer.vue'
import CountdownSocial from './components/CountdownSocial.vue'

export default {
  name: 'App',
  components: {
    CountdownTimer,
    CountdownSocial
  }
}
</script>

<style lang="scss">
#main {
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
  background-repeat: no-repeat;
}

.main-header {
  background-image: url("~@/assets/images/bg-stars.svg");
}

.main-footer {
  background-image: url("~@/assets/images/pattern-hills.svg");
  background-position: 28% top;
}

@media (min-width: 1200px) {
  .main-footer {
    background-size: cover;
  }
}
</style>
