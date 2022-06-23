<template>
  <div>
    <input v-model="autoCheck" type="checkbox" id="autoCheckCb" />
    <label for="autoCheckCb">Enable Auto Check</label>
    <PalindromeForm :autoCheck="autoCheck" />
  </div>
</template>

<script>
import PalindromeForm from "./components/PalindromeForm.vue";
export default {
  name: "App",
  components: {
    PalindromeForm: PalindromeForm,
  },
  data() {
    return {
      autoCheck: false,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
