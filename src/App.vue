<template>
  <div id="app">
    <GaugeComponent :data="intervals" />
  </div>
</template>

<script>
import GaugeComponent from './components/GaugeComponent.vue';

export default {
  components: {
    GaugeComponent,
  },
  data() {
    return {
      intervals: [
        { value: 0, color: '#E1CA46' },
        { value: 50, color: '#75C952' },
        { value: 100, color: '#469ED5' },
      ],
    };
  },
};
</script>
