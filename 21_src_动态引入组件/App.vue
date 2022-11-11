<template>
  <div class="app">
    <h3>我是App组件</h3>
    <Suspense>
      <template v-slot:default>
        <Child/>
      </template>
      <!-- 等待加载时显示 -->
      <template v-slot:fallback>
        <h3>稍等，加载中...</h3>
      </template>
    </Suspense>
  </div>
</template>

<script>
  // 静态引入
  // import Child from './components/Child.vue' 

  // 动态（异步）引入
  import {defineAsyncComponent} from 'vue'
  const Child = defineAsyncComponent(()=>import('./components/Child.vue'))


  export default {
    name:'App',
    components:{Child},
  }
</script>

<style>
  .app{
    background-color: gray;
    padding: 10px;
  }
</style>