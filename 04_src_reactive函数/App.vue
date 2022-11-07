<template>
  <h1>一个人的信息</h1>
  <!-- 发现name是RefImpl实例对象，Vue3会自动解析 -->
  <h2>姓名：{{name}}</h2>
  <h2>年龄：{{age}}</h2>
  <h3>工作种类：{{job.type}}</h3>
  <h3>工作薪水：{{job.salary}}</h3>
  <h3>爱好：{{hobby}}</h3>
  <button @click="changeInfo">修改人的信息</button>
</template>

<script>
import {ref,reactive} from 'vue' // 改了这里
export default {
  name: 'App',
  setup(){
    // 数据（可以将下面属性放到一个person对象里面，只用reactive，这里代码我没敲）
    let name = ref('张三')  
    let age = ref(18)
    let job = reactive({   // 改了这里
      type:'前端工程师',
      salary:'30K'
    })
    let hobby = ['抽烟','喝酒','烫头']

    // 方法
    function changeInfo(){
      name.value = '李四'
      age.value = 48
      job.type = '后端工程师'  // 改了这里
      job.salary = '40K'  // 改了这里
      hobby[0] = '学习'
    }

    // 返回一个对象（常用）
    return {
      name,
      age, 
      job,
      hobby,
      changeInfo
    }
  }
}
</script>
