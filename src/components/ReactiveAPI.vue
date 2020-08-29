<template>
<div class="module reactive-api">
    <h2>Reactive API {{ msg }}</h2>
    <p>count is {{ count }}</p>
    <p>plusOne is {{ plusOne }}</p>
    <button @click="increment">count +1</button>
    <p>multiplyTwo is {{ multiplyTwo }}</p>
    <button @click="treble">count x2</button>
</div>
</template>

<script lang="js">
import {
    reactive, // 响应式数据 reactive，将普通对象转换为proxy对象
    ref, //响应式系统 API,  接受一个参数值并返回一个响应式且可改变的 ref 对象。ref 对象拥有一个指向内部值的单一属性 .value。
    computed, //计算属性
    watch, //侦听器, 提供了一个更通用的方法，来响应数据的变化
    onMounted, //生命周期钩子
    readonly, //返回一个只读对象的代理，这个只读属性是「深入」的， 嵌套的属性都是只读
    watchEffect ////立即运行这个回调，自动跟踪依赖， 当依赖发生改变的时候，自动再次运行
} from 'vue'

export default {
    data() {
        return {
            // 
        }
    },
    setup() {
        // reactive state 响应式数据
        const count = ref(0)

        const original = reactive({
            count: 3
        })

        const copy = readonly(original)

        // computed state
        const plusOne = computed(() => count.value + 1)
        const multiplyTwo = computed(() => count.value * 2)

        // method
        const increment = () => {
            count.value++
        }
        const treble = () => {
            if (count.value > 0) {
                count.value *= 2
            }
        }

        // watch
        watch(() => count.value + 1, val => {
            console.log(`current count is ${val}`)
        })

        /**
         * 选项 flush:
         * sync  同步
         * pre    在更新（update）之前
         * post  在更新(update)之后， 这个是默认行为
         */
        watchEffect(() => {
            // 可以用在这里， 看来也是响应式的
            console.log('ractive:', copy.count)
        }, {
            flush: 'sync'
        })

        /**
         * watch 和 watchEffect 对比一下
            • 慢悠悠的执行副作用（惰性执行，默认在当前组件跟新后执行）
            • 指定了数据源， 指定数据源发生改变的时候才触发副作用回调函数执行
            • 可以获取当前值和上一个值
         */

        // mutating original will trigger watchers relying on the copy
        // original.count++

        // 改变这个 copy, 不会有用的， 且会告警
        copy.count++ // warning!

        // lifecycle
        onMounted(() => {
            console.log(`mounted`)
        })

        // expose bindings on render context
        return {
            count,
            plusOne, //加1
            increment,
            multiplyTwo, //乘2
            treble
        }
    }
}
</script>

<style lang="css">
.reactive-api {
    background-color: teal;
    color: bisque;
}

button {
    background-color: cadetblue;
    color: bisque;
    padding: 10px 20px;
    border-radius: 20px;
    font-size: 16px;
}
</style>
