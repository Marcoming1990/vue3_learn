<template>
  <h4>当前的x.y值是：{{x.y}}</h4>
  <button @click="x.y++">点我x+1</button>
  <hr>
  <h4>{{person}}</h4>
  <h2>姓名：{{name}}</h2>
  <h2>年龄：{{age}}</h2>
  <h2>薪资：{{job.j1.salary}}K</h2>
  <button @click="name+='~'">修改姓名</button>
  <button @click="age++">增长年龄</button>
  <button @click="job.j1.salary++">涨薪</button>
</template>

<script>
import { ref,reactive,toRefs,shallowReactive,shallowRef } from 'vue';
export default {
  name: 'Demo',

  setup() {
    // 数据
    // let person = shallowReactive({   // 浅层次的响应式，只处理第一层的，所以j1和salary都不响应
    let person = reactive({
      name:'张三',
      age:18,
      job:{
        j1:{
          salary:20
        }
      }
    })
    // let x = shallowRef(0)  // 0是基本对象，所以shallowRef跟ref没区别

    let x = shallowRef({ // 有对象数据，但不进行对象的响应式处理，后续不会修改该对象中的属性可以用这个，所以模板不能+1
      y:0
    })

    // 返回一个对象（常用）
    return {
      person,
      ...toRefs(person),
      x
    }
  },
};
</script>
