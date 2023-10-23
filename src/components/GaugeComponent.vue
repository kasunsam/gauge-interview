<template>
  <div class="gauge-container">
    <div class="gauge">
      <img
        src="../assets/meter.png"
        width="40"
        class="needle"
        :style="needleRotation"
      />
    </div>
    <div class="bottomSide"></div>
    <div class="value">{{ gaugeValue }}</div>
    <div class="counters">
      <div class="left">0</div>
      <div class="right">100</div>
      <div class="top">50</div>
    </div>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  props: {
    value: {
      type: Number,
      default: 0,
    },
  },
  data() {
    return {
      gaugeValue: this.value,
      intervalId: null,
    };
  },
  computed: {
    needleRotation() {
      return `transform: rotate(${(this.gaugeValue * 180) / 65}deg);`;
    },
  },
  methods: {
    startIncrement() {
      this.intervalId = setInterval(() => {
        if (this.gaugeValue < 100) {
          this.gaugeValue++;
          console.log(this.gaugeValue);
        } else {
          clearInterval(this.intervalId);
        }
      }, 250);
    },
  },
  mounted() {
    this.startIncrement();
  },
};
/* eslint-disable */
</script>

<style scoped>
.counters {
  width: 100%;
  position: relative;
  top: -135px;
}
.counters .left {
  float: left;
}

.counters .right {
  float: right;
}

.counters .top {
  float: none;
  text-align: center;
  top: -184px;
  position: relative;
}

.gauge-container {
  display: inline-block;
  position: relative;
  margin-left: auto;
  margin-right: auto;
  display: block;
  width: 200px;
  margin-top: 50px;
}
.bottomSide {
  width: 200px;
  height: 62px;
  background-color: #fff;
  position: relative;
  top: -51px;
}

.gauge {
  width: 150px;
  height: 150px;
  border: 10px solid #ccc;
  border-radius: 50%;
  position: relative;
  transform: rotate(-180deg);
  background: linear-gradient(#fff, #fff) padding-box,
    linear-gradient(272deg, #e1ca46, #75c952, #469ed5) border-box;
  border: 25px solid transparent;
  border-radius: 50%;
}

.needle {
  position: absolute;
  top: 9px;
  left: 55px;
  transform-origin: 15px 45px;
  transform: rotate(0deg);
  transition: transform 0.5s;
}

.gauge::after {
  content: 'After';
  display: block;
  font-style: italic;
}

.value {
  text-align: center;
  font-size: 24px;
  position: relative;
  top: -150px;
  left: -2px;
  font-weight: 700;
}
</style>
