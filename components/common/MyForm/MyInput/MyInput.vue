<template>
  <div class="field">
    <label :class="data.required ? 'required' : ''">
      {{ data.textLabel }}
    </label>
    <input
      v-if="data.typeInput === 'text' || data.typeInput === 'url'"
      :value="data.value"
      :type="data.typeInput"
      :placeholder="data.textPlaceholder"
      :tabindex="data.id"
      :class="(!data.isValid && isTouched ? 'error' : '')"
      @input="$emit('input', $event.target.value), changeValue()"
      @blur="isTouched = true"
    >
    <input
      v-if="data.typeInput === 'number'"
      v-mask="[
        '# ###',
        '###',
        '#',
        '##',
        '### ### ### ### ### ### ### ### ### ### ### ###',
      ]"
      :value="data.value"
      type="text"
      :placeholder="data.textPlaceholder"
      :tabindex="data.id"
      :class="(!data.isValid && isTouched ? 'error' : '')"
      @input="$emit('input', $event.target.value), changeValue(), $emit('valid')"
      @blur="isTouched = true"
    >
    <textarea
      v-if="data.typeInput === 'textarea'"
      :value="data.value"
      :placeholder="data.textPlaceholder"
      class="test-idaproject__textarea"
      @input="$emit('input', $event.target.value)"
    />
    <span
      v-if="data.isError && isTouched"
      class="test-idaproject__field-error"
    >{{ data.isError }}</span>
  </div>
</template>

<script>
export default {
  name: 'MyInput',
  props: {
    data: {
      type: Object,
      required: true,
    },
  },
  emits: ['input', 'valid'],
  data() {
    return {
      isTouched: false,
    };
  },
  methods: {
    changeValue() {
      this.data.isCheckValid();
    },
  },
};
</script>

<style lang="scss" scoped>
.field {
  position: relative;
  &:not(:last-child) {
    margin-bottom: 11px;
  }
  label {
    position: relative;
    font-family: "Source Sans Pro";
    font-weight: 400;
    font-size: 10px;
    line-height: 13px;
    letter-spacing: 0.02em;
    color: #49485e;

    &.required::after {
      content: "";
      position: absolute;
      width: 4px;
      height: 4px;
      top: 0;
      right: -4px;
      background: #ff8484;
      border-radius: 4px;
    }
  }
  input,
  textarea {
    width: 100%;
    padding: 10px 16px 11px;
    background: #fffefb;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
    border-radius: 4px;
    font-family: "Source Sans Pro";
    letter-spacing: 0.04em;
    font-weight: 400;
    font-size: 12px;
    line-height: 15px;
    color: #b4b4b4;
    outline: none;
    margin-top: 4px;
    border: 1px solid transparent;
    transition: all 0.2s ease-in;

    textarea {
      resize: vertical;
      min-height: 104px;
      max-height: 400px;
      padding-left: 10px;
    }

    &:focus {
      transform: scale(1.05);
      border: 1px solid rgb(0, 68, 255);
      background-color: rgb(243, 243, 243);
    }
  }
  span {
    position: absolute;
    bottom: -14px;
    left: 0;
    font-family: "Source Sans Pro";
    font-style: normal;
    font-weight: 400;
    font-size: 8px;
    line-height: 10px;
    letter-spacing: -0.02em;
    color: #ff8484;
  }
  input.error {
    border: 1px solid #ff8484;
  }
}
</style>
