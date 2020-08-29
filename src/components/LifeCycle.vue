<template>
  <div class="module lifecycle">
    <h2 class>LifeCycle</h2>
    <p>Look Console!</p>
  </div>
</template>

<script>
import { defineComponent, onMounted, onUpdated, onUnmounted } from "vue";
export default defineComponent({
  setup() {
    onMounted(() => {
      console.log("lifecycle: 0, onMounted");
    });
    onUpdated(() => {
      console.log("lifecycle 1, onMounted");
    });
    onUnmounted(() => {
      console.log("lifecycle 2, onMounted");
    });
  },
});
</script>

<style lang="css" scoped>
.lifecycle {
  background-color: #8c47bf;
  color: #fff;
}
</style>