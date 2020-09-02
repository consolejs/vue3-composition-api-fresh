<template>
  <div class="module setup" :style="boxStyle">
    <h3>Setup --> BackgroundColor:{{ colorValue }}</h3>
    <p>{{ count }} : {{ objectRea.foo }}</p>
    <button @click="onClick()">点我试试~</button>
  </div>
</template>

<script>
import {
  h,
  watchEffect,
  ref, //响应式系统 API,  接受一个参数值并返回一个响应式且可改变的 ref 对象。ref 对象拥有一个指向内部值的单一属性 .value。
  reactive, //响应式系统 API,  接收一个普通对象然后返回该普通对象的响应式代理
  defineComponent, // 主要是为了让TS类型提示变得友好一点
} from "vue";

import getRandomColor from "../libs/getRandomColor.js";

//随机颜色值 16hex
const colorValue = getRandomColor();

export default defineComponent({
  props: {
    name: String,//指定类型 string
  },
  data() {
    return {
      count: 0,
      colorValue,
      boxStyle: {
        "background-color": colorValue,
      },
    };
  },
  /**
   * setup 函数是一个新的组件选项。
   * 作为在组件内使用 Composition API 的入口点
   * 调用时机:
   * 创建组件实例,->初始化 props,->调用setup
   * 模板中使用:
   * 返回一个对象时，则对象的属性将会被合并到组件模板的渲染上下文: {{ objectRea.foo }}, 不需要写 '.value'
   */
  setup(props, { attrs }) {
    const countRef = ref(0);
    const objectRea = reactive({
      foo: "bar",
    });

    // 注意 props 对象是响应式的，watchEffect 或 watch 会观察和响应 props 的更新：
    watchEffect(() => {
      console.log(`Name is: ` + props.name);
    });

    // 创建虚拟dom
    const vNode = h("div", `Hello! ${props.name}`);
    console.log("setUp: vNode -> ", vNode);

    // 一个可能之后回调用的签名
    function onClick() {
      console.log('setUp:', attrs.foo); // 一定是最新的引用，没有丢失响应性
    }

    // return 的属性会暴露给模板，
    //模板中可以直接使用,
    //这里没有 return 的，无法在模板中使用
    return {
      countRef,
      objectRea,
      onClick,
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
