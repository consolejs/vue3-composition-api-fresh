<template>
<div class="module setup" :style="boxStyle">
    <h3>Setup --> BackgroundColor:{{ colorValue }}</h3>
    <p>{{ count }} : {{ objectRea.foo }}</p>
</div>
</template>

<script>
import {
    ref, //响应式系统 API,  接受一个参数值并返回一个响应式且可改变的 ref 对象。ref 对象拥有一个指向内部值的单一属性 .value。
    reactive, //响应式系统 API,  接收一个普通对象然后返回该普通对象的响应式代理
    defineComponent, // 主要是为了让TS类型提示变得友好一点
} from "vue";

import getRandomColor from "../libs/getRandomColor.js";

//随机颜色值 16hex
const colorValue = getRandomColor();

export default defineComponent({
    data() {
        return {
            count: 0,
            colorValue,
            boxStyle: {
                "background-color": colorValue
            },
        };
    },
    setup() {
        const countRef = ref(0);
        const objectRea = reactive({
            foo: "bar",
        });

        // return 的属性会暴露给模板，
        //模板中可以直接使用,
        //这里没有 return 的，无法在模板中使用
        return {
            countRef,
            objectRea,
        };
    },
});
</script>

<!--实现组件的私有化,不对全局造成样式污染-->
<style lang="css" scoped>
.setup {
    color: blanchedalmond;
}
</style>
