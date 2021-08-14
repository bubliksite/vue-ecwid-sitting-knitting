<template>
  <div class="app">
    <Header />
    <Slider />
    <Features />
    <Intro />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Features from './components/Features.vue';
import Intro from './components/Intro.vue';
import Slider from './components/Slider.vue';

export default {
  name: 'App',
  components: {
    Slider,
    Intro,
    Features,
    Header,
  },
};
</script>

<style lang="scss"></style>
