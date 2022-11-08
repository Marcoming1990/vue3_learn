<template>
  <h1>一个人的信息</h1>
  <h2>姓名：{{ person.name }}</h2>
  <h2>年龄：{{ person.age }}</h2>
  <button @click="test">测试触发Demo组件的hello事件</button>
</template>

<script>
import { reactive } from 'vue';
export default {
  name: 'Demo',
  props:['msg','school'], // 声明（接收）参数并proxy代理（响应式 数据劫持）
  emits:['hello'], // 声明（接收）绑定事件，不写控制台会警告

  setup(props,context) {
    // console.log('@props@',props);
    // console.log('@context@',context); 
    // console.log('@attrs@',context.attrs); // context.attrs 将没声明的参数捡漏放这里
    console.log('@slots@',context.slots); // context.slots 插槽

    // 数据
    let person = reactive({
      name: '张三',
      age: 18,
    });

    // 方法
    function test(){
        context.emit('hello',888) // context.emit 触发自定义事件
    }

    // 返回一个对象（常用）
    return {
      person,
      test,
    };
  },
};
</script>
