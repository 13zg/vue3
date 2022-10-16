<template>
  <!-- 可以没有根标签 -->
  <h3>姓名：{{ name }}</h3>
  <h3>年龄：{{ age }}</h3>
  <h3>职业：{{ type }}</h3>
  <h3>薪资：{{ salary }}</h3>
  <button @click="name += '~'">修改姓名</button>
  <button @click="age++">修改年龄</button>
  <button @click="salary += 1000">修改薪资</button>
</template>

<script>
import { reactive, ref, toRef, toRefs } from "@vue/reactivity";
export default {
  name: "Demo",
  setup() {
    let test = ref("好好");
    console.log(test);
    let p = reactive({
      name: "zt",
      age: 18,
      job: {
        j1: {
          type: "UI",
          salary: 2000,
        },
      },
    });
    const test1 = toRef(p, "name");
    console.log(test1);
    const test2 = toRefs(p);
    console.log(test2);
    return {
      name: toRef(p, "name"),
      age: toRef(p, "age"),
      type: toRef(p.job.j1, "type"),
      salary: toRef(p.job.j1, "salary"),
    };
  },
};
</script>

<style>
</style>
