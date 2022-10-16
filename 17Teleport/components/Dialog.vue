<template>
  <button @click="isShow = true">弹窗</button>
  <teleport to="body">
    <div id="mask" v-if="isShow">
      <div id="dialog">
        <h4>弹窗示例</h4>
        <h4>一些内容</h4>
        <h4>....</h4>
        <button @click="isShow = false">关闭</button>
      </div>
    </div>
  </teleport>
</template>

<script>
import { ref } from "@vue/reactivity";
export default {
  name: "Dialog",
  setup() {
    let isShow = ref(false);
    return {
      isShow,
    };
  },
};
</script>

<style>
#mask {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
}
#dialog {
  text-align: center;
  position: absolute;
  width: 200px;
  height: 200px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: blueviolet;
}
</style>