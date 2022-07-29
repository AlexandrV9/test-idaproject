<template>
  <li class="card">
    <button class="button-delete">
      <img
        class="button-delete-icon"
        src="../../../assets/icons/trash.svg"
      >
    </button>
    <div class="container">
      <div class="wrapper">
        <img
          v-show="isLoading"
          :src="data.url"
          :class="'card-image ' + (!isLoading ? 'load' : 'completed')"
          @load="onImgLoad"
        >
        <MyPreloader
          v-if="!isLoading"
          :width="60"
          :height="60"
        />
      </div>

      <div class="content">
        <h3 class="title">
          {{ data.title }}
        </h3>
        <p class="subtitle">
          {{ data.descriprion }}
        </p>
        <p class="price">
          10 000 руб.
        </p>
      </div>
    </div>
  </li>
</template>

<script>

import MyPreloader from '../../common/MyPreloader/MyPreloader.vue';

export default {
  name: 'CardItem',
  components: {
    MyPreloader,
  },
  props: {
    data: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      isLoading: false,
    };
  },
  methods: {
    onImgLoad() {
      setTimeout(() => {
        this.isLoading = true;
      }, 1000);
    },
  },
};
</script>

<style lang="scss" scoped>
  .card {
    position: relative;
    height: 100%;

    &:hover .button-delete {
      display: grid;
    }

    &:hover .wrapper > img {
      transform: scale(1.15);
    }

    .button-delete {
      display: none;
      position: absolute;
      top: -8px;
      right: -8px;
      z-index: 8;
      border: none;
      width: 32px;
      height: 32px;
      place-items: center;
      background: #FF8484;
      box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
      border-radius: 10px;
      transition: all 0.2s ease-in;

      &:hover {
        opacity: 1;
      }

      &:hover + .container > .wrapper > img {
        transform: scale(1.15);
      }
    }

    .container {
      background: #FFFEFB;
      box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
      border-radius: 4px;
      transition: all 0.3s ease-in;
      height: 100%;
      display: grid;
      grid-template-columns: 1fr;
      grid-template-rows: 221px 1fr;

      .wrapper {
        display: flex;
        align-items: center;
        justify-content: center;
        border-top-left-radius: 4px;
        border-top-right-radius: 4px;
        overflow: hidden;
        max-height: 221px;

        > img {
          width: 100%;
          height: 100%;
          transition: all 0.4s ease-in;
          display: block;
          object-fit: cover;

          @media screen and (max-width: 600px){
            height: 180px;
          }
        }

        @media screen and (max-width: 500px){
          max-height: 280px;
        }
      }

      @media screen and (max-width: 744px){
        grid-template-rows: repeat(2, 1fr);
      }

      @media screen and (max-width: 600px){
        grid-template-rows: 180px 1fr;
      }

    }

    .content {
      padding: 16px 16px 24px;
      display: grid;
      grid-template-columns: 1fr;
      grid-template-rows: 22px 1fr 30px;
      row-gap: 16px;

      .title {
        font-family: 'Source Sans Pro';
        font-style: normal;
        font-weight: 600;
        font-size: 20px;
        line-height: 21px;
        color: #3F3F3F;
        overflow: hidden;
        text-overflow: ellipsis;
      }

      .subtitle {
        font-family: 'Source Sans Pro';
        font-style: normal;
        font-weight: 400;
        font-size: 17px;
        line-height: 20px;
        overflow-y: auto;
        color: #3F3F3F;
        word-wrap: break-word;
        max-height: 96px;

        @media screen and (max-width: 400px){
          max-height: 120px;
        }

        @media screen and (max-width: 600px){
          font-size: 15px;
          max-height: 76px;
        }

      }
      .price {
        font-family: 'Source Sans Pro';
        font-style: normal;
        font-weight: 600;
        font-size: 24px;
        line-height: 30px;
        color: #3F3F3F;

        @media screen and (max-width: 600px){
          font-size: 17px;
        }
      }
      @media screen and (max-width: 600px){
        row-gap: 6px;
      }
    }
    @media screen and (max-width: 500px){
      height: 400px;
      margin-bottom: 20px;
    }
  }

</style>
