<template>
  <!-- 可以没有根标签 -->
  <h3>当前总和：{{ sum }}</h3>
  <button @click="sum++">点我+1</button>
</template>

<script>
import {
  ref,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
} from "vue";
export default {
  name: "App",
  setup() {
    let sum = ref(0);
    onBeforeMount(() => {
      console.log("----onBeforeMount");
    }),
      onMounted(() => {
        console.log("----onMounted");
      });
    onBeforeUpdate(() => {
      console.log("----onBeforeUpdate");
    }),
      onUpdated(() => {
        console.log("----onUpdate");
      });
    onBeforeUnmount(() => {
      console.log("---onBeforeUnmount");
    });
    onUnmounted(() => {
      console.log("----onUnmounted");
    });
    return {
      sum,
    };
  },
};
</script>

<style>
</style>
