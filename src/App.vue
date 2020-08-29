<template>
<div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <TestAPI msg="Test!" />
    <Setup />
</div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import TestAPI from "./components/TestAPI.vue";
import Setup from "./components/Setup.vue";

export default {
    name: "App",
    components: {
        HelloWorld,
        TestAPI,
        Setup,
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
