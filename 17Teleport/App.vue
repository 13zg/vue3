<template>
  <div id="root">
    <h3>我是祖组件</h3>
    <Son />
  </div>
</template>

<script>
import { reactive, toRefs } from "@vue/reactivity";
import Son from "./components/Son.vue";
import { provide } from "@vue/runtime-core";
export default {
  name: "App",
  components: {
    Son,
  },
};
</script>

<style>
#root {
  background-color: skyblue;
  padding: 10px;
}
</style>