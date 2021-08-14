<template>
  <section class="intro">
    <div class="intro__container">
      <div class="intro_description description">
        <div class="description__title"><h3>Добро пожаловать в наш новый магазин!</h3></div>
        <div class="description__text">
          Мы садимся вязать, и вселенная вокруг начинает жить по-другому. Точнее, мы создаем
          собственную вселенную, в которой мы отдыхаем, вдохновляемся и создаем шедевры. Наш магазин
          за то, чтобы вы занимались своим любимым делом с удовольствием. Наш магазин – это место,
          где вам предложат пряжу и инструмент исключительного качества для создания лучших
          творений, которые вы только задумали. Наш магазин – это место, куда вы просто можете
          прийти поболтать и выпить чашечку кофе за вязанием
        </div>
        <div class="description__link">
          <a href="#">Узнать о нас больше</a>
        </div>
      </div>
      <div class="intro__video">
        <video :src="video" ref="video" controls></video>
        <button type="button" v-if="!isVideoPlay">
          <img :src="play" @click="playVideo" alt="" />
        </button>
      </div>
    </div>
  </section>
</template>

<script>
import video from '../assets/video.mp4';
import play from '../assets/play.svg';

export default {
  name: 'Intro',
  data() {
    return {
      isVideoPlay: false,
      video,
      play,
    };
  },
  methods: {
    playVideo() {
      this.$refs.video.play();
      this.isVideoPlay = true;
    },
  },
};
</script>

<style scoped lang="scss">
@import './src/styles/mixins.scss';
@import './src/styles/variables.scss';

.intro {
  &__container {
    @include container();
    display: flex;
  }
  .description {
    width: 50%;
    &__title {
      text-transform: uppercase;
      h3 {
        margin-top: 0;
      }
    }
    &__text {
      font-size: 12px;
      line-height: 26px;
    }
    &__link {
      display: flex;
      justify-content: flex-end;
      a {
        font-size: 11px;
        color: $color-main;
      }
    }
  }
  &__video {
    position: relative;
    margin-left: 50px;
    width: 50%;
    video {
      width: 100%;
      border: 1px solid $color-main;
    }
    button {
      position: absolute;
      top: calc(50% - 30px);
      left: calc(50% - 30px);
      background-color: transparent;
      border: none;
      cursor: pointer;
    }
  }
}
</style>
