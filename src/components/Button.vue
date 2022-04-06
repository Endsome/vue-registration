<template>
    <button class="btn" @click="$emit('click')">{{ text }}</button>
</template>

<script>
export default {
  name: 'Button',
  props: {
      text: String,
  }
}
</script>

<style lang="scss">
    .btn {
        display: block;
        background-color: #d2468b;
        color: #fff;
        border-radius: 20px;
        padding: 12px 20px;
        font-weight: 600;
        max-width: 200px;
        width: 100%;
        margin: 0 auto 40px;
        transition: background-color .2s;
        cursor: pointer;

        &:hover {
            background-color: darken($color: #d2468b, $amount: 4);
        }
    }

    @media (max-width: 620px) {
        .btn {
            margin-bottom: 20px;
        }
    }
</style>
