<template>
<div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <ReactiveAPI msg="Reactive API!" />
    <Setup />
    <LifeCycle />
</div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import ReactiveAPI from "./components/ReactiveAPI.vue";
import Setup from "./components/Setup.vue";
import LifeCycle from "./components/LifeCycle.vue";

export default {
    name: "App",
    components: {
        HelloWorld,
        ReactiveAPI,
        Setup,
        LifeCycle
    },
};
</script>

<style>
#app {
    /* margin-top: 60px; */
    color: #2c3e50;
    text-align: center;
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}
</style>
