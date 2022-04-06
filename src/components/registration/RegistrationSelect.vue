<template>
  <div class="select-field">
    <label class="select-field__label">{{ label }}</label>
    <div
      class="select-field__wrapper"
      :class="{'select-field__wrapper--open': isOpen}"
      @blur="hideOptions"
      tabindex="0"
    >
      <div class="select-field__selected" @click="toggleOptions">
        <div v-if="selectedItem">
            <picture v-if="selectedItem.img">
              <source
                type="image/jpg"
                :srcset="`${require(`../../assets/flags/${selectedItem.img}.jpg`)} 1x, ${require(`../../assets/flags/${selectedItem.img}@2x.jpg`)} 2x`"
                media="(max-width: 620px)"
              >
              <img
                v-if="selectedItem.img"
                class="select-field__img select-field__img--selected"
                :src="require(`../../assets/flags/${selectedItem.img}.jpg`)"
                :srcset="`${require(`../../assets/flags/${selectedItem.img}@2x.jpg`)} 2x`"
                alt="img"
              >
            </picture>
            <span>{{ selectedItem.title }}</span>
        </div>
        <div v-else class="select-field__placeholder">{{ placeholder }}</div>
      </div>
      <div v-if="isOpen" class="select-field__list">
        <div
          v-for="(option, i) in options"
          :key="i"
          @click="selectOption(option)"
          class="select-field__item"
        >
          <picture v-if="option.img">
              <source
                type="image/jpg"
                :srcset="`${require(`../../assets/flags/${option.img}.jpg`)} 1x, ${require(`../../assets/flags/${option.img}@2x.jpg`)} 2x`"
                media="(max-width: 620px)"
              >
              <img
                v-if="option.img"
                class="select-field__img"
                :src="require(`../../assets/flags/${option.img}.jpg`)"
                :srcset="`${require(`../../assets/flags/${option.img}@2x.jpg`)} 2x`"
                alt="img"
              >
            </picture>
          <span>{{ option.title }}</span>
        </div>
      </div>
    </div>
  </div>
    
</template>

<script>
export default {
  name: 'RegistrationSelect',
  props: {
    options: Array,
    placeholder: String,
    label: String,
  },
  data() {
    return {
        selectedItem: null,
        isOpen: false,
    };
  },
  methods: {
    hideOptions() {
        this.isOpen = false;
    },
    toggleOptions() {
        this.isOpen = !this.isOpen;
    },
    selectOption(option) {
        this.selectedItem = option;
        this.isOpen = false;
    },
  },
};
</script>

<style lang="scss">
  $c-primary: #666d97;
  $c-secondary: #2e2f6f;
  $c-white: #fff;

  .select-field {
    width: 46%;

    &__wrapper {
      position: relative;
      outline: none;

      &::after {
      content: '';
        position: absolute;
        right: 4px;
        top: 8px;
        width: 8px;
        height: 8px;
        border-left: 2px solid rgba($color: $c-primary, $alpha: .4);
        border-bottom: 2px solid rgba($color: $c-primary, $alpha: .4);
        transform: rotate(-45deg);
      }

      &--open {
        &::after {
          transform: rotate(-225deg);
          top: 10px;
        }
      }
    }

    &__label {
      font-size: 14px;
    }

    &__placeholder {
      color: rgba($color: $c-primary, $alpha: .5);
    }

    &__selected {
      padding: 8px 25px 8px 0;
      border-bottom: 2px solid rgba($color: $c-primary, $alpha: .3);
      color: $c-white;
      cursor: pointer;
    }

    &__list {
      position: absolute;
      left: 0;
      right: 0;
      z-index: 1;
      overflow: auto;
      max-height: 150px;
      background-color: $c-secondary;
      border-radius: 0 0 6px 8px;
    }

    &__img {
      margin-right: 8px;
    }

    &__item {
      color: #97a2cb;
      padding: 5px;
      cursor: pointer;
      transition: background-color .2s, color .2s;

      &:hover {
        background-color: darken($color: $c-secondary, $amount: 8);
        color: $c-white;
      }
    }

    ::-webkit-scrollbar {
      width: 2px;
    }

    ::-webkit-scrollbar-thumb {
      background-color: $c-primary;
      border-radius: 2px;
    }
  }
</style>