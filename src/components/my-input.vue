<template>
  <div class="my-input">
    <my-button text="-" rounded @clicked="subtrackFromValue(null)" />
    <input
      type="number"
      class="text"
      :class="{
        'text--red': value < 0,
        'text--green': value > 0,
        'text--blue': value === 0,
      }"
      v-model="value"
    />
    <my-button text="+" rounded @clicked="addToValue(null)" />
  </div>
</template>

<script>
import MyButton from "./my-button.vue";

export default {
  name: "my-input",
  components: {
    MyButton,
  },
  data: function () {
    return {
      value: 0,
    };
  },
  watch: {
    valueToSubtrack() {
      if (this.valueToSubtrack.toString().length > 0) {
        this.value -= this.valueToSubtrack;
      }
    },
    currentlyValue() {
      if (this.currentlyValue.toString().length > 0) {
        this.value = this.currentlyValue;
      }
    },
    valueToAdd() {
      if (this.valueToAdd.toString().length > 0) {
        this.value += this.valueToAdd;
      }
    },
  },
  methods: {
    subtrackFromValue(newValue = null) {
      if (null === newValue) {
        this.value--;
      } else {
        this.value -= newValue;
      }
    },
    addToValue(newValue = null) {
      if (null === newValue) {
        this.value++;
      } else {
        this.value += newValue;
      }
    },
    setCurrently(newValue) {
      this.value = newValue;
    },
  },
};
</script>

<style lang="scss" scoped>
.my-input {
  display: flex;
  flex-direction: row;

  .text {
    font-size: 14px;

    &--red {
      color: red;
    }

    &--blue {
      color: blue;
    }

    &--green {
      color: green;
    }
  }
}
</style>