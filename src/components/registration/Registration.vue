<template>
    <div class="registration">
      <button class="registration__close" @click="$emit('close')"></button>
      <h1 class="registration__title">Create account</h1>
      <RegistrationSteps />
      <div class="registration__wrapper">
        <div class="registration__banner">
          <span class="banner__text">Sign Up & Get</span>
          <span class="banner__text text--golden">400 EUR + 250 FS</span>
        </div>
        <div class="registration__form">
          <div class="registration__row">
            <RegistrationInput
              type="text"
              label="Email"
              placeholder="Enter Email"
              name="email"
            />
          </div>
          <div class="registration__row">
            <RegistrationInput
              type="password"
              label="Password"
              placeholder="Enter Password"
              name="password"
            /> 
          </div>
          <div class="registration__row registration__row--flex">
            <RegistrationSelect
              :options="countryOptions"
              label="Country"
              placeholder="Select Country"
            />
            <RegistrationSelect
              :options="currencyOptions"
              label="Currency"
              placeholder="Currency"
            />
          </div>   
          <RegistrationCheckbox text="I'd like to recieve essential notifications" />
          <Button text="Sign Up" />
          <div class="registration__terms">
            By Tapping "Sign up", you accept the 
            <a href="#">Terms ans Conditions and Privacy Policy</a>
          </div>
        </div>
      </div>
    </div>
</template>

<script>
import Button from '../Button.vue';
import RegistrationInput from './RegistrationInput.vue';
import RegistrationCheckbox from './RegistrationCheckbox.vue';
import RegistrationSteps from './RegistrationSteps.vue';
import RegistrationSelect from './RegistrationSelect.vue';

export default {
  name: 'Registration',
  data() {
    return {
      countryOptions: [
        { title: 'Ukraine', img: 'ukr' },
        { title: 'USA', img: 'usa' },
        { title: 'Japan', img: 'jpn' },
        { title: 'Ukraine', img: 'ukr' },
        { title: 'USA', img: 'usa' },
        { title: 'Japan', img: 'jpn' },
        { title: 'Ukraine', img: 'ukr' },
        { title: 'USA', img: 'usa' },
        { title: 'Japan', img: 'jpn' },
      ],
      currencyOptions: [
        { title: 'USD' },
        { title: 'EUR' },
      ],
    }
  },
  components: {
    Button,
    RegistrationInput,
    RegistrationCheckbox,
    RegistrationSteps,
    RegistrationSelect,
  },
}
</script>

<style lang="scss">
  $c-primary: #666d97;
  $c-secondary: #2e2f6f;
  $c-white: #fff;

  .registration {
    position: relative;
    max-width: 750px;
    width: 100%;
    padding: 40px;
    background-color: #0c0d39;
    color: $c-primary;

    &__close {
      position: absolute;
      top: 15px;
      right: 30px;
      background: url('../../assets/close.svg');
      width: 30px;
      height: 30px;
      opacity: .6;
      transition: opacity .2s;
      cursor: pointer;

      &:hover {
        opacity: 1;
      }
    }

    &__title {
      color: $c-white;
      text-align: center;
      font-size: 28px;
      margin-bottom: 20px;
    }

    &__banner {
      width: 440px;
      min-height: 420px;
      padding: 40px 20px 0;
      margin-right: 40px;
      background-color: $c-secondary;
      border-radius: 8px;
      color: $c-white;
      text-align: center;
      font-size: 24px;
      font-weight: 700;
      line-height: 32px;
    }

    &__wrapper {
      display: flex;
    }

    &__form {
      display: flex;
      flex-direction: column;
    }

    &__row {
      margin-bottom: 25px;

      &--flex {
        display: flex;
        justify-content: space-between;
      }
    }

    &__terms {
      text-align: center;
      line-height: 20px;
      color: #97a2cb;
      font-size: 14px;

      & a {
        color: #7d77e9;
        font-weight: 600;
        text-decoration: none;
        transition: color .2s;

        &:hover {
          color: darken($color: #7d77e9, $amount: 7);
        }
      }
    }
  }

  .banner__text {
    display: inline-block;
  }

  .text--golden {
    color: #f4b03e;
  }

  @media (max-width: 620px) {
    .registration {
      padding: 20px 15px;
      height: 100vh;

      &__close { 
        right: 10px;
      }

      &__title {
        font-size: 24px;
      }

      &__wrapper {
        display: block;
      }

      &__banner {
        display: none;
      }
    }
  }
</style>
