<template>
  <!-- 可以没有根标签 -->
  <h3>姓名：{{ name }}</h3>
  <h3>年龄：{{ age }}</h3>
  <button @click="sayHello">点击</button>
</template>

<script>
import { h } from "vue";
export default {
  name: "App",
  //未实现响应式
  setup() {
    let name = "zt";
    let age = 18;
    function sayHello() {
      alert(`你好，${name}`);
    }
    return {
      name,
      age,
      sayHello,
    };
    //直接返回一个渲染函数
    // return () => h("h3", age);
  },
};
</script>

<style>
</style>
