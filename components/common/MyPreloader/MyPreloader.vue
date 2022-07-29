<template>
  <div class="loader" />
</template>

<script>
export default {
  name: 'MyPreloader',
};
</script>

<style>

  .loader {
    display: flex;
    justify-content: center;
    transition: all 0.4s linear;
    position: relative;
    animation: loading 1s ease infinite;
  }
  .loader::after {
    content: "";
    width: 13px;
    height: 13px;
    border: 3px solid #252931;
    border-top-color: #81838f;
    border-bottom-color: #81838f;
    border-radius: 50%;
  }
  @keyframes loading {
    to {
      transform: rotate(1turn);
    }
  }
</style>
