<template>
  <div class="form-wrapper">
    <form
      class="form"
      @submit.prevent="handleSubmit"
    >
      <MyInput
        v-for="item in inputs"
        :key="item.id"
        v-model.lazy="item.value"
        :data="item"
      />

      <MyButton
        v-if="!isLoading"
        :disabled="!isFormValid"
        text-btn="Добавить товар"
      />
      <MyPreloader
        v-if="isLoading"
      />
    </form>
  </div>
</template>

<script>

import MyInput from './MyInput/MyInput.vue';
import MyButton from './MyButton/MyButton.vue';
import MyPreloader from '../MyPreloader/MyPreloader.vue';

const urlRegex = /(https?:\/\/.*)/ig;

export default {
  name: 'MyForm',
  components: {
    MyInput,
    MyButton,
    MyPreloader,
  },
  data() {
    return {
      inputs: [
        {
          id: 1,
          name: 'title',
          textLabel: 'Наименование товара',
          typeInput: 'text',
          textPlaceholder: 'Введите наименование товара',
          required: true,
          isValid: false,
          isError: 'Поле является обязательным',
          value: '',
          isCheckValid() {
            if (!this.value) {
              this.isError = 'Поле является обязательным';
              this.isValid = false;
              return;
            }

            this.isError = '';
            this.isValid = true;
          },
        },
        {
          id: 2,
          name: 'description',
          textLabel: 'Описание товара',
          typeInput: 'textarea',
          textPlaceholder: 'Введите описание товара',
          required: false,
          isError: '',
          isValid: true,
          value: '',
        },
        {
          id: 3,
          name: 'url',
          textLabel: 'Ссылка на изображение товара',
          typeInput: 'url',
          textPlaceholder: 'Введите ссылку',
          required: true,
          isValid: false,
          isError: 'Поле является обязательным',
          value: '',
          async isCheckValid() {
            if (!this.value) {
              this.isError = 'Поле является обязательным';
              this.isValid = false;
              return;
            }

            const validUrl = urlRegex.test(this.value);

            if (!validUrl) {
              this.isError = 'Ccылка не валидная';
              this.isValid = false;
              return;
            }

            let isImgValid = false;
            try {
              const res = await fetch(this.value);
              if (!res.ok) {
                throw new Error('Ccылка не валидная');
              }
              isImgValid = true;
            } catch (error) {
              isImgValid = false;
            }
            if (!isImgValid) {
              this.isValid = false;
              this.isError = 'Ccылка не валидная';
              return;
            }
            this.isError = '';
            this.isValid = true;
          },
        },
        {
          id: 4,
          name: 'price',
          textLabel: 'Цена товара',
          typeInput: 'number',
          textPlaceholder: 'Введите цену',
          required: true,
          isValid: false,
          isError: 'Поле является обязательным',
          value: '',
          isCheckValid() {
            if (!this.value) {
              this.isError = 'Поле является обязательным';
              this.isValid = false;
              return;
            }
            this.isError = '';
            this.isValid = true;
          },
        },
      ],
      dataNewCard: {},
      isLoading: false,
    };
  },
  computed: {
    isFormValid() {
      const indexInput = this.inputs.findIndex((input) => !input.isValid);
      return (indexInput === -1);
    },
  },
  methods: {
    async handleSubmit() {
      this.isLoading = true;
      this.inputs.forEach((item) => {
        this.dataNewCard[item.name] = item.value;
      });
      this.addNewCard(this.dataNewCard);
      this.isLoading = false;
    },
  },
};
</script>

<style lang="scss" scoped>
  .form-wrapper {
    margin-right: 16px;

    @media screen and (max-width: 500px){
      width: 100%;
    }
  }
  .form {
    position: sticky;
    top: 24px;
    padding: 20px 24px 24px;
    width: 332px;
    border-radius: 4px;
    background-color: #FFFEFB;
    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);

    @media screen and (max-width: 744px){
      margin: 0 auto 20px;
    }

    @media screen and (max-width: 500px){
      width: 100%;
    }

    @media screen and (max-width: 400px){
      padding: 14px 18px 18px;
    }
  }

</style>
