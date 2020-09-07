<template>
<div ref="root" class="refs">Refs</div>
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

<style scoped> 
    .refs{
        padding: 20px 0;
        color: darkcyan;
        font-weight: 600;
    }
</style>