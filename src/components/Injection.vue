<template>
  <div class="module injection" :style="boxSyle">
    <h3>Injection.</h3>
    <p>
      <provideAndInject />
    </p>
  </div>diuv
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