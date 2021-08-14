<template>
  <section class="slider">
    <div class="slider__content" :style="{ left: -slideWidth * currentSlide + 'px' }">
      <div class="slider__item" v-for="(slide, index) in slides" :key="index">
        <img :src="slide" alt="" />
      </div>
    </div>
    <div class="slider__controls">
      <div class="controls__prev" @click="prevSlide"><img :src="arrow" alt="" /></div>
      <div class="controls__next" @click="nextSlide"><img :src="arrow" alt="" /></div>
    </div>
    <div class="slider__dots">
      <div
        class="slider__dot"
        :class="{ active: index - 1 === currentSlide }"
        v-for="index in slides.length"
        :key="index"
        @click="toSlide(index - 1)"
      ></div>
    </div>
  </section>
</template>

<script>
import slide1 from '@/assets/slide_1.png';
import slide2 from '@/assets/slide_2.jpg';
import slide3 from '@/assets/slide_3.jpg';
import arrow from '@/assets/control_arrow.svg';

export default {
  name: 'Slider',
  data() {
    return {
      arrow,
      slideWidth: 0,
      slides: [slide1, slide2, slide3],
      currentSlide: 0,
      offsetSlideLeft: 1,
      offsetSlideWidth: 0,
    };
  },
  mounted() {
    this.slideWidth = document.querySelector('.slider').clientWidth;
    window.addEventListener('resize', () => {
      this.slideWidth = document.querySelector('.slider').clientWidth;
    });
  },
  methods: {
    nextSlide() {
      if (this.currentSlide + 1 === this.slides.length) {
        this.currentSlide = 0;
      } else {
        this.currentSlide += 1;
      }
    },
    prevSlide() {
      if (this.currentSlide === 0) {
        this.currentSlide = this.slides.length - 1;
      } else {
        this.currentSlide -= 1;
      }
    },
    toSlide(index) {
      this.currentSlide = index;
    },
  },
};
</script>

<style scoped lang="scss">
@import './src/styles/mixins.scss';
@import './src/styles/variables.scss';

.slider {
  @include container();
  overflow: hidden;
  position: relative;
  &__content {
    display: flex;
    position: relative;
    transition: left 0.5s ease-in-out;
  }
  &__item {
    width: 100%;
    height: 500px;
    flex: 0 0 100%;
    img {
      height: 100%;
      width: 100%;
      object-fit: cover;
    }
  }
  &__controls {
    @include container();
    position: absolute;
    top: calc(50% - 15px);
    display: flex;
    justify-content: space-between;
    .controls__prev {
      margin-left: 22px;
      cursor: pointer;
    }
    .controls__next {
      transform: rotate(180deg);
      margin-right: 22px;
      cursor: pointer;
    }
    img {
      object-fit: contain;
    }
  }
  &__dots {
    @include container();
    position: absolute;
    bottom: 25px;
    display: flex;
    justify-content: center;
    .slider__dot {
      width: 10px;
      height: 10px;
      background-color: #fff;
      border-radius: 50%;
      margin: 0 15px;
      cursor: pointer;
      transition: background-color 0.5s ease-in-out;
      &.active {
        background-color: $color-main;
      }
    }
  }
}
</style>
