<template>
  <div>
    <hr>
    <h2>{{msg}}</h2>
    <hr>
    <p v-on:click="click"> javascript 点击更改信息</p>
    <hr>
    <span v-html="rich"></span>
  </div>
</template>

<script>
  import axios from 'axios'
  import Mock from 'mockjs'
  const data = Mock.mock({
    // 属性 list 的值是一个数组，其中含有 1 到 10 个元素
    'foods|10-30': [{
      'name': '@ctitle(2,10)',
      'img': '@image("600x600",#b7ef7c)',
      'brief': '@csentence(1,50)',
      'price|0-20.0-2': 1,
      'num': 0,
      'minusFlag': true,
      'time': '@time',
      'peisongfei|0-100.0-2': 1,
      'limit|0-50': 1
    }]
  })
  export default {
    name: 'Home',
    data () {
      return {
        msg: 'hello vue',
        rich: '<p>一个p标签</p><span>一个span标签</span>'
      }
    },
    beforeCreate: function () {
      console.log('组件创建前状态---')
    },
    created: function () {
      console.log('组件创建后的状态---')
      console.log('mock--data', data)
      axios.get('/api/testApi').then(
        (response) => {
          console.log('response---', response)
        }
      )
    },
    beforeMount: function () {
      console.log('组件挂载前的状态---')
    },
    mounted: function () {
      console.log('组件挂载之后的状态---')
    },
    beforeUpdate: function () {
      console.log('组件更新前状态---')
    },
    updated: function () {
      console.log('组件更新完成的状态---')
    },
    beforeDestroy: function () {
      console.log('组件销毁前的状态----')
    },
    destroyed: function () {
      console.log('组件销毁后的状态')
    },
    methods: {
      click: function () {
        this.msg = 'my first vue project'
      }
    }
  }
</script>

<style scoped>

</style>
