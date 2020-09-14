<template>
<div id="event">
    <!-- `greet` 是在下面定义的方法名 -->
    <button @click="greet">Greet</button>
    <button @click="say('hi', $event)">say hi</button>
    <!--
        使用修饰符时，顺序很重要；
        相应的代码会以同样的顺序产生。
        因此，用 v-on:click.prevent.self 会阻止所有的点击，
        而 v-on:click.self.prevent 只会阻止对元素自身的点击
    -->
    <button @click.stop="doThis">Some</button>
    <!-- 点击事件将只会触发一次 -->
    <button v-on:click.once="doThis">One click</button>
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
        },
        doThis() {
         
            console.log('Do this!')
        }
    }
})
</script>

<style>
#event {
    padding: 20px 0;
    background-color: chocolate
}

button {
    background-color: #6d7979;
}
</style>
