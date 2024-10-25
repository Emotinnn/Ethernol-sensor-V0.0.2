<template>
  <div class="gauge-container center">
      <div class="gauge-background" :style="{ background: gaugeStyle }"></div>
      <div class="gauge-center">
          <div class="gauge-value">{{ ethanolValue }}</div>
          <div class="unit">Ethanol %</div>
      </div>
  </div>
</template>

<script>
export default {
  props: ['ethanolValue'],
  computed: {
      gaugeStyle() {
          const percentage = (this.ethanolValue / 100) * 100;
          const red = Math.floor(255 * (1 - percentage / 100));
          const green = Math.floor(255 * (percentage / 100));
          return `conic-gradient(
              rgb(${red}, ${green}, 0) ${percentage}%,
              #000000 ${percentage}% 100%
          )`;
      }
  }
};
</script>

<style scoped>
  .gauge-container {
      position: relative;
      width: 300px;
      height: 300px;
      border-radius: 50%;
      box-shadow: 
          inset 0 5px 15px rgba(255, 255, 255, 0.2),
          0 10px 20px rgba(0, 0, 0, 0.6);
      display: flex;
      justify-content: center;
      align-items: center;
  }

  .gauge-background {
      position: absolute;
      width: 100%;
      height: 100%;
      border-radius: 50%;
      transition: background 0.5s ease;
  }

  .gauge-center {
      position: absolute;
      width: 70%;
      height: 70%;
      background: radial-gradient(circle, #333333, #000000);
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      box-shadow: inset 0 5px 10px rgba(0, 0, 0, 0.6),
                  0 5px 10px rgba(0, 0, 0, 0.6);
  }

  .gauge-value {
      font-size: 3.5rem;
      color: #FFFFFF;
      text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7);
      position: relative;
      z-index: 1;
  }

  .unit {
      font-size: 1rem;
      color: #FFFFFF;
      position: absolute;
      bottom: 20px;
  }
</style>
