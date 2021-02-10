<template>
  <div class="my-button">
    <button
      class="item"
      :class="{ 'item--rounded': rounded }"
      type="button"
      @click="$emit('clicked')"
    >
      {{ text }}
    </button>
  </div>
</template>

<script>
export default {
  name: "my-button",
  props: {
    text: { type: String, required: false },
    rounded: { type: Boolean, required: false, default: false },
  },
};
</script>

<style lang="scss" scoped>
.my-button {
  .item {
    margin-left: 5px;
    margin-right: 5px;
    cursor: pointer;

    &--rounded {
      border-radius: 20%;
    }
  }
}
</style>
