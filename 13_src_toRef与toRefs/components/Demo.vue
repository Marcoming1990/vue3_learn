<template>
  <h4>{{person}}</h4>
  <h2>姓名：{{name}}</h2>
  <h2>年龄：{{age}}</h2>
  <h2>薪资：{{salary}}K</h2>
  <button @click="name+='~'">修改姓名</button>
  <button @click="age++">增长年龄</button>
  <button @click="salary++">涨薪</button>
</template>

<script>
import { reactive,toRef,toRefs } from 'vue';
export default {
  name: 'Demo',

  setup() {
    // 数据
    let person = reactive({   
      name:'张三',
      age:18,
      job:{
        j1:{
          salary:20
        }
      }
    })

    // 返回一个对象（常用）
    return {
      person,
      // toRef 单个属性
      name:toRef(person,'name'),
      age:toRef(person,'age'),
      salary:toRef(person.job.j1,'salary')

      // toRefs 多个属性
      // ...toRefs(person)  // 只会把第一层的全拆出来做成对象。例如job，模板要使用job.j1.salary
    };
  },
};
</script>
