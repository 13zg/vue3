<template>
  <!-- 可以没有根标签 -->
  <h3>姓名：{{ name }}</h3>
  <h3>年龄：{{ age }}</h3>
  <h3>职业：{{ job.type }}</h3>
  <h3>薪资：{{ job.salary }}</h3>
  <button @click="changeInfo">修改信息</button>
</template>

<script>
import { h, ref } from "vue";
export default {
  name: "App",
  //ref函数实现
  setup() {
    let name = ref("zt");
    let age = ref(18);
    let job = ref({
      type: "UI设计",
      salary: "5k",
    });
    function changeInfo() {
      name.value = "Yee";
      age.value = 20;
      job.value.type = "web前端";
    }
    return {
      name,
      age,
      job,
      changeInfo,
    };
  },
};
</script>

<style>
</style>
