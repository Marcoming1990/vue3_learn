<template>
  <h4>当前求和为：{{sum}}</h4>
  <button @click="sum++">点我+1</button>
  <hr>
  <h2>姓名：{{name}}</h2>
  <h2>年龄：{{age}}</h2>
  <h2>薪资：{{job.j1.salary}}K</h2>
  <h3 v-show="person.car">座驾信息：{{person.car}}</h3>
  <button @click="name+='~'">修改姓名</button>
  <button @click="age++">增长年龄</button>
  <button @click="job.j1.salary++">涨薪</button>
  <hr>
  <button @click="showRawPerson">输出最原始的person</button>
  <h4>{{person}}</h4>
  <hr>
  <button @click="addCar">给人添加一台车</button>
  <button @click="person.car.name +='!'">换车名</button>
</template>

<script>
import { ref,reactive,toRefs,toRaw, markRaw } from 'vue';
export default {
  name: 'Demo',

  setup() {
    // 数据
    let sum = ref(0)
    let person = reactive({
      name:'张三',
      age:18,
      job:{
        j1:{
          salary:20
        }
      }
    })

    // 方法
    function showRawPerson(){
      const p = toRaw(person)  // 把响应式的对象改为原始对象(新)，只能处理reactive的对象
      p.age++
      console.log(p)
    }

    function addCar(){
      let car = {name:'奔驰',price:'40W'}
      // person.car = car  // 追加属性也是响应式的

      // 需求：car对象不需要修改（不要响应式）
      person.car = markRaw(car)  
    }

    // 返回一个对象（常用）
    return {
      sum,
      ...toRefs(person),  // 追加的car不会通过这个方式更新到页面，因为setup只会调用一次，这个也只会调用一次
      showRawPerson,
      person,
      addCar
    }
  },
};
</script>
