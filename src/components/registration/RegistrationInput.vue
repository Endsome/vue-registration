<template>
     <div class="input-field" :class="{'input-field--error': error}">
        <label class="input-field__label" :for="name">{{ label }}</label>
        <div class="input-field__wrapper">
            <input
                class="input-field__input"
                :type="typeInput"
                :name="name"
                :placeholder="placeholder"
                v-model="value"
                @blur="validation()"
            >
            <button
                v-if="isShowEye"
                @click="togglePasswordVisible"
                class="input-field__btn input-field__btn--visible"
                :class="{'input-field__btn--active': isActiveEye}"
            ></button>
            <button
                v-if="isShowClearBtn"
                @click="clearValue"
                class="input-field__btn input-field__btn--clear"
            ></button>
        </div>
        <div v-if="error" class="input-field__error">{{ error }}</div>
    </div>
</template>

<script>
export default {
  name: 'RegistrationInput',
  props: {
    type: String,
    label: String,
    placeholder: String,
    name: String,
  },
  data() {
    return {
        typeInput: this.type,
        value: null,
        error: '',
    }
  },
  watch: {
    value() {
        this.error = '';
    },
  },
  computed: {
    isShowEye() {
        return this.name === 'password';
    },
    isActiveEye() {
        return this.isShowEye && this.typeInput === 'text';
    },
    isShowClearBtn() {
        return this.name === 'email' && this.value;
    },
  },
  methods: {
    togglePasswordVisible() {
        this.typeInput = this.typeInput === 'password' ? 'text' : 'password';
    },
    validation() {
        if (this.name === 'email' && !/^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(this.value)) {
            this.error = 'Incorrect email';
        }

        if (this.name === 'password' && this.value.length < 8) {
            this.error = 'Password must be 8 characters or longer';
        }
    },
    clearValue() {
        if (this.value) {
            this.value = '';
        }
    }
  },
}
</script>

<style lang="scss">
    $c-error: #cd5259;

    .input-field {
        $self: &;
        $c-white: #fff;

        &--error {
            #{$self}__label {
                color: $c-error;
            }

            #{$self}__input {
                border-color: $c-error; 
            }
        }

        &__wrapper {
            position: relative;
            display: flex;
            flex-direction: column;
        }

        &__label {
            margin-bottom: 5px;
            font-size: 14px;
        }

        &__input {
            background-color: transparent;
            border: none;
            border-bottom: 2px solid rgba($color: #666d97, $alpha: .3);
            padding: 8px 25px 8px 0;
            font-weight: 600;
            color: $c-white;

            &::placeholder {
                color: $c-white;
            }
        }

        &__error {
            color: $c-error;
            font-size: 12px;
            margin-top: 6px;
        }

        &__btn {
            position: absolute;
            right: 0;
            bottom: 8px;
            width: 20px;
            height: 20px;
            background-color: transparent;
            cursor: pointer;
            transition: opacity .2s;

            &--visible {
                background-image: url('../../assets/eye.svg');
                opacity: .6;
            }

            &--clear {
                background: rgba(0,0,0,.5) url('../../assets/close.svg');
                opacity: .6;
                border-radius: 10px;
                width: 15px;
                height: 15px;
            }

            &--active,
            &:hover {
                opacity: 1; 
            }
        }
    }
</style>
