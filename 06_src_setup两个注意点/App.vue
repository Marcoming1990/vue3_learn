<template>
  <Demo @hello="showHelloMsg" msg="你好啊" school="清华小学">
    <template v-slot:qwe>
      <span>我是Span1</span>  
    </template>
    <template v-slot:asd>
      <span>我是Span2</span>  
    </template>
  </Demo>
</template>

<script>
import Demo from './components/Demo' 
export default {
  name: 'App',
  components:{Demo},
  setup(){
    function showHelloMsg(value){
      alert(`你好啊，你触发了hello事件，我收到参数是：${value}！`)
    }

    return {
      showHelloMsg
    }
  }
}
</script>
