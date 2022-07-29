<template>
  <ul class="list">
    <CardItem
      v-for="card in cards"
      :key="card.id"
      :data="card"
    />
  </ul>
</template>

<script>
import CardItem from './CardItem/CardItem.vue';

export default {
  name: 'ListCard',
  components: {
    CardItem,
  },
  props: {
    cards: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>
  .list {
    list-style-type: none;
    display: grid;
    width: 100%;
    grid-template-columns: repeat(auto-fill, 332px);
    grid-template-rows: 440px;
    grid-auto-rows: 440px;
    gap: 16px;

    @media screen and (max-width: 744px){
      grid-template-columns: repeat(2, 1fr);
    }

    @media screen and (max-width: 600px){
      grid-template-rows: 360px;
    }

    @media screen and (max-width: 500px){
      margin: 0 auto;
      width: 100%;
      display: block;
    }

    @media screen and (max-width: 400px){
      width: calc(100vw - 20px * 2);
    }

  }

</style>
