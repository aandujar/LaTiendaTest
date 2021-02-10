<template>
  <div class="actions">
    <!-- value to subtrack or add -->
    <div class="item">
      <div class="item__input">
        <label>Unidades a sumar o restar:</label>
        <input type="number" class="my-input__text" v-model="newValue" />
      </div>
      <my-button class="item__button" text="-" rounded @clicked="subtrack" />
      <my-button class="item__button" text="+" rounded @clicked="add" />
    </div>
    <!-- value to init -->
    <div class="item">
      <div class="item__input">
        <label>Número inicial:</label>
        <input type="number" v-model="currentlyValue" />
      </div>
      <my-button class="item__button" text="+" rounded @clicked="setCurrentlyValue" />
    </div>
  </div>
</template>

<script>
import MyButton from "./my-button.vue";
export default {
  name: "Actions",
  components: {
    MyButton,
  },
  data: function () {
    return {
      newValue: 0,
      currentlyValue: 0,
    };
  },
  methods: {
    subtrack() {
      this.$emit("subtrack", this.newValue);
    },
    setCurrentlyValue() {
      this.$emit("changeCurrently", this.currentlyValue);
    },
    add() {
      this.$emit("add", this.newValue);
    },
  },
};
</script>

<style lang="scss" scoped>
.actions {
  display: flex;
  flex-direction: row;

  .item {
    display: flex;
    flex-direction: row;
    margin-left: 10px;
    margin-right: 10px;

    &__input {
      display: flex;
      flex-direction: column;
    }

    &__button {
      align-self: flex-end;
    }
  }
}
</style>