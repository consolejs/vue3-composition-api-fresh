<template>
<div class="hooks-one">
    <h2>{{ msg }}</h2>
    <p>count is {{ count }}</p>
    <p>plusOne is {{ plusOne }}</p>
    <button @click="increment">count++</button>
</div>
</template>

<script lang="js">
import {
    value,
    computed,
    watch,
    onMounted
} from 'vue'

export default {
    data(){
        return{
            // 
        }
    },
    setup() {
        // reactive state
        const count = value(0)
        // computed state
        const plusOne = computed(() => count.value + 1)
        // method
        const increment = () => {
            count.value++
        }
        // watch
        watch(() => count.value * 2, val => {
            console.log(`count * 2 is ${val}`)
        })
        // lifecycle
        onMounted(() => {
            console.log(`mounted`)
        })
        // expose bindings on render context
        return {
            count,
            plusOne,
            increment
        }
    }
}
</script>
