<template>
  <Button class="primary__btn" @click="showModal" text="Registration"></Button>
</template>

<script>
import Button from './components/Button.vue';
import Registration from './components/registration/Registration.vue';

export default {
  name: 'App',
  components: {
    Registration,
    Button
  },
  methods: {
    showModal() {
      this.$modal.show(Registration, {}, {
        adaptive: true,
        height: 'auto',
        width: '100%',
        maxWidth: 750,
      });
    },
  },
  mounted() {
    this.showModal();
  },
}
</script>

<style lang="scss">
  *, :after, :before {
    box-sizing: border-box;
  }

  input {
    outline: none;
  }

  body {
    margin: 0;
    font-family: sans-serif;
  }

  h1 {
    margin: 0;
  }

  button {
    border: none;
  }

  .vm--container {
    .vm--modal {
      border-radius: 10px;

      @media (max-width: 620px) {
        border-radius: 0;
      }
    }
  }

  .primary__btn {
    margin-top: 10px;
  }
</style>
