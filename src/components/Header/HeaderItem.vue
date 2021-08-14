<template>
  <div>
    <a
      href="https://yandex.ru/maps/?ll=33.904203%2C57.936726&mode=routes&rtext=59.994931%2C30.303846~55.743598%2C37.603397&rtt=auto&ruri=~ymapsbm1%3A%2F%2Fgeo%3Fll%3D37.603%252C55.744%26spn%3D0.001%252C0.001%26text%3D%25D0%25A0%25D0%25BE%25D1%2581%25D1%2581%25D0%25B8%25D1%258F%252C%2520%25D0%259C%25D0%25BE%25D1%2581%25D0%25BA%25D0%25B2%25D0%25B0%252C%2520%25D0%25A1%25D0%25BE%25D0%25B9%25D0%25BC%25D0%25BE%25D0%25BD%25D0%25BE%25D0%25B2%25D1%2581%25D0%25BA%25D0%25B8%25D0%25B9%2520%25D0%25BF%25D1%2580%25D0%25BE%25D0%25B5%25D0%25B7%25D0%25B4%252C%25207%25D1%25811&z=7.22"
      target="_blank"
      class="item"
      v-if="type === 'map'"
    >
      <div class="item__image">
        <img :src="image" alt="Menu item" />
      </div>
      <div v-if="description" class="item__description">
        <p>
          {{ description[0] }} <br />
          {{ description[1] }}
        </p>
      </div>
    </a>
    <div class="item" v-if="type === 'schedule'">
      <div class="item__image">
        <img :src="image" alt="Menu item" />
      </div>
      <div v-if="description" class="item__description">
        <p>
          <span>{{ description[0][0] }}</span>
          <span>{{ description[0][1] }}</span>
        </p>
        <p>
          <span>{{ description[1][0] }}</span>
          <span>{{ description[1][1] }}</span>
        </p>
      </div>
    </div>
    <div class="item" v-if="type === 'phone'">
      <div class="item__image">
        <img :src="image" alt="Menu item" />
      </div>
      <div v-if="description" class="item__description">
        <p>
          <a :href="`tel:${description[0]}`">{{ description[0] }}</a>
        </p>
        <p>
          <a :href="`tel:${description[1]}`">{{ description[1] }}</a>
        </p>
      </div>
    </div>
    <a href="/cart" class="item" v-if="type === 'cart'">
      <div class="item__image">
        <img :src="image" alt="Menu item" />
      </div>
    </a>
  </div>
</template>

<script>
export default {
  name: 'Schedule',
  props: {
    image: String,
    description: Array,
    type: String,
  },
};
</script>

<style scoped lang="scss">
a {
  text-decoration: none;
  color: inherit;
}
.item {
  display: flex;
  align-items: center;
  .item__image {
    display: flex;
    align-items: center;
  }
  .item__description {
    p {
      margin: 0 0 0 17px;
      font-size: 13px;
      display: flex;
      justify-content: space-between;
      width: 100%;
      @media screen and (max-width: 992px) {
        font-size: 12px;
        margin-left: 10px;
      }
    }
  }
}
</style>
