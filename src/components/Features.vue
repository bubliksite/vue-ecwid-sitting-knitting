<template>
  <section class="features">
    <div class="features__container">
      <div class="features__item" v-for="(item, index) in features" :key="index">
        <img class="item__image" :src="item.image" :alt="item.description" />
        <p class="item__description" v-html="item.description"></p>
      </div>
    </div>
  </section>
</template>

<script>
import sheep from '../assets/Sheep.png';
import avi from '../assets/Avi.png';
import delivery from '../assets/Delivery.png';
import location from '../assets/Location.png';
import support from '../assets/Support.png';

export default {
  name: 'Features',
  data() {
    return {
      features: [
        {
          image: sheep,
          description: 'Только <br> натуральный состав',
        },
        {
          image: avi,
          description: 'Актуальное <br> наличие на сайте',
        },
        {
          image: delivery,
          description: 'Быстрая <br> отправка',
        },
        {
          image: location,
          description: 'Удобное <br> расположение',
        },
        {
          image: support,
          description: 'Помощь <br> в подборе товаров',
        },
      ],
    };
  },
};
</script>

<style scoped lang="scss">
@import './src/styles/mixins.scss';
@import './src/styles/variables';

.features {
  &__container {
    @include container();
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
  }
  &__item {
    margin: 15px 0;
    text-align: center;
    flex: auto;
    padding: 0 15px;
  }
  .item {
    &__image {
      height: 80px;
      object-fit: contain;
    }
    &__description {
      margin-top: 24px;
      font-size: 14px;
      color: $color-main;
    }
  }
}
</style>
