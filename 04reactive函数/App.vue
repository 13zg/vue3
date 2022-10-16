<template>
  <!-- 可以没有根标签 -->
  <h3>姓名：{{ p.name }}</h3>
  <h3>年龄：{{ p.age }}</h3>
  <h3>职业：{{ p.job.type }}</h3>
  <h3>薪资：{{ p.job.salary }}</h3>
  <h2>爱好：</h2>
  <li v-for="(h, index) in p.hobby" :key="index">{{ h }}</li>
  <button @click="changeInfo">修改信息</button>
</template>

<script>
import { reactive } from "vue";
export default {
  name: "App",

  //reactive函数实现，由于只能处理对象，所以全部放在一个对象中
  setup() {
    let p = reactive({
      name: "zt",
      age: 18,
      job: {
        type: "UI设计",
        salary: "5k",
      },
      hobby: ["学习", "看书", "洗澡"],
    });
    function changeInfo() {
      (p.name = "Yee"),
        (p.age = 20),
        (p.job.type = "web前端"),
        (p.job.salary = "8k");
      p.hobby[0] = "吃饭";
    }
    return {
      p,
      changeInfo,
    };
  },
};
</script>

<style>
</style>
