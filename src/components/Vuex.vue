<template>
<div class="vuex">Vuex</div>
</template>

<script>
import {
    // Vue,
    defineComponent,
    onMounted
} from 'vue'

// import Vuex from 'vuex'

// import 'es6-promise/auto'

// console.log(111, Vue)
// Vue.use(Vuex)

export default defineComponent({
    setup() {
        // const store = new Vuex.Store({
        //     state: {
        //         count: 0,
        //         info: {
        //             name: "iwen"
        //         }
        //     }
        // })

        onMounted(() => {
            // console.log(this.store);
        });

        return {
            // store
        };
    }

})
</script>

<style scoped>
.vuex {
    padding: 20px 0;
    color: darkcyan;
    font-weight: 600;
}
</style>
