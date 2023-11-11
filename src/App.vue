<template>
  <div id="app">
    <vuelidate-form />
  </div>
</template>

<script>
import VuelidateForm from "./components/VuelidateForm/VuelidateForm.vue";

export default {
  name: "App",
  components: {
    VuelidateForm,
  },
};
</script>

<style>
@import url("./styles/global.css");
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
