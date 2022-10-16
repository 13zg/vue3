<template>
  <div id="root">
    <h3>我是父组件</h3>
    <Suspense>
      <template v-slot:default>
        <Son />
      </template>
      <template v-slot:fallback>
        <h3>加载中...</h3>
      </template>
    </Suspense>
  </div>
</template>

<script>
//静态引入
// import Son from "./components/Son.vue";
//异步引入组件
import { defineAsyncComponent } from "vue";
const Son = defineAsyncComponent(() => import("./components/Son.vue"));
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