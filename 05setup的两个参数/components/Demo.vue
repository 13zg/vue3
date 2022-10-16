<template>
  <!-- 可以没有根标签 -->
  <h2>信息</h2>
  <h3>姓名：{{ p.name }}</h3>
  <h3>年龄：{{ p.age }}</h3>
  <slot name="test2"></slot>
  <button @click="test1">测试emit</button>
</template>

<script>
import { reactive } from "@vue/reactivity";
export default {
  name: "App",
  props: ["msg"],
  emits: ["test"],
  setup(props, context) {
    let p = reactive({
      name: "zt",
      age: 18,
    });
    console.log("接收的第一个参数", props);
    //如果利用了props接收了。则没有值
    console.log("接收的第二个参数的$attr", context.attrs);
    //测试contex.emit
    function test1() {
      context.emit("test", p.name);
    }
    console.log("接收的第二个参数的slot", context.slots);
    return {
      p,
      test1,
    };
  },
};
</script>

<style>
</style>
