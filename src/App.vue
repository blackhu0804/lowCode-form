<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" />
  <p>{{ state.name }} {{ name2 }}</p>
</template>

<script lang="ts">
import { defineComponent, reactive, computed, watchEffect } from "vue";
import HelloWorld from "./components/HelloWorld.vue";

export default defineComponent({
  name: "App",
  components: {
    HelloWorld
  },
  mounted() {
    console.log(this.name2);
  },
  setup(props, { slots, attrs, emit }) {
    const state = reactive({
      name: 1
    });

    const computedNameRef = computed(() => {
      return state.name + "2";
    });

    watchEffect(() => {
      console.log(state.name);
    });

    return {
      state,
      name2: computedNameRef
    };
  }
});
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
