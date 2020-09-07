<template>
<div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <ReactiveAPI msg="Reactive API!" />
    <Setup name="seeeetup!" foo="我是从父组件来的!" />
    <LifeCycle />
    <Injection />
    <TemplateRefs />
    <Refs />
</div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import ReactiveAPI from "./components/ReactiveAPI.vue";
import Setup from "./components/Setup.vue";
import LifeCycle from "./components/LifeCycle.vue";
import Injection from "./components/Injection.vue";
import TemplateRefs from "./components/TemplateRefs.vue";
import Refs from "./components/Refs.vue";

export default {
    name: "App",
    components: {
        HelloWorld,
        ReactiveAPI,
        Setup,
        LifeCycle,
        Injection,
        TemplateRefs,
        Refs
    },
};
</script>

<style>
*{
    margin: 0;
    padding: 0;
}
#app {
    /* margin-top: 60px; */
    color: #2c3e50;
    text-align: center;
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}
#app .module{
    padding: 20px 0;
}
</style>
