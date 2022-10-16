<template>
  <!-- 可以没有根标签 -->
  <h3>当前的和为：{{ sum }}</h3>
  <button @click="sum++">sum+1</button>
  <hr />
  <h3>姓名：{{ name }}</h3>
  <h3>年龄：{{ age }}</h3>
  <h3>薪资：{{ job.j1.salary }}</h3>
  <h3 v-if="p.car">汽车信息：{{ p.car }}</h3>
  <button @click="name += '~'">修改姓名</button>
  <button @click="age++">修改年龄</button>
  <button @click="job.j1.salary += 1000">修改薪资</button>
  <button @click="changeOrigin">修改源数据</button>
  <button @click="addCar">添加一辆车</button>
</template>

<script>
import { reactive, ref, toRaw, toRefs, markRaw } from "@vue/reactivity";
export default {
  name: "Demo",
  setup() {
    let sum = ref(0);
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
    //修改源数据，但是不响应式到页面
    function changeOrigin() {
      const person = toRaw(p);
      person.age++;
      console.log(person);
    }
    function addCar() {
      let car = { number: 13, type: "Benz" };
      //car直接为普通对象，无法修改
      p.car = markRaw(car);
    }
    return {
      ...toRefs(p),
      sum,
      changeOrigin,
      addCar,
      p,
    };
  },
};
</script>

<style>
</style>