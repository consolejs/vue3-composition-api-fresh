<!--
    * 说明:
    * provide() 和 inject() 可以实现嵌套组件之间的数据传递
    * 这两个函数只能在 setup() 函数中使用
    * 父级组件中使用 provide() 函数向下传递数据
    * 子级组件中使用 inject() 获取上层传递过来的数据
    * 不限层级
    * 父组件可以通过ref创建响应式数据通过provide 共享给子组件
-->


<template>
  <div class="module injection" :style="boxSyle">
    <h3>Injection.</h3>
    <p>
      <provideAndInject />
    </p>
  </div>
</template>

<script lang="js">
import {
    defineComponent,
    provide  // 父组件引入 provide
} from "vue"

import getRandomColor from "../libs/getRandomColor";
import provideAndInject from "./provideAndInject.vue";  // 引入子组件

//随机颜色值 16hex
const colorValue = getRandomColor();

export default defineComponent({
    name: "injectAncestor",
    components: {
        provideAndInject
    },
    data(){
        return{
            boxSyle: {
                "background-color": colorValue
            }
        }
    },
    setup() {

        const obj = {
            "data": "我是父组件向子组件传递的值"
        }
        // provide('数据名称', 要传递的数据)
        provide("customVal", obj.data); 

        return {
            // 
        }
    }
})
</script>

<style lang="css" scoped>
.injection {
  color: cornsilk;
}
</style>