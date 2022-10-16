<template>
  <Demo @test="Test" msg="你好">
    <template v-slot:test2>
      <h3>学习中</h3>
    </template>
  </Demo>
</template>

<script>
import Demo from "./components/Demo.vue";
export default {
  name: "App",
  components: {
    Demo,
  },
  setup() {
    function Test(value) {
      console.log("收到的值为：", value);
    }
    return {
      Test,
    };
  },
};
</script>

<style>
</style>