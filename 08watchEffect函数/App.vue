<template>
  <!-- 可以没有根标签 -->
  <h3>当前总和：{{ sum }}</h3>
  <button @click="sum++">点我+1</button>
  <hr />
  <h3>{{ msg }}</h3>
  <button @click="msg += '~'">修改信息</button>
  <hr />
  <h2>个人信息为:</h2>
  <h3>姓名:{{ p.name }}</h3>
  <h3>年龄：{{ p.age }}</h3>
  <h3>薪资:{{ p.job.j1.salary }}k</h3>
  <button @click="p.age++">修改年龄</button>
  <button @click="p.job.j1.salary++">修改薪资</button>
</template>

<script>
import { reactive, ref } from "@vue/reactivity";
import { watch, watchEffect } from "@vue/runtime-core";
export default {
  name: "App",
  setup() {
    let sum = ref(0);
    let msg = ref("你好");
    let p = reactive({
      name: "zt",
      age: 18,
      job: {
        j1: {
          salary: "20",
        },
      },
    });
    watchEffect(() => {
      const x1 = sum.value;
      const x2 = p.age;
      console.log("数据被用到了");
    });
    return {
      sum,
      msg,
      p,
    };
  },
};
</script>

<style>
</style>
