<template>
  <!-- 可以没有根标签 -->
  <h3>姓名：{{ name }}</h3>
  <h3>年龄：{{ age }}</h3>
  <h3>薪资：{{ job.j1.salary }}</h3>
  <button @click="name += '~'">修改姓名</button>
  <button @click="age++">修改年龄</button>
  <button @click="job.j1.salary += 1000">修改薪资</button>
</template>

<script>
import { reactive, shallowReactive, toRefs } from "@vue/reactivity";
export default {
  name: "Demo",
  setup() {
    let p = shallowReactive({
      name: "zt",
      age: 18,
      job: {
        j1: {
          type: "UI",
          salary: 2000,
        },
      },
    });
    console.log(toRefs(p));

    return {
      ...toRefs(p),
    };
  },
};
</script>

<style>
</style>
