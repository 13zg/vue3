
<template>
  <!-- 可以没有根标签 -->
  <input type="text" v-model="keyword" />
  <h3>{{ keyword }}</h3>
</template>

<script>
import { customRef } from "@vue/reactivity";
export default {
  name: "Demo",
  setup() {
    let keyword = myRef("hello", 500);
    function myRef(value, delay) {
      return customRef((track, trigger) => {
        let timer;
        return {
          get() {
            console.log(`读取的值为${value}`);
            track();
            return value;
          },
          set(newval) {
            clearTimeout(timer);
            console.log(`修改值为${newval}`);
            timer = setTimeout(() => {
              value = newval;
              trigger();
            }, delay);
          },
        };
      });
    }
    return {
      keyword,
    };
  },
};
</script>

<style>
</style>

