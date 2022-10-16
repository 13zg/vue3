<template>
  <h3>我是孙组件--{{ name }}--{{ age }}</h3>
</template>
<script>
import { inject, toRefs } from "@vue/runtime-core";
export default {
  name: "App",
  setup() {
    let info = inject("info");
    return {
      ...toRefs(info),
    };
  },
};
</script>

<style scoped>
* {
  background-color: orchid;
}
</style>