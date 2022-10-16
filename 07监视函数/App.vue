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
import { watch } from "@vue/runtime-core";
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
    console.log(p);
    //情况一：监视ref定义的一个响应式数据
    watch(sum, (newval, oldval) => {
      console.log("sum改变了", newval, oldval);
    });
    //情况二：监视ref定义的多个响应式数据
    watch([sum, msg], (newval, oldval) => {
      console.log("sum或msg改变了", newval, oldval);
    });
    //情况三：监视reactive定义的一个响应式对象
    watch(p, (newval, oldval) => {
      console.log("p对象发生改变了", newval, oldval);
    });
    //情况四：监视reactive定义的响应式对象中的一个属性
    watch(
      () => p.age,
      (newval, oldval) => {
        console.log("年龄发生变化了", newval, oldval);
      }
    );
    //情况五：监视reactive定义的响应式数据中的某些属性
    watch([() => p.age, () => p.name], (newval, oldval) => {
      console.log("年龄或姓名发生变化了", newval, oldval);
    });
    //特殊情况:监视reactive定义的响应式数据中的某个对象属性
    watch(
      () => p.job,
      (newval, oldval) => {
        console.log("薪资发生变化了", newval, oldval);
      },
      { deep: true }
    );
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
