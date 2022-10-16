<template>
  <div id="son">
    <h3>我是子组件</h3>
    {{ sum }}
  </div>
</template>
<script>
import { ref } from "@vue/reactivity";
export default {
  name: "App",
  async setup() {
    let sum = ref(0);
    let p = new Promise((resolve, reject) => {
      setTimeout(() => {
        resolve({ sum });
      }, 3000);
    });
    console.log(p);
    return await p;
  },
};
</script>

<style>
#son {
  background-color: pink;
  padding: 10px;
}
</style>