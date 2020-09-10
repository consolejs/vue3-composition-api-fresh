<template>
<div id="example-2">
    <!-- `greet` 是在下面定义的方法名 -->
    <button @click="greet">Greet</button>
    <button @click="say('hi', $event)">say hi</button>
</div>
</template>

<script>
import {
    defineComponent
} from "vue"

export default defineComponent({
    data() {
        return {
            name: 'Event'
        }
    },
    // 在 `methods` 对象中定义方法
    methods: {
        greet(event) {
            // `this` 在方法里指向当前 Vue 实例
            console.log('Hello ' + this.name + '!')
            // `event` 是原生 DOM 事件
            if (event) {
                console.log(event.target.tagName)
            }
        },
        say(msg, event) {
            // 现在我们可以访问原生事件对象
            if (event) {
                console.log(event.target.tagName)
            }
            alert(msg)
        }
    }
})
</script>
