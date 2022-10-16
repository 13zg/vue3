<template>
  <h3>我是孙组件</h3>
  <Dialog />
</template>
<script>
import Dialog from "./Dialog.vue";
export default {
  name: "App",
  components: {
    Dialog,
  },
};
</script>

<style scoped>
* {
  background-color: orchid;
}
</style>