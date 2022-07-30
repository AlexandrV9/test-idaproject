<template>
  <div class="filter">
    <button>
      <span>По умолчанию</span>
      <img
        src="../../assets/icons/down-arrow.svg"
        alt="иконка стрелки"
      >
    </button>
    <div class="wrapper">
      <ul class="filter-options">
        <li class="filter-option">
          По цене min
        </li>
        <li class="filter-option">
          По цене max
        </li>
        <li class="filter-option">
          По наименованию
        </li>
      </ul>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  .filter {
    position: relative;

    button {
      display: flex;
      align-items: center;
      border: none;
      padding: 10px 16px 11px;
      background: #FFFEFB;
      box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
      border-radius: 4px;
      font-family: 'Source Sans Pro';
      font-weight: 400;
      font-size: 12px;
      line-height: 15px;
      color: #B4B4B4;

      &:hover {
        cursor: pointer;
      }

      span {
        margin-right: 5px;
      }

      img {
        width: 7.5px;
        height: 7.5px;
      }

      @media screen and (max-width: 500px){
        padding: 7px 13px 8px;
      }
    }

    .wrapper {
      bottom: -70px;
      left: 0;
      position: absolute;
      z-index: 10;
      display: none;
      padding-top: 8px;
      width: 100%;

      ul {
        background: #FFFEFB;
        box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
        border-radius: 4px;
        list-style: none;

        li {
          font-family: 'Source Sans Pro';
          font-weight: 400;
          font-size: 12px;
          line-height: 15px;
          color: #B4B4B4;
          width: 100%;
          text-align: center;
          padding: 3px 0;
          transition: all 0.1s ease-in;

          &:hover {
            cursor: pointer;
            background-color: rgb(165 165 165 / 28%);
          }

          &:not(:last-child) {
            border-bottom: 1px solid rgb(0 0 0 / 38%);
          }
        }
      }
    }

  }

  button:hover + .wrapper,
  .filter:hover > .wrapper {
    display: block;
  }

</style>
