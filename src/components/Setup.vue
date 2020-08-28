<template>
<div>{{ count }} {{ object.foo }}</div>
</template>

<script>
    import {
        ref,
        reactive,
        defineComponent

    } from 'vue'

    export default defineComponent({
        data() {
            return {
                count: 1
            }
        },
        setup() {
            const countRef = ref(0)
            const objectRea = reactive({
                foo: 'bar'
            })

            // return 的属性会暴露给模板，模板中可以直接使用,这里没有 return 的， 无法在模板中使用
            return {
                countRef,
                objectRea
            }
        }
    })
</script>

<!--
<template>
    <div class="hooks-one">
        <h2>{{ msg }}</h2>
        <p>count is {{ count }}</p>
        <p>plusOne is {{ plusOne }}</p>
        <button @click="increment">count++</button>
    </div>
</template>

<script lang='js'>

import { value, computed, watch, onMounted } from '@vue/runtime-core'

export default {
   setup() {
    // reactive state
    const count = value(0)
    // computed state
    const plusOne = computed(() => count.value + 1)
    // method
    const increment = () => { count.value++ }
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
-->
