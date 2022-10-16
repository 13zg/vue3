<template>
  <!-- 可以没有根标签 -->
  姓：<input type="text" v-model="p.firstName" />
  <br />
  名: <input type="text" v-model="p.lastName" />
  <br />
  全名：<input type="text" v-model="p.fullName" />
</template>

<script>
import { reactive } from "@vue/reactivity";
import { computed } from "@vue/runtime-core";
export default {
  name: "App",
  mounted() {
    console.log(this);
  },
  setup() {
    let p = reactive({
      firstName: "易烊",
      lastName: "千玺",
    });
    //简写方式
    /*  p.fullName = computed(() => {
      return p.firstName + "-" + p.lastName;
    }); */
    p.fullName = computed({
      get() {
        return p.firstName + "-" + p.lastName;
      },
      set(value) {
        const newName = value.split("-");
        p.firstName = newName[0];
        p.lastName = newName[1];
      },
    });
    return {
      p,
    };
  },
};
</script>

<style>
</style>
