<template>
  <button @click="isShow = !isShow">显示/隐藏</button>
  <Demo v-if="isShow" />
</template>

<script>
import { ref } from "@vue/reactivity";
import Demo from "./components/Demo.vue";
export default {
  components: { Demo },
  setup() {
    let isShow = ref(true);
    return {
      isShow,
    };
  },
};
</script>

<style>
</style>