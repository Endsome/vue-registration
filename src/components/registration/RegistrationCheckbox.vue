<template>
    <label class="checkbox-field">
        <input class="checkbox-field__input" type="checkbox">
        <span class="checkbox-field__custom"></span>
        <span class="checkbox-field__text">{{ text }}</span>
    </label>
</template>

<script>
export default {
  name: 'RegistrationCheckbox',
  props: {
      text: String,
  }
}
</script>

<style lang="scss">
    .checkbox-field {
        display: flex;
        align-items: center;
        margin-bottom: 25px;
        font-size: 14px;

        &__input {
            display: none;
        }

        &__custom {
            position: relative;
            display: inline-block;
            width: 16px;
            height: 16px;
            margin-right: 8px;
            border: 1px solid #666d97;
            border-radius: 2px;
            cursor: pointer;

            &::before {
                content: '';
                position: absolute;
                top: 50%;
                left: 50%;
                transform: translate(-50%, -50%);
                opacity: 0;
                transition: opacity .3s;
                width: 8px;
                height: 8px;
                border-radius: 1px;
                background-color: #7d77e9;
            }
        }
    }

    .checkbox-field__input:checked + .checkbox-field__custom::before {
        opacity: 1;
    }
</style>
