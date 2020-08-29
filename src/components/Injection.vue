<template>
  <div class="module injection" :style="boxSyle">Injection! {{count}}</div>
</template>

<script lang="js">
import {
    defineComponent,
    ref
} from "vue"

import getRandomColor from "../libs/getRandomColor";

//随机颜色值 16hex
const colorValue = getRandomColor();

export default defineComponent({
    data(){
        return{
            boxSyle: {
                "background-color": colorValue
            }
        }
    },
    setup() {
        
        const count = ref(0);
        return {
            count
        }
    }
})
</script>

<style lang="css" scoped>
.injection {
  color: cornsilk;
}
</style>