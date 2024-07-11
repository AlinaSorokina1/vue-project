<template>
  <div class="circle-progress-container">
    <svg
      class="circle-progress"
      :width="size"
      :height="size"
      viewBox="0 0 240 240"
    >
      <defs>
        <linearGradient
          id="leftToRightGradient"
          x1="0%"
          y1="0%"
          x2="100%"
          y2="0%"
        >
          <stop offset="0%" stop-color="#505B69" />
          <stop offset="100%" stop-color="#353D47" />
        </linearGradient>
        <linearGradient
          id="rightToLeftGradient"
          x1="0%"
          y1="0%"
          x2="0%"
          y2="100%"
        >
          <stop offset="0%" stop-color="#505B69" />
          <stop offset="100%" stop-color="#353D47" />
        </linearGradient>
        <linearGradient
          id="gradientCircleBackground"
          x1="0%"
          y1="0%"
          x2="100%"
          y2="0%"
        >
          <stop offset="0%" stop-color="#282F37" />
          <stop offset="100%" stop-color="#282d3b" />
        </linearGradient>
      </defs>
      <circle
        class="circle-background"
        cx="120"
        cy="120"
        r="118"
        fill="url(#gradientCircleBackground)"
        stroke="none"
        stroke-width="1"
      ></circle>
      <circle
        class="circle-inner"
        cx="120"
        cy="120"
        r="77"
        fill="url(#leftToRightGradient)"
        stroke="url(#rightToLeftGradient)"
        stroke-width="6"
      ></circle>
      <circle
        class="circle-progress-track"
        cx="120"
        cy="120"
        r="99"
        fill="none"
        stroke="#F96C00"
        stroke-width=""
        :stroke-dasharray="circleDashArray"
        :stroke-dashoffset="circleDashOffset"
      ></circle>

      <circle
        class="circle-progress-fill"
        cx="120"
        cy="120"
        r="99"
        fill="none"
        :stroke="fillColor"
        stroke-width="38"
        :stroke-dasharray="circleDashArray"
        :stroke-dashoffset="circleDashOffset"
        stroke-linecap="round"
      ></circle>
    </svg>
    <div class="circle-info">
      <span v-if="value < targetValue" class="circle-text"
        >Еще продать на завтра</span
      >
      <div class="text-container">
      <span class="circle-value" :style="{ color: fillColor }">{{
        !isTargetReached ? value  : '+' + remainingPercentage 
      }}</span>
       <span class="custom-letter">ч</span>
    </div>
  </div>
  </div>
</template>

<script>
export default {
  props: ['maxValue', 'value', 'targetValue', 'size'],

  computed: {
    percentage() {
      return ((this.value / this.maxValue) * 100).toFixed(2);
    },
    circleDashArray() {
      return Math.PI * 2 * 99; 
    },
    circleDashOffset() {
      const offset = (1 - this.percentage / 100) * this.circleDashArray;
      return offset.toFixed(2); 
    },
    isTargetReached() {
      return this.value < this.targetValue;
    },
    remainingPercentage() {
      return this.targetValue - this.value;
    },
    fillColor() {
      return this.value < this.targetValue ? '#F96C00' : '#298D40';
    },
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400&family=Roboto:wght@400;700&display=swap');


.circle-progress-container {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  position: relative;
  width: 240px;
  height: 240px;
}

.circle-progress {
  position: relative;
  transform: rotate(-90deg);
  transform-origin: 50% 50%;
}

.circle-info {
  display: flex;
  flex-direction: column;
  align-items: center;
  position: absolute;
  width: 100px;
  text-align: center;
}

.circle-value {
  font-family: 'Roboto', sans-serif;
  font-size: 38px;
  font-weight: 900;
  line-height: 39.52px;
  text-align: center;
}

.text-container {
  display: flex; 
  align-items: last baseline; 
  gap: 2px; 
}

.circle-text {
  font-family: 'Poppins', sans-serif;
  font-size: 14px;
  font-weight: 400;
  line-height: 18px;
  text-align: center;
  color: #b5c3d7;
  text-wrap: wrap;
}

.custom-letter {
  font-family: 'Poppins', sans-serif;
font-size: 14px;
font-weight: 400;
line-height: 20px;
text-align: center;
color: #b5c3d7;
}
</style>
