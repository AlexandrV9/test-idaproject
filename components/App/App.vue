<!-- Please remove this file from your project -->
<template>
  <div class="test-idaproject">
    <header class="header">
      <h1>Добавление товара</h1>
    </header>

    <main class="main">
      <MyForm />
    </main>
  </div>
</template>

<script>

import MyForm from '../common/MyForm/MyForm.vue';

export default {
  name: 'App',
  components: {
    MyForm,
  },
  data() {
    return {
      cards: [],
    };
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
