<template>
<div class="test">
    {{ msg }}
</div>
</template>

<script>
export default {
    name: 'TestAPI',
    props: {
        msg: String
    }
}
</script>

<style scoped>
.test {
    color: red;
}
</style>
