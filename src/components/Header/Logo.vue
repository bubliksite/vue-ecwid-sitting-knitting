<template>
  <div>
    <img :src="logo" alt="" />
  </div>
</template>

<script>
import logo from '@/assets/logo_header.png';

export default {
  name: 'Logo',
  data() {
    return {
      logo,
    };
  },
};
</script>

<style scoped></style>
