<template>
  <!--template 中通过 ref="root" 的方式和一个 div 绑定了-->
  <div :ref="root"></div>
</template>

<script>
import { ref, toRef, defineComponent, onMounted } from "vue";

export default defineComponent({
  setup() {
    const root = ref(null);

    const state = {
      foo: 1,
      bar: 2,
    };

    const fooRef = toRef(state, "foo");

    fooRef.value++; // fooRef 改变了，state.foo 也会改变
    console.log(state.foo); // 2
    state.foo++;
    console.log(fooRef.value); // 3

    onMounted(() => {
      console.log(root.value);
    });

    return {
      root, //渲染上下文暴露了一个ref 类型的数据 root
    };
  },
});
</script>
