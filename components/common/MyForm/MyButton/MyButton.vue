<template>
  <button
    :class="'test-idaproject__button ' + (disabled ? 'disabled' : 'active')"
    :disabled="disabled"
  >
    {{ textBtn }}
  </button>
</template>

<script>
export default {
  name: 'MyButton',
  props: {
    textBtn: {
      type: String,
      required: true,
    },
    disabled: {
      type: Boolean,
      required: true,
    },
  },
};
</script>

<style>
  .test-idaproject__button {
    width: 100%;
    padding: 10px 0 11px;
    margin: 0;
    border: none;
    background: #EEEEEE;
    border-radius: 10px;
    font-family: 'Inter';
    font-weight: 600;
    font-size: 13px;
    line-height: 15px;
    letter-spacing: -0.02em;
    margin-top: 12px;
    transition: all 0.2s ease-in;
  }
  .test-idaproject__button.active {
    background: #7BAE73;
    color: #FFFFFF;
  }
  .test-idaproject__button.disabled {
    background: #EEEEEE;
    color: #B4B4B4;
  }
</style>
