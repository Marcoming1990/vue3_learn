<template>
  <div class="son">
    <h3>我是Son组件（孙），{{car.name}}-{{car.price}}</h3>
  </div>
</template>

<script>
  import {inject} from 'vue'
  export default {
    name:'Son',
    setup(){
        let car = inject('car') // 获取祖提供的数据，且是响应式的
        return {car}
    }
  }
</script>

<style>
  .son{
    background-color: orange;
    padding: 10px;
  }
</style>