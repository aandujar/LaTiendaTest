<template>
  <div id="app">
    <actions
      class="component"
      ref="actions"
      @subtrack="subtrack"
      @changeCurrently="changeCurrently"
      @add="add"
    />
    <my-input class="component" ref="myInput" />
    <my-button
      class="component"
      text="Realizar petición post"
      @clicked="sendPostRequest"
    />
  </div>
</template>

<script>
import MyInput from "./components/my-input.vue";
import Actions from "./components/actions.vue";
import MyButton from "./components/my-button.vue";

export default {
  name: "App",
  components: {
    MyInput,
    Actions,
    MyButton,
  },
  methods: {
    subtrack(value) {
      this.$refs.myInput.subtrackFromValue(Number(value));
    },
    changeCurrently(value) {
      this.$refs.myInput.setCurrently(Number(value));
    },
    add(value) {
      this.$refs.myInput.addToValue(Number(value));
    },
    sendPostRequest() {
      const dataToSend = {
        value: this.$refs.myInput.value,
        delta: this.$refs.actions.newValue,
        nombre: "Alejandro",
      };
      
      fetch("https://orqphp.latiendahome.net/vue/test", {
        mode: "no-cors",
        method: "POST",
        body: dataToSend,
      });
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  width: 100vw;

  .component {
    margin-top: 10px;
    margin-bottom: 10px;
  }
}
</style>
