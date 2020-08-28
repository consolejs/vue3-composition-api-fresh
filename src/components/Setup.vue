<template>
<div>{{ count }} : {{ objectRea.foo }}</div>
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
            count: 0
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