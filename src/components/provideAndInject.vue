<template>
  <div>
    <h3>{{ customVal }}</h3>
  </div>
</template>
 
<script>
// 子组件导入 inject
import { inject } from "vue";

export default {
  setup() {
    //调用 inject 函数，通过指定的数据名称，获取到父级共享的数据
    const customVal = inject("customVal");
    return {
      customVal,
    };
  },
};
</script>