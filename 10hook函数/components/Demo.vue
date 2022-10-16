<template>
  <!-- 可以没有根标签 -->
  <h3>当前总和：{{ sum }}</h3>
  <button @click="sum++">点我+1</button>
  <h3>当前鼠标的坐标时x:{{ point.x }} y:{{ point.y }}</h3>
</template>
<script>
import { ref } from "vue";
import usepoint from "../hook/usePoint";
export default {
  name: "App",
  setup() {
    let sum = ref(0);
    const point = usepoint();
    return {
      sum,
      point,
    };
  },
};
</script>

<style>
</style>
