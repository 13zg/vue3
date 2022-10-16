<template>
  <div id="root">
    <h3>我是祖组件---{{ name }}---{{ age }}</h3>
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
  setup() {
    let info = reactive({
      name: "zt",
      age: 18,
    });
    provide("info", info);
    return {
      ...toRefs(info),
    };
  },
};
</script>

<style>
#root {
  background-color: skyblue;
  padding: 10px;
}
</style>