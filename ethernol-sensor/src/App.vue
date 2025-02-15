<template class="flex items-center justify-center h-screen bg-black">
  <div>
    <GaugeComponent :ethanolValue="ethanolValue" />
    
  </div>
</template>

<script>
import GaugeComponent from './components/GaugeComponent.vue';

export default {
  components: {
    GaugeComponent
  },
  data() {
    return {
      ethanolValue: 0
    };
  },
  mounted() {
    setInterval(() => {
      this.ethanolValue = Math.floor(Math.random() * 101);
    }, 1000);
  }
};
</script>
