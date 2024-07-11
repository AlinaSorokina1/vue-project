<template>
  <div id="app">
    <div class="progress-bars">
      <CircleProgress 
        :maxValue="108"
        :value="36"
        :targetValue="80"
        size='240'
      />
      <CircleProgress
        :maxValue="108"
        :value="80"
        :targetValue="80"
        size='240'
      />
      <CircleProgress
        :maxValue="108"
        :value="108"
        :targetValue="80"
        size='240'
      />
    </div>
  </div>
</template>

<script>
import CircleProgress from './components/CircleProgress.vue';

export default {
  name: 'App',
  components: {
    CircleProgress,
  },
};

</script>

<style>

#app {
  text-align: center;
  margin-top: 60px;
}

.progress-bars {
  display: flex;
  justify-content: space-between; 
  flex-direction: column;
  gap: 30px
}


</style>
