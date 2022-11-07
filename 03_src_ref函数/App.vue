<template>
  <h1>一个人的信息</h1>
  <!-- 发现name是RefImpl实例对象，Vue3会自动解析 -->
  <h2>姓名：{{name}}</h2>
  <h2>年龄：{{age}}</h2>
  <h3>工作种类：{{job.type}}</h3>
  <h3>工作薪水：{{job.salary}}</h3>
  <button @click="changeInfo">修改人的信息</button>
</template>

<script>
import {ref} from 'vue'
export default {
  name: 'App',
  setup(){
    // 数据
    let name = ref('张三')  // 包装成一个RefImpl实例对象
    let age = ref(18)
    let job = ref({   // 包装成一个Proxy实例对象
      type:'前端工程师',
      salary:'30K'
    })

    // 方法
    function changeInfo(){
      name.value = '李四'
      age.value = 48
      job.value.type = '后端工程师'  // 先value再属性
      job.value.salary = '40K'
    }

    // 返回一个对象（常用）
    return {
      name,
      age, 
      job,
      changeInfo
    }
  }
}
</script>
