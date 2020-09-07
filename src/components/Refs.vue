<template>
<div ref="root">Refs</div>
</template>

<script>
import {
    ref,
    onMounted,
    defineComponent
} from 'vue'
export default defineComponent({
    setup() {
        const root = ref(null)
        onMounted(() => {
            // 在渲染完成后, 这个 div DOM 会被赋值给 root ref 对象
            console.log(root.value) // <div/>
        })
        return {
            root
        }
    }
})
</script>
