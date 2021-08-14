<template>
  <header class="header">
    <div class="header__top desktop">
      <Logo />
      <HeaderItem
        v-for="(item, index) in headerItems"
        :key="index"
        :image="item.image"
        :description="item.description"
        :type="item.type"
      />
    </div>
    <div class="header__top mobile">
      <Logo />
      <button type="button" @click="toggleMenu" class="open-menu__button">
        <img :src="hamburger" alt="menu" />
      </button>
    </div>
    <div class="header__open-menu"></div>
    <nav class="header__nav nav">
      <ul class="nav__container">
        <li class="nav__item" v-for="(item, index) in nav" :key="index">
          <!-- При применении VueRouter использовать <router-link> вместо <a> -->
          <a class="nav__link" :href="item.link">{{ item.title }}</a>
        </li>
      </ul>
    </nav>
    <div v-if="isShowMenu" class="header__mobile-menu mobile-menu">
      <div class="mobile-menu__container">
        <div class="mobile-menu__top">
          <HeaderItem
            :type="headerItems[0].type"
            :image="headerItems[0].image"
            :description="headerItems[0].description"
          />
          <HeaderItem
            :type="headerItems[3].type"
            :image="headerItems[3].image"
            :description="headerItems[3].description"
          />
        </div>
        <div class="mobile-menu__nav">
          <ul class="nav__container mobile">
            <li class="nav__item" v-for="(item, index) in nav" :key="index">
              <!-- При применении VueRouter использовать <router-link> вместо <a> -->
              <a class="nav__link" :href="item.link">{{ item.title }}</a>
            </li>
          </ul>
        </div>
        <div class="mobile-menu__bottom">
          <HeaderItem
            :type="headerItems[2].type"
            :image="headerItems[2].image"
            :description="headerItems[2].description"
          />
          <HeaderItem
            :type="headerItems[1].type"
            :image="headerItems[1].image"
            :description="headerItems[1].description"
          />
        </div>
      </div>
    </div>
  </header>
</template>

<script>
import Logo from './Header/Logo.vue';
import HeaderItem from './Header/HeaderItem.vue';

import map from '@/assets/map.png';
import schedule from '@/assets/clock.png';
import phone from '@/assets/phone.png';
import cart from '@/assets/cart.png';
import hamburger from '@/assets/hamburger.svg';

export default {
  name: 'Header',
  components: { Logo, HeaderItem },
  data() {
    return {
      hamburger,
      isShowMenu: false,
      headerItems: [
        {
          image: map,
          description: ['м. Кропоткинская', 'Соймоновский проезд, д.7 с.1'],
          type: 'map',
        },
        {
          image: schedule,
          description: [
            ['Пн - Пт', '11 - 20'],
            ['Сб - Вск', '11 - 18'],
          ],
          type: 'schedule',
        },
        {
          image: phone,
          description: ['+7 800 000 00 00', '+7 800 000 00 00'],
          type: 'phone',
        },
        {
          image: cart,
          type: 'cart',
        },
      ],
      nav: [
        {
          title: 'Пряжа',
          link: '#',
        },
        {
          title: 'Спицы',
          link: '#',
        },
        {
          title: 'Крючки',
          link: '#',
        },
        {
          title: 'Аксессуары',
          link: '#',
        },
        {
          title: 'Подарочные сертификаты',
          link: '#',
        },
        {
          title: 'МК и описание',
          link: '#',
        },
        {
          title: 'Модели',
          link: '#',
        },
      ],
    };
  },
  methods: {
    toggleMenu() {
      this.isShowMenu = !this.isShowMenu;
    },
  },
};
</script>

<style scoped lang="scss">
@import '../styles/mixins.scss';
@import '../styles/variables.scss';

.header {
  margin: 30px 0;
  &__top {
    @include container();
    margin-bottom: 30px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    &.desktop {
      display: flex;
      @media screen and (max-width: 768px) {
        display: none;
      }
    }
    &.mobile {
      display: none;
      @media screen and (max-width: 768px) {
        display: flex;
      }
    }
  }
  .nav {
    background-color: $color-main;
    padding: 11px 0;
    &__container {
      @include container();
      list-style: none;
      display: flex;
      justify-content: center;
      align-items: center;
      &.mobile {
        padding-left: 0;
        display: block;
        .nav__item {
          margin: 12px 0;
        }
        .nav__link {
          font-size: 16px;
        }
      }
    }
    &__item {
      margin: 0 16px;
    }
    &__link {
      color: #ffffff;
      text-decoration: none;
      font-weight: 700;
      font-size: 14px;
      @media screen and (max-width: 992px) {
        font-size: 12px;
      }
    }
    @media screen and (max-width: 768px) {
      display: none;
    }
  }
  &__open-menu {
    display: none;
    @media screen and (max-width: 768px) {
      display: block;
    }
  }
  .mobile-menu {
    display: none;
    &__top,
    &__bottom {
      @include container();
      margin-bottom: 17px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    &__nav {
      margin-bottom: 17px;
      padding: 17px 0;
      background-color: $color-main;
    }
    @media screen and (max-width: 768px) {
      display: block;
    }
  }
  .open-menu__button {
    background-color: transparent;
    border: none;
  }
}
</style>
