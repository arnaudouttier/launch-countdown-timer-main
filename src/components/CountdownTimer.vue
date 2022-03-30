<template>
  <div class="countdown">
    <h2 class="countdown-title">We're launching soon</h2>
    <ul class="countdown-list">
      <li class="timer-item">
        <div class="timer-number">
          <h3>{{ days }}</h3>
          <div class="semi-circle-left"></div>
          <div class="semi-circle-right"></div>
        </div>
        <p>days</p>
      </li>
      <li class="timer-item">
        <div class="timer-number">
          <h3>{{ hours }}</h3>
          <div class="semi-circle-left"></div>
          <div class="semi-circle-right"></div>
        </div>
        <p>hours</p>
      </li>
      <li class="timer-item">
        <div class="timer-number">
          <h3>{{ minutes }}</h3>
          <div class="semi-circle-left"></div>
          <div class="semi-circle-right"></div>
        </div>
        <p>minutes</p>
      </li>
      <li class="timer-item">
        <div class="timer-number">
          <h3>{{ seconds }}</h3>
          <div class="semi-circle-left"></div>
          <div class="semi-circle-right"></div>
        </div>
        <p>seconds</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'CountdownTimer',
  data () {
    return {
      currentTime: 0,
      endTime: 'March 31, 2022 19:30:00',
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
  text-align: center;
}

.countdown-title {
  margin-bottom: clamp(
    50px,
    calc(3.125rem + ((1vw - 3.75px) * 12.5945)),
    100px
  );
  color: $white;
  font-size: clamp(18px, calc(1.125rem + ((1vw - 3.75px) * 1.5113)), 24px);
  text-transform: uppercase;
  font-weight: 600;
  letter-spacing: 7px;
}

.countdown-list {
  display: flex;
  justify-content: space-evenly;
}

.timer-item {
  text-align: center;

  .timer-number {
    width: clamp(70px, calc(4.375rem + ((1vw - 3.75px) * 17.6322)), 140px);
    height: clamp(70px, calc(4.375rem + ((1vw - 3.75px) * 17.6322)), 140px);
    margin-bottom: clamp(
      15px,
      calc(0.9375rem + ((1vw - 3.75px) * 2.5189)),
      25px
    );
    background: linear-gradient(180deg, #2c2c44 50%, #34364f 49%);
    -webkit-box-shadow: 0px 10px 7px -2px rgba(0, 0, 0, 0.84);
    box-shadow: 0px 10px 7px -2px rgba(0, 0, 0, 0.84);
    border-radius: 5px;
    position: relative;

    &::after {
      content: " ";
      width: 100%;
      height: 2px;
      background-color: rgba(0, 0, 0, 0.15);
      position: absolute;
      top: 50%;
      left: 0;
    }

    h3 {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translateY(-50%) translateX(-50%);
      font-size: clamp(32px, calc(2rem + ((1vw - 3.75px) * 8.0605)), 64px);
      font-weight: 600;
    }
  }

  p {
    font-size: clamp(7px, calc(0.4375rem + ((1vw - 3.75px) * 0.5038)), 13px);
    letter-spacing: 3px;
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
