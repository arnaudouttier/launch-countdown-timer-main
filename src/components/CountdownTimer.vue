<template>
  <section class="countdown">
    <h2 class="countdown-title">We're launching soon</h2>
    <ul class="countdown-list">
      <li class="timer-item days">
        <div class="timer-number">
          <h3>{{ days }}</h3>
        </div>
        <p>days</p>
      </li>
      <li class="timer-item hours">
        <div class="timer-number">
          <h3>{{ hours }}</h3>
        </div>
        <p>hours</p>
      </li>
      <li class="timer-item minutes">
        <div class="timer-number">
          <h3>{{ minutes }}</h3>
        </div>
        <p>minutes</p>
      </li>
      <li class="timer-item seconds">
        <div class="timer-number">
          <h3>{{ seconds }}</h3>
        </div>
        <p>seconds</p>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  name: 'CountdownTimer',
  data () {
    return {
      currentTime: 0,
      endTime: 'April 18, 2022 14:22:00',
      t: 0,
      days: 0,
      hours: 0,
      minutes: 0,
      seconds: 0
    }
  },
  methods: {
    dateCounterTime () {
      this.currentTime = Date.parse(new Date())
      this.endTime = Date.parse(new Date(this.endTime))

      this.t = this.endTime - this.currentTime

      this.days = parseInt(this.t / (1000 * 60 * 60 * 24), 10)
      this.hours = parseInt((this.t / (1000 * 60 * 60)) % 24, 10)
      this.minutes = parseInt((this.t / 1000 / 60) % 60, 10)
      this.seconds = parseInt((this.t / 1000) % 60, 10)

      this.days = this.days < 10 ? '0' + this.days : this.days
      this.hours = this.hours < 10 ? '0' + this.hours : this.hours
      this.minutes = this.minutes < 10 ? '0' + this.minutes : this.minutes
      this.seconds = this.seconds < 10 ? '0' + this.seconds : this.seconds
    }
  },
  created () {
    setInterval(() => {
      this.dateCounterTime()
    }, 1000)
  }
}
</script>

<style scoped lang="scss">
.countdown {
  width: min(90vw, 750px);
  margin: 0 auto;
  border: 2px solid red;
  text-align: center;
}
.countdown-title {
  margin-bottom: 50px;
  color: $white;
  font-size: 18px;
  text-transform: uppercase;
  font-weight: 600;
  letter-spacing: 7px;
}
.countdown-list {
  display: flex;
  justify-content: space-between;
}
.timer-item {
  text-align: center;
  p {
    font-size: 8px;
    letter-spacing: 2px;
    font-weight: 600;
    color: $grayish_blue;
    text-transform: uppercase;
  }
}

.timer-number {
  h3 {
    color: $soft_red;
  }
}
</style>
