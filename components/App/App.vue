<!-- Please remove this file from your project -->
<template>
  <div class="test-idaproject">
    <header class="header">
      <h1>Добавление товара</h1>
    </header>

    <main class="main">
      <MyForm :add-new-card="addNewCard" />
      <ListCards
        :cards="cards"
        :delete-card="deleteCard"
      />
    </main>
  </div>
</template>

<script>

import MyForm from '../MyForm/MyForm.vue';
import ListCards from '../ListCards/ListCards.vue';

export default {
  name: 'App',
  components: {
    MyForm,
    ListCards,
  },
  data() {
    return {
      cards: [
        {
          id: 5,
          title: 'test',
          url: 'https://images.unsplash.com/photo-1511919884226-fd3cad34687c?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1740&q=80',
          descriprion: 'wecwedewdewdwedewd',
          price: '12 121',
        },
        {
          id: 6,
          title: 'test',
          url: 'https://mishka-shop.com/upload/resize_cache/webp/upload/iblock/8c5/8c55b52e342794925bbefff1638798ab.webp',
          descriprion: 'wecd',
          price: '12 121',
        },
        {
          id: 7,
          title: 'test',
          url: 'https://mishka-shop.com/upload/resize_cache/webp/upload/iblock/8c5/8c55b52e342794925bbefff1638798ab.webp',
          descriprion: 'wecd',
          price: '12 121',
        },
      ],
    };
  },
  methods: {
    addNewCard(data) {
      this.cards.push({
        ...data,
        id: this.cards[this.cards.length - 1].id + 1,
      });
    },
    deleteCard(id) {
      const indexCard = this.cards.findIndex((card) => card.id === id);
      this.cards = [
        ...this.cards.slice(0, indexCard),
        ...this.cards.slice(indexCard + 1),
      ];
    },
  },
};
</script>

<style lang="scss" scoped>
  .test-idaproject {
    padding: 32px;
    background-color: #FFFEFB;

      .header {
        display: flex;
        justify-content: space-between;
        margin-bottom: 15px;
        h1 {
          font: {
            family: "SourceSansPro", sans-serif;
            weight: 600;
            size: 28px;
          }
          color: #3F3F3F;
          @media screen and (max-width: 500px) {
            font-size: 22px;
          }
          @media screen and (max-width: 400px){
            font-size: 18px;
          }
        }
      }

    .main {
      display: flex;
      @media screen and (max-width: 744px) {
        flex-direction: column;
      }
    }

    @media screen and (max-width: 500px) {
      padding: 16px;
    }
  }
</style>
