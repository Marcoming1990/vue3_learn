<template>
  <div class="child">
    <h3>我是Child组件（子）</h3>
    <Son />
  </div>
</template>

<script>
    import Son from "./Son.vue";
    export default {
    name: "Child",
    components: { Son },
    // 这里也可以通过inject获取祖组件数据，只是一般父子传递用props
    };
</script>

<style>
    .child {
    background-color: skyblue;
    padding: 10px;
    }
</style>