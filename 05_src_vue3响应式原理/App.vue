<template>
  <h1>一个人的信息</h1>
  <!-- 发现name是RefImpl实例对象，Vue3会自动解析 -->
  <h2>姓名：{{name}}</h2>
  <h2>年龄：{{age}}</h2>
  <h3 v-show="job.type">工作种类：{{job.type}}</h3>
  <h3>工作薪水：{{job.salary}}</h3>
  <h3 v-show="job.address">工作地点：{{job.address}}</h3>
  <h3>爱好：{{hobby}}</h3>
  <button @click="changeInfo">修改人的信息</button>
  <button @click="addJobAddress">添加工作地址</button>
  <button @click="deleteJboType">删除工作类型</button>
</template>

<script>
import {ref,reactive} from 'vue' 
export default {
  name: 'App',
  setup(){
    // 数据
    let name = ref('张三')  
    let age = ref(18)
    let job = reactive({   
      type:'前端工程师',
      salary:'30K'
    })
    let hobby = ['抽烟','喝酒','烫头']

    // 方法
    function changeInfo(){
      name.value = '李四'
      age.value = 48
      job.type = '后端工程师'  
      job.salary = '40K'  
      hobby[0] = '学习'  // 因为job是reactive才可以下标修改
    }

    function addJobAddress(){  // 因为job是reactive才可以这样添加
      job.address = '广州'
    }

    function deleteJboType(){ // 因为job是reactive才可以这样删除
      delete job.type
    }

    // 返回一个对象（常用）
    return {
      name,
      age, 
      job,
      hobby,
      changeInfo,
      addJobAddress,
      deleteJboType
    }
  }
}
</script>
