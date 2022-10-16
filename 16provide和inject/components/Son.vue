<template>
  <div id="son">
    <h3>我是子组件</h3>
    <grandSon />
  </div>
</template>
<script>
import grandSon from "./grandSon.vue";
export default {
  name: "App",
  components: {
    grandSon,
  },
};
</script>

<style>
#son {
  background-color: pink;
  padding: 10px;
}
</style>