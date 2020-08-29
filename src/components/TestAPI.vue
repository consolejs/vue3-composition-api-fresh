<template>
<div class="hooks-one">
    <h2>TestAPI {{ msg }}</h2>
    <p>count is {{ count }}</p>
    <p>plusOne is {{ plusOne }}</p>
    <button @click="increment">count +1 </button>
    <p>multiplyTwo is {{ multiplyTwo }}</p>
    <button @click="treble">count 2倍</button>
</div>
</template>

<script lang="js">
import {
    ref, //响应式系统 API,  接受一个参数值并返回一个响应式且可改变的 ref 对象。ref 对象拥有一个指向内部值的单一属性 .value。
    computed,//计算属性
    watch, //侦听器, 提供了一个更通用的方法，来响应数据的变化
    onMounted //生命周期钩子
} from 'vue'

export default {
    data(){
        return{
            // 
        }
    },
    setup() {
        // reactive state 响应式数据
        const count = ref(0)
        // computed state
        const plusOne = computed(() => count.value + 1)
        const multiplyTwo = computed(() => count.value * 2)

        // method
        const increment = () => {
            count.value++
        }
        const treble = () => {
            if(count.value > 0){
                count.value *= 2
            }
        }
        
        // watch
        watch(() => count.value + 1, val => {
            console.log(`current count is ${val}`)
        })
        
        // lifecycle
        onMounted(() => {
            console.log(`mounted`)
        })
        
        // expose bindings on render context
        return {
            count,
            plusOne,  //加1
            increment,
            multiplyTwo,//乘2
            treble
        }
    }
}
</script>

<style lang="css">
    .hooks-one{
        padding: 20px 0;
        background-color: teal;
        color: bisque;
    }
    button{
        background-color: cadetblue;
        color: bisque;
        padding: 10px 20px;
        border-radius: 20px;
        font-size: 16px;
    }
</style>